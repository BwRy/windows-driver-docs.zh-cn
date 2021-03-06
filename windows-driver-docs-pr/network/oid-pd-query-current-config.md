---
title: OID_PD_QUERY_CURRENT_CONFIG
description: NDIS 协议或筛选器驱动程序将 OID_PD_QUERY_CURRENT_CONFIG 的对象标识符（OID）方法请求发送到支持 PD 的微型端口驱动程序，以检索 PD 状态和功能。 所有支持 PD 的微型端口驱动程序都必须处理此 OID 请求。
ms.assetid: 1BF09EAE-9D03-4655-98CD-D3A10BF48A48
ms.date: 08/08/2017
keywords: -从 Windows Vista 开始 OID_PD_QUERY_CURRENT_CONFIG 网络驱动程序
ms.localizationpriority: medium
ms.openlocfilehash: c99b86721c23064c6983e5f7a2324162d116fcbd
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72844065"
---
# <a name="oid_pd_query_current_config"></a>OID\_PD\_QUERY\_当前\_配置


NDIS 协议或筛选器驱动程序将\_PD\_QUERY\_当前\_CONFIG 的对象标识符（OID）方法请求发送到支持 PD 的微型端口驱动程序，以检索 PD 状态和功能。 所有支持 PD 的微型端口驱动程序都必须处理此 OID 请求。

[ **\_OID 的 NDIS\_请求**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/ns-ndis-_ndis_oid_request)结构的**InformationBuffer**成员包含指向缓冲区的指针。 此缓冲区包含以下数据：

-   [**NDIS\_PD\_CONFIG**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_pd_config)结构

<a name="remarks"></a>备注
-------

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
<td><p>Windows 10</p></td>
</tr>
<tr class="even">
<td><p>最低受支持的服务器</p></td>
<td><p>Windows Server 2016</p></td>
</tr>
<tr class="odd">
<td><p>标头</p></td>
<td>Ntddndis （包括 Ndis .h）</td>
</tr>
</tbody>
</table>

## <a name="see-also"></a>另请参阅


[*MiniportOidRequest*](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/nc-ndis-miniport_oid_request)

[**NDIS\_PD\_CONFIG**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_pd_config)

[**NDIS\_OID\_请求**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ndis/ns-ndis-_ndis_oid_request)

 

 




