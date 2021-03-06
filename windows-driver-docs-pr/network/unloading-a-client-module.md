---
title: 卸载客户端模块
description: 卸载客户端模块
ms.assetid: 2cca2918-ce0b-4016-b3f2-fbbc06c0b7f7
keywords:
- 客户端模块 WDK 网络模块注册器，卸载
- 卸载网络模块
- NmrDeregisterClient
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 9f4a80c287c32438b640b83e726e589b3093bfdf
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72843014"
---
# <a name="unloading-a-client-module"></a>卸载客户端模块


若要卸载客户端模块，操作系统将调用客户端模块的[**unload**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nc-wdm-driver_unload)函数。 有关如何在初始化过程中指定客户端模块的**Unload**函数的详细信息，请参阅[初始化和注册客户端模块](initializing-and-registering-a-client-module.md)。

在从系统内存中卸载客户端模块之前，客户端模块的[**Unload**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nc-wdm-driver_unload)函数可确保从网络模块注册器（NMR）取消对客户端模块的注册。 客户端模块通过调用[**NmrDeregisterClient**](https://docs.microsoft.com/windows-hardware/drivers/ddi/netioddk/nf-netioddk-nmrderegisterclient)函数开始从 NMR 注销，该函数通常从其**Unload**函数调用它。 在从 NMR 完全取消注册后，客户端模块不能从其**Unload**函数返回。 如果对**NmrDeregisterClient**的调用返回状态\_"挂起"，则客户端模块必须调用[**NmrWaitForClientDeregisterComplete**](https://docs.microsoft.com/windows-hardware/drivers/ddi/netioddk/nf-netioddk-nmrwaitforclientderegistercomplete)函数以等待注销完成，然后从其**卸载**返回才能.

例如：

```C++
// Variable containing the handle for the registration
HANDLE ClientHandle;

// Unload function
VOID
  Unload(
    IN PDRIVER_OBJECT DriverObject
    )
{
  NTSTATUS Status;

  // Deregister the client module from the NMR
  Status =
    NmrDeregisterClient(
      ClientHandle
      );

  // Check if pending
  if (Status == STATUS_PENDING)
  {
    // Wait for the deregistration to be completed
    NmrWaitForClientDeregisterComplete(
      ClientHandle
      );
  }

  // An error occurred
  else
  {
    // Handle error
    ...
  }
}
```

如果客户端模块注册为多个[网络编程接口（NPIs）](network-programming-interface.md)的客户端，则它必须为其支持的每个 NPI 调用[**NmrDeregisterClient**](https://docs.microsoft.com/windows-hardware/drivers/ddi/netioddk/nf-netioddk-nmrderegisterclient) 。 如果将网络模块注册为客户端模块和提供程序模块（即，它是一个 NPI 的客户端和另一个 NPI 的提供程序），则它必须同时调用**NmrDeregisterClient**和[**NmrDeregisterProvider**](https://docs.microsoft.com/windows-hardware/drivers/ddi/netioddk/nf-netioddk-nmrderegisterprovider)。

在从其[**Unload**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nc-wdm-driver_unload)函数返回之前，网络模块必须一直等待，直到所有注销都完成。

不需要客户端模块从其[**Unload**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nc-wdm-driver_unload)函数中调用[**NmrDeregisterClient**](https://docs.microsoft.com/windows-hardware/drivers/ddi/netioddk/nf-netioddk-nmrderegisterclient) 。 例如，在客户端模块是复杂驱动程序的子组件的情况下，当停用客户端模块子组件时，可能会取消注册客户端模块。 但是，在这种情况下，驱动程序必须确保在从 NMR 的**Unload**函数返回之前已完全从取消对该客户端模块的注册。

 

 





