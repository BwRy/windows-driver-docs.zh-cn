---
title: Bug 检查 0x138 GPIO_CONTROLLER_DRIVER_ERROR
description: GPIO_CONTROLLER_DRIVER_ERROR bug 检查具有 0x00000138 值。 此 bug 检查指示 GPIO 类扩展驱动程序遇到错误。
ms.assetid: 4025D968-10F9-4F2F-953F-914A4BE7D883
keywords:
- Bug 检查 0x138 GPIO_CONTROLLER_DRIVER_ERROR
- GPIO_CONTROLLER_DRIVER_ERROR
ms.date: 05/23/2017
topic_type:
- apiref
api_name:
- GPIO_CONTROLLER_DRIVER_ERROR
api_type:
- NA
ms.localizationpriority: medium
ms.openlocfilehash: f55a14ae7b0c72a0b49436fee3e8bd054ab9408e
ms.sourcegitcommit: 0cc5051945559a242d941a6f2799d161d8eba2a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63347839"
---
# <a name="bug-check-0x138-gpiocontrollerdrivererror"></a>Bug 检查 0x138：GPIO\_控制器\_驱动程序\_错误


GPIO\_控制器\_驱动程序\_错误 bug 检查的值为 0x00000138。 此 bug 检查指示 GPIO 类扩展驱动程序遇到错误。

> [!IMPORTANT]
> 本主题面向程序员。 如果你已使用计算机时收到一个蓝色的屏幕，错误代码的客户，请参阅[疑难解答蓝屏错误](https://windows.microsoft.com/windows-10/troubleshoot-blue-screen-errors)。


## <a name="gpiocontrollerdrivererror-parameters"></a>GPIO\_控制器\_驱动程序\_错误参数


*参数 1*指示冲突类型。 其他参数的含义取决于的值*参数 1*。

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
<td align="left"><p>1</p></td>
<td align="left"><p>GSIV</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>管理特定 GSIV GPIO 控制器未注册。</p></td>
</tr>
<tr class="even">
<td align="left"><p>2</p></td>
<td align="left"><p>上下文值</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>客户端驱动程序指定为的锁无效的上下文或解除锁定请求。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>3</p></td>
<td align="left"><p>指示是否正在请求的关键的转换。</p></td>
<td align="left"><p>指示是否银行已在 F1 由于非关键的转换。</p></td>
<td align="left"><p>指示是否银行已在 F1 由于关键的转换。</p></td>
<td align="left"><p>PoFx 请求 GPIO 控制器发送一家银行通过不合适的 F1 电源状态和/或关键转换。</p></td>
</tr>
<tr class="even">
<td align="left"><p>4</p></td>
<td align="left"><p>指示是否正在请求的关键的转换。</p></td>
<td align="left"><p>指示是否银行为 F1 中由于非关键的转换。</p></td>
<td align="left"><p>指示是否银行为 F1 中由于关键的转换。</p></td>
<td align="left"><p>PoFx 请求 GPIO 控制器发送一家银行通过不合适的 F0 电源状态和/或关键转换。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>5</p></td>
<td align="left"><p>NTSTATUS</p></td>
<td align="left"><p>GPIO 设备扩展</p></td>
<td align="left"><p>GPIO 中断参数</p></td>
<td align="left"><p>在 Soc GPIO 中断操作失败。</p></td>
</tr>
<tr class="even">
<td align="left"><p>6</p></td>
<td align="left"><p>NTSTATUS</p></td>
<td align="left"><p>GPIO 设备扩展</p></td>
<td align="left"><p>GPIO IO 参数</p></td>
<td align="left"><p>在 Soc GPIO IO 操作失败。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>7</p></td>
<td align="left"><p>修订 ID</p></td>
<td align="left"><p>函数索引</p></td>
<td align="left"><p>保留</p></td>
<td align="left"><p>_DSM 方法返回的格式不正确的数据。</p></td>
</tr>
</tbody>
</table>

 

 

 



