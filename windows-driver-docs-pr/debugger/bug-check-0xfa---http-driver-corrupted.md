---
title: Bug 检查 0xFA HTTP_DRIVER_CORRUPTED
description: HTTP_DRIVER_CORRUPTED bug 检查具有 0x000000FA 值。 这表示 HTTP 内核驱动程序 (Http.sys) 已达到损坏的状态且无法恢复。
ms.assetid: f7e3c1bf-2259-4aa6-af19-267b537dedfe
keywords:
- Bug 检查 0xFA HTTP_DRIVER_CORRUPTED
- HTTP_DRIVER_CORRUPTED
ms.date: 05/23/2017
topic_type:
- apiref
api_name:
- HTTP_DRIVER_CORRUPTED
api_type:
- NA
ms.localizationpriority: medium
ms.openlocfilehash: 2afaeb93f2fdb7ec9b83cd3c4a763743ab0a0e64
ms.sourcegitcommit: 0cc5051945559a242d941a6f2799d161d8eba2a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63340614"
---
# <a name="bug-check-0xfa-httpdrivercorrupted"></a>Bug 检查 0xFA：HTTP\_驱动程序\_已损坏


HTTP\_驱动程序\_损坏错误检查的值为 0x000000FA。 这表示 HTTP 内核驱动程序 (Http.sys) 已达到损坏的状态且无法恢复。

> [!IMPORTANT]
> 本主题面向程序员。 如果你已使用计算机时收到一个蓝色的屏幕，错误代码的客户，请参阅[疑难解答蓝屏错误](https://windows.microsoft.com/windows-10/troubleshoot-blue-screen-errors)。


## <a name="httpdrivercorrupted-parameters"></a>HTTP\_驱动程序\_损坏参数


参数 1 标识 HTTP 内核驱动程序的确切状态。

<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">参数 1</th>
<th align="left">参数 2</th>
<th align="left">参数 3</th>
<th align="left">参数 4</th>
<th align="left">错误的原因</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>0x1</p></td>
<td align="left"><p>工作项的地址</p></td>
<td align="left"><p>包含工作项检查的文件的名称</p></td>
<td align="left"><p>在文件中的工作项检查的行数</p></td>
<td align="left"><p>工作项是无效的。 这将最终导致线程池损坏和访问冲突。</p></td>
</tr>
</tbody>
</table>

 

 

 



