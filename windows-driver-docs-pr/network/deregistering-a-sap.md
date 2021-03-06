---
title: 取消注册 SAP
description: 取消注册 SAP
ms.assetid: 2d279348-b58e-4d7e-ac8b-211e9b8a0622
keywords:
- 服务访问点 WDK CoNDIS
- Sap WDK CoNDIS
- 取消注册 Sap
- 正在注销 Sap
- 删除 Sap
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 051ca43c6e04cce2c1780929482b8980993cace4
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72834922"
---
# <a name="deregistering-a-sap"></a>取消注册 SAP





面向连接的客户端使用[**NdisClDeregisterSap**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nf-ndis-ndisclderegistersap)注销 SAP。

下图显示了取消注册 SAP 的呼叫管理器的客户端。

![说明调用管理器的客户端注销 sap 的关系图](images/cm-04.png)

下图显示了注销 SAP 的 MCM 驱动程序的客户端。

![说明 mcm 驱动程序的客户端注销 sap 的示意图](images/fig1-04.png)

调用**NdisClDeregisterSap**会导致 NDIS 调用调用管理器或 MCM 驱动程序的[**ProtocolCmDeregisterSap**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nc-ndis-protocol_cm_deregister_sap)函数。 在*ProtocolCmDeregisterSap*中，呼叫管理器或 MCM 驱动程序可能会与网络控制设备或其他特定于媒体的代理进行通信，以便在网络上取消注册 SAP。 此外， *ProtocolCmDeregisterSap*必须释放为 SAP 动态分配的任何资源。

*ProtocolCmDeregisterSap*可以同步或异步完成。 若要异步完成，调用管理器的*ProtocolCmDeregisterSap*函数将调用[**NdisCmDeregisterSapComplete**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nf-ndis-ndiscmderegistersapcomplete)。 MCM 驱动程序的*ProtocolCmDeregisterSap*函数将调用[**NdisMCmDeregisterSapComplete**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nf-ndis-ndismcmderegistersapcomplete)。 **Ndis （M） CmDegisterSapComplete**通知 ndis 和客户端：调用管理器已完成其*ProtocolCmDeregisterSap*函数之前为其返回了 NDIS\_状态的 SAP 注销请求\_未.

调用**ndis （M） CmDeregisterSapComplete**导致 ndis 调用客户端的[**ProtocolClDeregisterSapComplete**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nc-ndis-protocol_cl_deregister_sap_complete)函数。 调用*ProtocolClDeregisterSapComplete*表示客户端对**NdisClDeregisterSap**的前一调用已由调用管理器或 MCM 驱动程序处理。

请注意，客户端可以取消注册 SAP，而不会影响已在该 SAP 上收到的传入呼叫，并且不会影响该传入呼叫的 VC。

 

 





