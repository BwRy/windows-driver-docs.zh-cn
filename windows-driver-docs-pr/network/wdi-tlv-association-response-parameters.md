---
title: WDI_TLV_ASSOCIATION_RESPONSE_PARAMETERS
description: WDI_TLV_ASSOCIATION_RESPONSE_PARAMETERS 是包含关联响应参数 OID_WDI_TASK_SEND_AP_ASSOCIATION_RESPONSE TLV。
ms.assetid: FB116762-2064-48FA-B630-D5AE54657D10
ms.date: 07/18/2017
keywords:
- 从 Windows Vista 开始 WDI_TLV_ASSOCIATION_RESPONSE_PARAMETERS 网络驱动程序
ms.localizationpriority: medium
ms.openlocfilehash: 1266b946d737622a64340caf75ecfd3e0ae6702b
ms.sourcegitcommit: fb7d95c7a5d47860918cd3602efdd33b69dcf2da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2019
ms.locfileid: "67354936"
---
# <a name="wditlvassociationresponseparameters"></a>WDI\_TLV\_关联\_响应\_参数


WDI\_TLV\_关联\_响应\_参数是包含关联响应参数 TLV [OID\_WDI\_任务\_发送\_亚太\_关联\_响应](https://docs.microsoft.com/windows-hardware/drivers/network/oid-wdi-task-send-ap-association-response)。

## <a name="tlv-type"></a>TLV 类型


0x97

## <a name="length"></a>长度


所有包含的元素的大小的总和 （以字节为单位）。

## <a name="values"></a>值


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>在任务栏的搜索框中键入</th>
<th>描述</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>UINT8</td>
<td>指定接受关联的请求。
<p>有效的值为的 0 （不接受） 和 1 （接受）。</p></td>
</tr>
<tr class="even">
<td>UINT16</td>
<td>指定原因代码。 如果接受请求设置为 0，此字段提供了要将发回给对等方适配器的原因代码。</td>
</tr>
</tbody>
</table>

 

<a name="requirements"></a>要求
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>最低受支持的客户端</p></td>
<td><p>Windows 10</p></td>
</tr>
<tr class="even">
<td><p>最低受支持的服务器</p></td>
<td><p>Windows Server 2016</p></td>
</tr>
<tr class="odd">
<td><p>Header</p></td>
<td>Wditypes.hpp</td>
</tr>
</tbody>
</table>

 

 




