---
title: Bug 检查 0x1A6 BLUETOOTH_ERROR_RECOVERY_LIVEDUMP
description: BLUETOOTH_ERROR_RECOVERY_LIVEDUMP bug 检查具有 0x000001A6 值。 它指示 Bluetooth 无线电驱动程序已启动错误恢复以尝试重置与无法挽回条件单选。
keywords:
- Bug 检查 0x1A6 BLUETOOTH_ERROR_RECOVERY_LIVEDUMP
- BLUETOOTH_ERROR_RECOVERY_LIVEDUMP
ms.date: 01/28/2019
topic_type:
- apiref
api_name:
- BLUETOOTH_ERROR_RECOVERY_LIVEDUMP
api_type:
- NA
ms.localizationpriority: medium
ms.openlocfilehash: e5546d2377f074d94e260f66d9c73715ac5709b4
ms.sourcegitcommit: d03b44343cd32b3653d0471afcdd3d35cb800c0d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2019
ms.locfileid: "67519749"
---
# <a name="bug-check-0x1a6-bluetootherrorrecoverylivedump"></a>Bug 检查 0x1A6：蓝牙\_错误\_恢复\_LIVEDUMP

蓝牙\_错误\_恢复\_LIVEDUMP bug 检查的值为 0x000001A6。 它指示 Bluetooth 无线电驱动程序 (bthport.sys) 已启动错误恢复以尝试恢复和重置无法挽回的内部情况从单选。

> [!IMPORTANT]
> 本主题面向程序员。 如果你已使用计算机时收到一个蓝色的屏幕，错误代码的客户，请参阅[疑难解答蓝屏错误](https://www.windows.com/stopcode)。

 

## <a name="bluetootherrorrecoverylivedump-parameters"></a>蓝牙\_错误\_恢复\_LIVEDUMP 参数

|参数|描述|
|--- |--- |
|1| PDO 的蓝牙无线 （设备）。|
|2| 保留。|
|3| 保留。|
|4| 保留。|

## <a name="cause"></a>原因
-----

Bluetooth 无线电驱动程序 (bthport.sys) 已启动错误恢复以尝试恢复和重置无法挽回的内部情况从单选。

（此代码可以永远不会用于实际的执行错误检查; 它用于标识实时转储）。


## <a name="see-also"></a>请参阅
----------

[Bug 检查代码参考](bug-check-code-reference2.md)

