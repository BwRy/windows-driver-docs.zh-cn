---
title: 驱动程序对象中的驱动程序入口点
description: 驱动程序对象中的驱动程序入口点
ms.assetid: f004c2b3-8435-4c25-82e9-aff3911dc316
keywords:
- 驱动对象 WDK 内核
- 标准驱动程序例程 WDK 内核，驱动程序对象
- 驱动程序例程 WDK 内核，驱动程序对象
- 例程的 WDK 内核，驱动程序对象
- 对象 WDK 驱动程序对象
- 入口点 WDK 内核
- 驱动程序入口点 WDK 内核
ms.date: 06/16/2017
ms.localizationpriority: medium
ms.openlocfilehash: 67b5f2f3ebc0f5a8ee9deaff9056f320b1ad4525
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72836810"
---
# <a name="driver-entry-points-in-driver-objects"></a>驱动程序对象中的驱动程序入口点





内核模式驱动程序必须在其驱动程序对象中指定以下入口点：

-   至少一个调度例程的入口点，以便获取 Irp 请求 PnP、电源和 i/o 操作。

-   [*AddDevice*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nc-wdm-driver_add_device)例程的入口点， **DriverObject-&gt; DriverExtension-&gt; AddDevice**。

-   其[*StartIo*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nc-wdm-driver_startio)例程的入口点（如果它管理自己的 irp 队列）。

-   如果可以动态加载和/或动态替换驱动程序，则[*卸载*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nc-wdm-driver_unload)入口点以释放驱动程序已分配的任何系统资源，如系统对象或内存。 （当系统正在运行时无法替换的驱动程序，如键盘驱动程序，不需要提供*卸载*例程。）

这些要求不适用于某些微型端口驱动程序，其中对应的类或端口驱动程序定义驱动程序对象中的入口点。 有关详细信息，请参阅特定于设备类型的文档。

I/o 管理器在相应的驱动程序对象中维护有关驱动程序创建的设备对象的信息。

加载驱动程序时，将使用指向驱动程序对象的指针调用其[**DriverEntry**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/nc-wdm-driver_initialize)例程。 当调用驱动程序的**DriverEntry**例程时，它将设置*调度*、 *StartIo* （如果有），并在驱动程序对象中直接*卸载*（如果有）入口点，如下所示：

```cpp
DriverObject->MajorFunction[IRP_MJ_xxx] = DDDispatchXxx; 
              :    : 
DriverObject->MajorFunction[IRP_MJ_yyy] = DDDispatchYyy; 
              :    : 
DriverObject->DriverStartIo = DDStartIo; 
DriverObject->DriverUnload = DDUnload; 
              :    : 
```

**DriverEntry**例程还在其 driver 对象的**DriverExtension**中设置其*AddDevice*例程的入口点，如下所示：

```cpp
DriverObject->DriverExtension->AddDevice = DDAddDevice; 
```

**DriverEntry**或可选的重新[*初始化*](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddk/nc-ntddk-driver_reinitialize)例程还可以使用 driver 对象中的字段（不显示在[驱动程序对象图](introduction-to-driver-objects.md#driver-object-illustration)中）来从和/或设置 configuration manager 的注册表数据库中的信息。 有关详细信息，请参阅[驱动程序的注册表项](https://docs.microsoft.com/windows-hardware/drivers/install/overview-of-registry-trees-and-keys)。

I/o 管理器不会导出支持例程来操作驱动程序对象，驱动程序对象是[**驱动程序\_对象**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/ns-wdm-_driver_object)结构。 I/o 管理器使用驱动程序对象跟踪当前加载的驱动程序。 驱动程序对象的某些成员仅由 i/o 管理器使用。 其他成员也由驱动程序编写器使用;例如，您必须知道某些成员名称，才能定义*AddDevice*、*调度*、 *StartIo*和*卸载*入口点。 您既不应尝试使用**驱动程序\_对象**结构中未记录的成员，也不应对本文档中命名的任何驱动程序对象成员的位置做出假设。 否则，不能将驱动程序从一个 Windows 平台移植到另一个平台。

 

 




