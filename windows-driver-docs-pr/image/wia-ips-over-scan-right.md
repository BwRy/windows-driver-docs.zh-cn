---
title: WIA\_IPS\_转移\_扫描\_右
description: WIA\_IP\_转移\_扫描\_RIGHT 属性以及 WIA\_IP\_通过\_扫描\_LEFT，WIA\_IP\_转移\_扫描\_上边缘和 WIA\_IPS\_转移\_扫描\_底部用于通过扫描英寸为单位的千分之几秒中配置的金额 (0.001 \ 0034;)单元，相对于物理文档。
ms.assetid: 17259314-2102-46B9-A493-7F879A7D0604
keywords:
- WIA_IPS_OVER_SCAN_RIGHT 成像设备
topic_type:
- apiref
api_name:
- WIA_IPS_OVER_SCAN_RIGHT
api_location:
- Wiadef.h
api_type:
- HeaderDef
ms.date: 05/22/2018
ms.localizationpriority: medium
ms.openlocfilehash: c3fe67bd9c62239e23157482a2476b64ff572f08
ms.sourcegitcommit: 0cc5051945559a242d941a6f2799d161d8eba2a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63354646"
---
# <a name="wiaipsoverscanright"></a>WIA\_IPS\_转移\_扫描\_右


**WIA\_IPS\_转移\_扫描\_右**属性连同[ **WIA\_IP\_通过\_扫描\_左侧**](wia-ips-over-scan-left.md)， [ **WIA\_IP\_通过\_扫描\_顶部**](wia-ips-over-scan-top.md)，和[ **WIA\_IP\_转移\_扫描\_底部**](wia-ips-over-scan-bottom.md)用于通过扫描千分之一英寸 （0.001 英寸） 单元中配置的量相对于物理文档。 WIA 微型驱动程序创建并维护此属性。




属性类型：VT\_UI4

有效值：WIA\_PROP\_RANGE

访问权限：读/写

<a name="remarks"></a>备注
-------

此属性仅适用于所有可编程图像数据源项，包括平板 (WIA\_类别\_平板) 和送纸器 (WIA\_类别\_送纸器)，但仅当[ **WIA\_IPS\_转移\_扫描**](wia-ips-over-scan.md)支持属性。 如果支持，此属性是必需的。

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
<td>Wiadef.h （包括 Wiadef.h）</td>
</tr>
</tbody>
</table>

 

 





