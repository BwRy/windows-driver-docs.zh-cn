---
title: 接收操作
description: 接收操作
ms.assetid: 9ec2ba38-36dd-42d2-b0a8-0abe4d1bb847
keywords:
- 接收操作 WDK 本机 802.11 IHV 扩展 DLL
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: ed6f88553eea6c202702b93b1f441e0bd5f9f77c
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72843472"
---
# <a name="receive-operations"></a>接收操作




 

当执行后连接操作（通过调用[*Dot11ExtIhvPerformPostAssociate*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wlanihv/nc-wlanihv-dot11extihv_perform_post_associate)启动）时，操作系统将调用[*Dot11ExtIhvReceivePacket*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wlanihv/nc-wlanihv-dot11extihv_receive_packet)函数将数据包转发到通过无线 LAN （WLAN）适配器接收的 HV 扩展 DLL。 有关后处理后操作的详细信息，请参阅[之后的关联操作](post-association-operations.md)。

为了接收数据包，IHV Extension DLL 必须调用[**Dot11ExtSetEtherTypeHandling**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wlanihv/nc-wlanihv-dot11ext_set_ethertype_handling)来注册一个或多个 IEEE EtherTypes 的列表。 当使用与此列表中的条目相匹配的 EtherType 接收数据包时，操作系统将调用[*Dot11ExtIhvReceivePacket*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wlanihv/nc-wlanihv-dot11extihv_receive_packet)函数并通过函数的*pvInBuffer*参数传递数据包缓冲区。

**请注意**  在 dll 完成预关联操作之前，必须先调用[**Dot11ExtSetEtherTypeHandling**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wlanihv/nc-wlanihv-dot11ext_set_ethertype_handling) 。 有关此操作的详细信息，请参阅[预关联操作](pre-association-operations.md)。

 

调用[*Dot11ExtIhvReceivePacket*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wlanihv/nc-wlanihv-dot11extihv_receive_packet)时， *pvInBuffer*参数指向由包含整个802.11 数据包的操作系统分配的缓冲区，包括媒体访问控制（MAC）标头、LLC 封装（如有必要）和负载数据。

IHV 扩展 DLL 可以在对[*Dot11ExtIhvReceivePacket*](https://docs.microsoft.com/windows-hardware/drivers/ddi/wlanihv/nc-wlanihv-dot11extihv_receive_packet)的调用中将响应发送到收到的数据包。 在这种情况下，DLL 必须遵循[发送操作](send-operations.md)中所述的准则。

 

 





