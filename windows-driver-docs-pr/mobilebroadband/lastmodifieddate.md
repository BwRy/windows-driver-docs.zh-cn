---
title: LastModifiedDate
description: LastModifiedDate
ms.assetid: e0ef7ca0-0c3d-4e71-af2e-ead90013e561
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 5f688bf5d02d98787157e897488532211244c7f7
ms.sourcegitcommit: f017184b00f59b088df87a5bd85fec51b7aed8b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72323655"
---
# <a name="lastmodifieddate"></a>LastModifiedDate

[!include[MBAE deprecation warning](mbae-deprecation-warning.md)]

LastModifiedDate 元素指定上次更改服务元数据包时的时间戳。 操作系统基于此信息选择并加载最新的服务元数据包版本。

## <a name="span-idusagespanspan-idusagespanspan-idusagespanusage"></a><span id="Usage"></span><span id="usage"></span><span id="USAGE"></span>使用情况


``` syntax
<LastModifiedDate>
  text
</LastModifiedDate>
```

## <a name="span-idattributesspanspan-idattributesspanspan-idattributesspanattributes"></a><span id="Attributes"></span><span id="attributes"></span><span id="ATTRIBUTES"></span>属性


没有特性。

## <a name="span-idtext_valuespanspan-idtext_valuespanspan-idtext_valuespantext-value"></a><span id="Text_value"></span><span id="text_value"></span><span id="TEXT_VALUE"></span>文本值


Timestamp 值用协调世界时（UTC）格式表示。

## <a name="span-idchild_elementsspanspan-idchild_elementsspanspan-idchild_elementsspanchild-elements"></a><span id="Child_elements"></span><span id="child_elements"></span><span id="CHILD_ELEMENTS"></span>子元素


没有子元素。

## <a name="span-idparent_elementsspanspan-idparent_elementsspanspan-idparent_elementsspanparent-elements"></a><span id="Parent_elements"></span><span id="parent_elements"></span><span id="PARENT_ELEMENTS"></span>父元素


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>元素</th>
<th>描述</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="metadatakey.md" data-raw-source="[MetadataKey](metadatakey.md)">MetadataKey</a></p></td>
<td><p><a href="metadatakey.md" data-raw-source="[MetadataKey](metadatakey.md)">MetadataKey</a>元素指定设备元数据包的属性。 这包括：</p>
<ul>
<li><p>设备支持的每个硬件功能的标识符。</p></li>
<li><p>包中的文本字符串的语言特定区域设置。</p></li>
</ul></td>
</tr>
</tbody>
</table>

 

## <a name="span-idxsdspanspan-idxsdspanxsd"></a><span id="XSD"></span><span id="xsd"></span>XSD.EXE


``` syntax
<xs:element name="LastModifiedDate" type="xs:dateTime" />
```

## <a name="span-idremarksspanspan-idremarksspanspan-idremarksspanremarks"></a><span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>备注


-   LastModifiedDate 元素的值必须表示元数据包上次更改的实际时间。

-   每次向 Windows 硬件开发人员中心仪表板提交服务元数据包，以便通过 Windows 元数据和 Internet 服务（WMIS）进行分发时，将在对包进行验证后更新 LastModifiedDate 元素。

LastModifiedDate 元素是必需的。

 

 





