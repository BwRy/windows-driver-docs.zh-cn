---
title: Bug 检查 0x188 CLUSTER_CSVFS_LIVEDUMP
description: CLUSTER_CSVFS_LIVEDUMP bug 检查具有 0x00000188 值。 这指示 CSVFS 启动此 livedump 来帮助调试不一致的状态。
ms.assetid: 220B0CDB-6E10-4262-A07C-042E8BA21D7F
keywords:
- Bug 检查 0x188 CLUSTER_CSVFS_LIVEDUMP
- CLUSTER_CSVFS_LIVEDUMP
ms.date: 05/23/2017
topic_type:
- apiref
api_name:
- CLUSTER_CSVFS_LIVEDUMP
api_type:
- NA
ms.localizationpriority: medium
ms.openlocfilehash: 2ee3a658201214892da36b18bf82e436cd75b104
ms.sourcegitcommit: d03b44343cd32b3653d0471afcdd3d35cb800c0d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2019
ms.locfileid: "67519866"
---
# <a name="bug-check-0x188-clustercsvfslivedump"></a>Bug 检查 0x188：CLUSTER\_CSVFS\_LIVEDUMP


群集\_CSVFS\_LIVEDUMP bug 检查的值为 0x00000188。 这指示 CSVFS 启动此 livedump 来帮助调试不一致的状态。

> [!IMPORTANT]
> 本主题面向程序员。 如果你已使用计算机时收到一个蓝色的屏幕，错误代码的客户，请参阅[疑难解答蓝屏错误](https://www.windows.com/stopcode)。


## <a name="clustercsvfslivedump-parameters"></a>群集\_CSVFS\_LIVEDUMP 参数


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">参数</th>
<th align="left">描述</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">1</td>
<td align="left"><p>原因代码</p>
0x1:缓存清除 oplock 降级为无上的已失败
<p>2-地址 CSVFS ！ _SCB</p>
0x2:机会锁升级时从无缓存清除已失败
<p>2-地址 CSVFS ！ _SCB</p>
0x3:在设置清除失败模式的缓存清除
<p>2-地址 CSVFS ！ _SCB</p>
0x4:缓存刷新上 oplock 降级为无失败
<p>2-地址 CSVFS ！ _SCB</p></td>
</tr>
<tr class="even">
<td align="left">2</td>
<td align="left">请参阅参数 1</td>
</tr>
<tr class="odd">
<td align="left">3</td>
<td align="left">保留</td>
</tr>
<tr class="even">
<td align="left">4</td>
<td align="left">保留</td>
</tr>
</tbody>
</table>

 

<a name="cause"></a>原因
-----

第一个参数包含当 CSVFS 检测到当前状态可能会导致数据损坏，原因代码或其他类型的不一致，则会生成与实时转储此状态代码。 Parameter1 具有代码指向此实时转储哪些方案创建的。 其他参数应解释的原因代码的上下文中。

 

 




