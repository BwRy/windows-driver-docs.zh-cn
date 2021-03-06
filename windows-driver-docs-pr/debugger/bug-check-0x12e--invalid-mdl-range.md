---
title: Bug 检查 0x12E INVALID_MDL_RANGE
description: INVALID_MDL_RANGE bug 检查具有 0x0000012E 值。
ms.assetid: 911192DC-17B8-4D75-A96E-2E310B30348F
keywords:
- Bug 检查 0x12E INVALID_MDL_RANGE
- INVALID_MDL_RANGE
ms.date: 05/23/2017
topic_type:
- apiref
api_name:
- INVALID_MDL_RANGE
api_type:
- NA
ms.localizationpriority: medium
ms.openlocfilehash: 72626bade771f97fb3112aca5aa79648beff5aac
ms.sourcegitcommit: d03b44343cd32b3653d0471afcdd3d35cb800c0d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2019
ms.locfileid: "67520506"
---
# <a name="bug-check-0x12e-invalidmdlrange"></a>Bug 检查 0x12E：无效\_MDL\_范围


无效\_MDL\_范围错误检查的值为 0x0000012E。 这表示一个驱动程序具有名为 IoBuildPartialMdl() 函数并将其传递 MDL 映射属于源 MDL，但指定的虚拟地址范围不在源 MDL 的范围。 这通常是驱动程序 bug。

源和目标 MDLs 中，使用以及在要映射的地址范围长度的参数是 IoBuildPartialMdl() 函数，即;）。

```cpp
IoBuildPartialMdl(
        IN PMDL SourceMdl,
        IN OUT PMDL TargetMdl,
        IN PVOID VirtualAddress,
        IN ULONG Length
```

> [!IMPORTANT]
> 本主题面向程序员。 如果你已使用计算机时收到一个蓝色的屏幕，错误代码的客户，请参阅[疑难解答蓝屏错误](https://www.windows.com/stopcode)。


## <a name="invalidmdlrange-parameters"></a>无效\_MDL\_范围参数


| 参数 | 描述    |
|-----------|----------------|
| 1         | SourceMdl      |
| 2         | TargetMdl      |
| 3         | VirtualAddress |
| 4         | 长度         |

 

 

 




