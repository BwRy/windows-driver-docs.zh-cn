---
title: KSPROPERTY\_DIRECTSOUND3DBUFFER\_模式
description: KSPROPERTY\_DIRECTSOUND3DBUFFER\_MODE 属性指定三维声音缓冲区的处理模式。
ms.assetid: a3b15544-c534-47ea-a02e-5c8f9ccee414
keywords:
- KSPROPERTY_DIRECTSOUND3DBUFFER_MODE 音频设备
topic_type:
- apiref
api_name:
- KSPROPERTY_DIRECTSOUND3DBUFFER_MODE
api_location:
- Ksmedia.h
api_type:
- HeaderDef
ms.date: 11/28/2017
ms.localizationpriority: medium
ms.openlocfilehash: 2b56f7486f180992c2b319d4f57061aaa2d3d5ca
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72830812"
---
# <a name="ksproperty_directsound3dbuffer_mode"></a>KSPROPERTY\_DIRECTSOUND3DBUFFER\_模式


KSPROPERTY\_DIRECTSOUND3DBUFFER\_MODE 属性指定三维声音缓冲区的处理模式。

## <span id="ddk_ksproperty_directsound3dbuffer_mode_ks"></span><span id="DDK_KSPROPERTY_DIRECTSOUND3DBUFFER_MODE_KS"></span>


### <a name="span-idusage_summary_tablespanspan-idusage_summary_tablespanspan-idusage_summary_tablespanusage-summary-table"></a><span id="Usage_Summary_Table"></span><span id="usage_summary_table"></span><span id="USAGE_SUMMARY_TABLE"></span>使用情况摘要表

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
<th align="left">“获取”</th>
<th align="left">设置</th>
<th align="left">目标</th>
<th align="left">属性描述符类型</th>
<th align="left">属性值类型</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>“是”</p></td>
<td align="left"><p>“是”</p></td>
<td align="left"><p>大头针</p></td>
<td align="left"><p><a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-ksnodeproperty" data-raw-source="[&lt;strong&gt;KSNODEPROPERTY&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-ksnodeproperty)"><strong>KSNODEPROPERTY</strong></a></p></td>
<td align="left"><p>ULONG</p></td>
</tr>
</tbody>
</table>

 

属性值（操作数据）的类型为 ULONG，并指定声音缓冲区的处理模式。 模式可以具有以下值之一，这些值在头文件 Dsound 中定义：

-   DS3DMODE\_正常

-   DS3DMODE\_HEADRELATIVE

-   DS3DMODE\_禁用

Microsoft Windows SDK 文档中介绍了这些参数的含义。

### <a name="span-idreturn_valuespanspan-idreturn_valuespanspan-idreturn_valuespanreturn-value"></a><span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>返回值

KSPROPERTY\_DIRECTSOUND3DBUFFER\_模式属性请求返回状态\_SUCCESS，以指示已成功完成。 否则，请求将返回相应的错误状态代码。

<a name="remarks"></a>备注
-------

有关 DirectSound 3D 缓冲区的处理模式的其他信息，请参阅 Windows SDK 文档中的以下内容：

-   DS3DBUFFER 结构的**dwMode**成员。

-   **IDirectSound3DBuffer：： GetMode**和**IDirectSound3DBuffer：： SetMode**方法。

<a name="requirements"></a>要求
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>标头</p></td>
<td align="left">Ksmedia （包括 Ksmedia）</td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>另请参阅


[**KSNODEPROPERTY**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ksmedia/ns-ksmedia-ksnodeproperty)

 

 






