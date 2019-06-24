---
title: DoubleDeviceInitFree 规则 (kmdf)
description: DoubleDeviceInitFree 规则指定驱动程序应两次释放设备初始化结构。
ms.assetid: C48FB426-C958-4F4A-A1F0-C91A603DC1FD
ms.date: 05/21/2018
keywords:
- DoubleDeviceInitFree 规则 (kmdf)
topic_type:
- apiref
api_name:
- DoubleDeviceInitFree
api_type:
- NA
ms.localizationpriority: medium
ms.openlocfilehash: 60bfce1144dc7ef265deb5887e035be26743b5dd
ms.sourcegitcommit: 0cc5051945559a242d941a6f2799d161d8eba2a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63350482"
---
# <a name="doubledeviceinitfree-rule-kmdf"></a>DoubleDeviceInitFree 规则 (kmdf)


**DoubleDeviceInitFree**规则指定驱动程序应两次释放设备初始化结构。

[ **WdfDeviceInitFree** ](https://msdn.microsoft.com/library/windows/hardware/ff546050)方法不应调用两次以相同的设备初始化结构。

|              |      |
|--------------|------|
| 驱动程序模型 | KMDF |

<a name="how-to-test"></a>如何测试
-----------

<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">在编译时</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>运行<a href="https://msdn.microsoft.com/library/windows/hardware/ff552808" data-raw-source="[Static Driver Verifier](https://msdn.microsoft.com/library/windows/hardware/ff552808)">Static Driver Verifier</a>并指定<strong>DoubleDeviceInitFree</strong>规则。</p>
使用以下步骤来分析你的代码：
<ol>
<li><a href="https://msdn.microsoft.com/library/windows/hardware/hh454281#preparing-your-source-code" data-raw-source="[Prepare your code (use role type declarations).](https://msdn.microsoft.com/library/windows/hardware/hh454281#preparing-your-source-code)">准备你的代码 （使用角色类型声明）。</a></li>
<li><a href="https://msdn.microsoft.com/library/windows/hardware/hh454281#running-static-driver-verifier" data-raw-source="[Run Static Driver Verifier.](https://msdn.microsoft.com/library/windows/hardware/hh454281#running-static-driver-verifier)">运行的 Static Driver Verifier。</a></li>
<li><a href="https://msdn.microsoft.com/library/windows/hardware/hh454281#viewing-and-analyzing-the-results" data-raw-source="[View and analyze the results.](https://msdn.microsoft.com/library/windows/hardware/hh454281#viewing-and-analyzing-the-results)">查看和分析结果。</a></li>
</ol>
<p>有关详细信息，请参阅<a href="https://msdn.microsoft.com/library/windows/hardware/hh454281" data-raw-source="[Using Static Driver Verifier to Find Defects in Drivers](https://msdn.microsoft.com/library/windows/hardware/hh454281)">以找到缺陷驱动程序中使用 Static Driver Verifier</a>。</p></td>
</tr>
</tbody>
</table>

<a name="applies-to"></a>适用对象
----------

[**WdfDeviceInitFree**](https://msdn.microsoft.com/library/windows/hardware/ff546050)
 

 




