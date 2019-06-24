---
title: KSPROPERTY\_流\_质量
description: KSPROPERTY\_流\_质量属性是可选属性，如果 pin 生成质量管理投诉应实现。
ms.assetid: ed4d9baa-967a-41b3-b8b9-910b86230254
keywords:
- KSPROPERTY_STREAM_QUALITY 流式处理媒体设备
topic_type:
- apiref
api_name:
- KSPROPERTY_STREAM_QUALITY
api_location:
- ks.h
api_type:
- HeaderDef
ms.date: 11/28/2017
ms.localizationpriority: medium
ms.openlocfilehash: 7b7df0fa564c1bb76ef6fc5a964d299aa811a855
ms.sourcegitcommit: 0cc5051945559a242d941a6f2799d161d8eba2a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63379957"
---
# <a name="kspropertystreamquality"></a>KSPROPERTY\_流\_质量


KSPROPERTY\_流\_质量属性是可选属性，如果 pin 生成质量管理投诉应实现。

## <span id="ddk_ksproperty_stream_quality_ks"></span><span id="DDK_KSPROPERTY_STREAM_QUALITY_KS"></span>


### <a name="usage-summary-table"></a>使用率摘要表

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
<th>Get</th>
<th>设置</th>
<th>目标</th>
<th>属性描述符类型</th>
<th>属性值类型</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>否</p></td>
<td><p>是</p></td>
<td><p>Pin</p></td>
<td><p><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/content/ks/ns-ks-ksidentifier" data-raw-source="[&lt;strong&gt;KSPROPERTY&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/ks/ns-ks-ksidentifier)"><strong>KSPROPERTY</strong></a></p></td>
<td><p><a href="https://msdn.microsoft.com/library/windows/hardware/ff566730" data-raw-source="[&lt;strong&gt;KSQUALITY_MANAGER&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff566730)"><strong>KSQUALITY_MANAGER</strong></a></p></td>
</tr>
</tbody>
</table>

 

<a name="remarks"></a>备注
-------

发出此请求后，pin 连接会通知质量管理器，从而[ **KSQUALITY** ](https://msdn.microsoft.com/library/windows/hardware/ff566728)具有给定的上下文参数的结构。

如果 pin 不会报告质量问题，它不需要以支持 KSPROPERTY\_流\_质量。

另请参阅[质量管理](https://msdn.microsoft.com/library/windows/hardware/ff568124)。

<a name="requirements"></a>要求
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Header</p></td>
<td>Ks.h （包括 Ks.h）</td>
</tr>
</tbody>
</table>

## <a name="see-also"></a>请参阅


[**KSPROPERTY**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/ks/ns-ks-ksidentifier)

[**KSQUALITY\_MANAGER**](https://msdn.microsoft.com/library/windows/hardware/ff566730)

[**KSQUALITY**](https://msdn.microsoft.com/library/windows/hardware/ff566728)

 

 





