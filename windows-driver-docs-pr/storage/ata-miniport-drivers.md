---
title: ATA 微型端口驱动程序
description: ATA 微型端口驱动程序
ms.assetid: 4e5cf0e3-72c5-43df-b61e-0039c3666de4
keywords:
- ATA 微型端口驱动程序 WDK
- 存储 ATA 微型端口驱动程序 WDK
- 存储微型端口驱动程序 WDK，ATA 微型端口驱动程序
- 微型端口驱动程序 WDK 存储，ATA 微型端口驱动程序
ms.date: 10/08/2019
ms.localizationpriority: medium
ms.openlocfilehash: e63b7ccae30dca03ac5c6a157eccb9d0adedb9a7
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72845102"
---
# <a name="ata-miniport-drivers"></a>ATA 微型端口驱动程序

> [!NOTE]
> ATA 端口驱动程序和 ATA 微型端口驱动程序模型可能会在将来更改或不可用。 相反，我们建议使用[storport 驱动](https://docs.microsoft.com/windows-hardware/drivers/storage/storport-driver)程序和[storport 微型端口](https://docs.microsoft.com/windows-hardware/drivers/storage/storport-miniport-drivers)驱动程序模型。

ATA 微型端口驱动程序适用于 ATA 端口驱动程序。 此页列出 ATA 端口驱动程序调用的 ATA 微型端口驱动程序中实现的例程。 有关 ATA 微型端口驱动程序可调用的系统提供的 ATA 端口驱动程序例程的列表，请参阅[Ata 端口驱动程序支持例程](ata-port-driver-support-routines.md)。

## <a name="ata-controller-interface-routines"></a>ATA 控制器接口例程

需要每个供应商提供的微型端口驱动程序才能实现一组定义控制器接口的例程。 通过使用这些例程，微型端口驱动程序与系统提供的控制器驱动程序*pciidex*通信。

供应商提供的微型端口驱动程序与控制器驱动程序通信，以便初始化端口和微型端口驱动程序以及配置主机总线适配器（HBA）所需的交换参数。 如果未在此节中将例程显式标识为可选，则它是必需的。 如果选择不实现可选例程，则必须确保微型端口驱动程序将[IDE_CONTROLLER_INTERFACE](https://docs.microsoft.com/windows-hardware/drivers/ddi/irb/ns-irb-_ide_controller_interface)结构中的相应函数指针设置为 NULL。

- DriverEntry
- AtaAdapterControl
- AtaControllerChannelEnabled
- AtaControllerTransferModeSelect

## <a name="ata-channel-interface-routines"></a>ATA 通道接口例程

供应商提供的微型端口驱动程序可以选择实现一组定义通道接口的例程。 通过使用这些例程，微型端口驱动程序可以处理发送到硬件的每个请求。 微型端口驱动程序不得部分实现通道接口。 如果微型端口驱动程序支持[**AtaChannelInitRoutine**](https://docs.microsoft.com/windows-hardware/drivers/ddi/irb/nf-irb-ataportinitializeex)例程，还应实现以下例程：

- AtaChannelInitRoutine
- IdeHwInitialize
- IdeHwBuildIo
- IdeHwStartIo
- IdeHwInterrupt
- IdeHwReset
- IdeHwControl
