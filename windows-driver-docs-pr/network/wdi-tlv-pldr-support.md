---
title: WDI_TLV_PLDR_SUPPORT
description: WDI_TLV_PLDR_SUPPORT 是 TLV，指定是否支持 PLDR （平台级别重置）。
ms.assetid: BC1BE1A7-AA2D-4D11-A75A-EC0143343F33
ms.date: 07/18/2017
keywords:
- 从 Windows Vista 开始 WDI_TLV_PLDR_SUPPORT 网络驱动程序
ms.localizationpriority: medium
ms.openlocfilehash: 295ccd496becfbd8158c30071bb12c220351cf39
ms.sourcegitcommit: fb7d95c7a5d47860918cd3602efdd33b69dcf2da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2019
ms.locfileid: "67380739"
---
# <a name="wditlvpldrsupport"></a>WDI\_TLV\_PLDR\_支持


WDI\_TLV\_PLDR\_支持是 TLV，指定是否支持 PLDR （平台级别重置）。

**请注意**  此 TLV 添加 Windows 10，版本 1511，WDI 版本 1.0.10 中。

 

## <a name="tlv-type"></a>TLV 类型


0x11A

## <a name="length"></a>长度


超出 UINT8 的大小 （以字节为单位）。

## <a name="values"></a>值


| 在任务栏的搜索框中键入  | 描述                                                                                                                                                                                                                       |
|-------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| UINT8 | 指定是否支持 PLDR。 如果设备或总线不支持重置功能 （通常通过查询的 ACPI 或 PCI 方法），此值设置为 0。 一个非零值指定支持重置功能。 |

 

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

## <a name="see-also"></a>请参阅


[PLDR](https://docs.microsoft.com/windows-hardware/drivers/network/wdi-pldr-and-fldr)

 

 




