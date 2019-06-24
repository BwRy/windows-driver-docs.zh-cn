---
title: WDI_TLV_CONNECTION_QUALITY_PARAMETERS
description: WDI_TLV_CONNECTION_QUALITY_PARAMETERS 是包含所需的 Wi-fi 连接质量提示 TLV。
ms.assetid: A371FD3A-5BF9-4921-AB8E-1651789FA9A1
ms.date: 07/18/2017
keywords:
- 从 Windows Vista 开始 WDI_TLV_CONNECTION_QUALITY_PARAMETERS 网络驱动程序
ms.localizationpriority: medium
ms.openlocfilehash: 3ce8680e00d04276a7bb7fd80a96db8ae9ae977c
ms.sourcegitcommit: 0cc5051945559a242d941a6f2799d161d8eba2a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63357258"
---
# <a name="wditlvconnectionqualityparameters"></a>WDI\_TLV\_连接\_质量\_参数


WDI\_TLV\_连接\_质量\_参数是包含所需的 Wi-fi 连接质量提示 TLV。

## <a name="tlv-type"></a>TLV 类型


0xA3

## <a name="length"></a>长度


UINT32 大小 （以字节为单位）。

## <a name="values"></a>值


| 在任务栏的搜索框中键入   | 描述                                                                                                                          |
|--------|--------------------------------------------------------------------------------------------------------------------------------------|
| UINT32 | 所需的 Wi-fi 连接质量提示中, 定义[ **WDI\_连接\_质量\_提示**](https://msdn.microsoft.com/library/windows/hardware/dn897807)。 |

 

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

 

 



