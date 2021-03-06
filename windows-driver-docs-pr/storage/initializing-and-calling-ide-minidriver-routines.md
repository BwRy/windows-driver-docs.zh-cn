---
title: 初始化和调用 IDE 微型驱动程序例程
description: 初始化和调用 IDE 微型驱动程序例程
ms.assetid: ae7b19a9-0a2e-4231-b008-879b7f6c8566
keywords:
- IDE 控制器微型驱动程序 WDK 存储，初始化
- 存储 IDE 控制器微型驱动程序 WDK，初始化
- IDE 控制器微型驱动程序 WDK 存储，调用
- 存储 IDE 控制器微型驱动程序 WDK，调用
- 初始化 IDE 控制器微型驱动程序
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: b689bbd9666ffcbf5f0c6fb6a9deb352cda8044b
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72845377"
---
# <a name="initializing-and-calling-ide-minidriver-routines"></a>初始化和调用 IDE 微型驱动程序例程


## <span id="ddk_initializing_and_calling_ide_minidriver_routines_kr"></span><span id="DDK_INITIALIZING_AND_CALLING_IDE_MINIDRIVER_ROUTINES_KR"></span>


所有 IDE 控制器微型驱动程序必须提供一系列实现硬件特定功能的标准例程。 下图说明了 IDE 控制器微型驱动程序如何使其例程可用于控制器驱动程序。 请注意，尽管在概念上不同于 IDE 控制器驱动程序（如下图中所示）的 PciIdeX 库包含在控制器驱动程序的可执行文件*PciIdeX*中。 当微型驱动程序调用 PciIdeX 库例程时，实际上是在控制器驱动程序内调用例程。

![微型驱动程序例程初始化的程序流](images/idecallbacks.png)

1.  PnP 管理器加载 IDE 控制器驱动程序-微型驱动程序，然后调用其[**DriverEntry**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nc-wdm-driver_initialize)例程，并向其传递指向控制器驱动程序的驱动程序对象的指针。

2.  微型驱动程序的**DriverEntry**调用[**PciIdeXInitialize**](https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff563788(v=vs.85))库例程，并向其传递一个指向微型驱动程序的**GetControllerProperties**例程的指针。

3.  **PciIdeXInitialize**将指向**GetControllerProperties**的指针存储在驱动程序对象中。

4.  PnP 管理器调度 IRP\_MN\_开始向 IDE 控制器驱动程序\_设备请求，以启动控制器。 IDE 控制器驱动程序在其[**DispatchPnP**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nc-wdm-driver_dispatch)例程中接收请求，并调用用于启动设备的内部例程。

5.  控制器驱动程序检索指向存储在驱动程序对象中的**GetControllerProperties**的指针。

6.  控制器驱动程序调用**GetControllerProperties**，并向其传递指向[**IDE\_控制器\_PROPERTIES**](https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff559076(v=vs.85))结构的指针。

7.  **GetControllerProperties**将标准微型驱动程序例程集的指针加载到 IDE\_控制器\_属性中。

微型驱动程序填充 IDE 后\_控制器\_PROPERTIES 结构，其中包含指向微型驱动程序例程的函数指针，控制器驱动程序可以调用它们。

对于控制器调用的每个微型驱动程序必须提供的例程如下：

此例程确定所指示的通道是否已启用。

此例程报告 IDE 控制器硬件的属性。

此例程指示是否可以同时访问其控制器的两个通道。

此例程为*XferMode*中指示的每个设备返回最佳 PIO 模式和最佳 DMA 模式。

此例程指示哪个 hyper-v 内存访问（UDMA）传输模式为最新，哪种模式最适合于设备。

此例程确定是否可以通过 DMA 来完成 i/o。

[**HwIdeXChannelEnabled**](https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff557252(v=vs.85))

[**HwIdeXGetControllerProperties**](https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff557254(v=vs.85))

[**HwIdeXSyncAccessRequired**](https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff557256(v=vs.85))

[**HwIdeXTransferModeSelect**](https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff557260(v=vs.85))

[**HwIdeXUdmaModesSupported**](https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff557264(v=vs.85))

[**HwIdeXUseDma**](https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff557266(v=vs.85))

 

 




