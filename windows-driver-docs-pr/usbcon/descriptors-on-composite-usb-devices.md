---
Description: USB 复合设备上的描述符
title: USB 复合设备上的描述符
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: c29ff848daba9517d440293164c67a92a9ef0c85
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72842396"
---
# <a name="descriptors-on-usb-composite-devices"></a>USB 复合设备上的描述符


如 USB 规范所述，每个 USB 设备都提供一组定义其功能的分层描述符。 在顶级，每个设备都有一个或多个 USB 配置描述符，其中每个都有一个或多个接口描述符。 有关 USB 配置描述符的详细信息，请参阅[Usb 配置描述符](usb-configuration-descriptors.md)。 配置是互相排斥的，因此，一次只能选择一个配置来操作。

在 Windows Vista 之前，Microsoft 提供的驱动程序只选择 "配置 1"。 在 Windows Vista 和更高版本的 Windows 中，你可以设置注册表值以指定[USB 通用父驱动程序（Usbccgp）](usb-common-class-generic-parent-driver.md)将使用的配置。 有关在复合设备上选择设备配置的详细信息，请参阅[如何为 USB 设备选择配置](how-to-select-a-configuration-for-a-usb-device.md)。

在配置中，接口和接口集合是独立管理的。 每个接口都通过其[**USB\_接口**](https://docs.microsoft.com/windows-hardware/drivers/ddi/usbspec/ns-usbspec-_usb_interface_descriptor)的**bInterfaceNumber**成员中的唯一值来表示（在描述符级别）\_描述符结构。

接口的功能由相同结构的**bInterfaceClass**、 **bInterfaceSubClass**和**bInterfaceProtocol**成员以及可能跟随它的类特定说明符指示。

有关描述符的详细信息，请参阅[USB 描述符](usb-descriptors.md)。

## <a name="related-topics"></a>相关主题
[USB 通用父驱动程序（Usbccgp）](usb-common-class-generic-parent-driver.md)  
[Microsoft 提供的 USB 驱动程序](system-supplied-usb-drivers.md)  



