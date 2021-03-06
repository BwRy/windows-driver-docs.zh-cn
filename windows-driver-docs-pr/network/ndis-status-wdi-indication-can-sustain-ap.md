---
title: NDIS_STATUS_WDI_INDICATION_CAN_SUSTAIN_AP
description: 微型端口驱动程序使用 NDIS_STATUS_WDI_INDICATION_CAN_SUSTAIN_AP 以指示该端口已准备好后以前，该值指示 NDIS_STATUS_WDI_INDICATION_STOP_AP 接收 OID_WDI_TASK_START_AP 请求。
ms.assetid: 638822A9-4CED-4564-86B3-8BC9DBA05DD3
ms.date: 07/18/2017
keywords:
- 从 Windows Vista 开始 NDIS_STATUS_WDI_INDICATION_CAN_SUSTAIN_AP 网络驱动程序
ms.localizationpriority: medium
ms.openlocfilehash: c85f147bda630839523ab23a412755acc4270b74
ms.sourcegitcommit: fb7d95c7a5d47860918cd3602efdd33b69dcf2da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2019
ms.locfileid: "67385236"
---
# <a name="ndisstatuswdiindicationcansustainap"></a>NDIS\_状态\_WDI\_指示\_可以\_SUSTAIN\_亚太


微型端口驱动程序使用 NDIS\_状态\_WDI\_指示\_可以\_SUSTAIN\_AP 以指示该端口已准备好接收[OID\_WDI\_任务\_启动\_AP](oid-wdi-task-start-ap.md)后以前，该值指示请求[NDIS\_状态\_WDI\_指示\_停止\_亚太](ndis-status-wdi-indication-stop-ap.md)。

| Object |
|--------|
| Port   |

 

## <a name="payload-data"></a>有效负载数据


| 在任务栏的搜索框中键入                                                                                     | 允许多个 TLV 实例 | 可选 | 描述                                                     |
|------------------------------------------------------------------------------------------|--------------------------------|----------|-----------------------------------------------------------------|
| [**WDI\_TLV\_INDICATION\_CAN\_SUSTAIN\_AP**](https://docs.microsoft.com/windows-hardware/drivers/network/wdi-tlv-indication-can-sustain-ap) |                                |          | 现在，适配器的原因可以承受 802.11 AP 的功能。 |

 

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
<td>Dot11wdi.h</td>
</tr>
</tbody>
</table>

 

 




