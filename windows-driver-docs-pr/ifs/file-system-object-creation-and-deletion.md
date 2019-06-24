---
title: 文件系统对象的创建和删除
description: 文件系统对象的创建和删除
ms.assetid: 71e342cf-455f-4b01-af55-12568bf06728
keywords:
- 最小重定向程序 WDK，对象创建
- 最小重定向程序 WDK、 对象删除
- 文件对象 WDK 微型-重定向程序
- 对象 WDK 微型-重定向程序
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 3b2a12233c762a012bcb08701051bc51452c35e3
ms.sourcegitcommit: 0cc5051945559a242d941a6f2799d161d8eba2a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63383831"
---
# <a name="file-system-object-creation-and-deletion"></a>文件系统对象的创建和删除


数例程由网络微型重定向实现适用于文件的创建和删除。 RDBSS 提取此过程通过创建多个结构包括 SRV\_打开、 FCB 和 FOBX 结构，它是引用计数。 创建或打开文件系统对象通常需要创建 SRV\_打开、 FCB 和 FOBX 结构。 正常过程的目的是，要调用的 RDBSS [ **MRxCreate** ](https://msdn.microsoft.com/library/windows/hardware/ff549862)例程实现网络微型-重定向器要填充到这些结构的信息。 还有可能折叠一个打开/创建的文件请求上现有 SRV\_打开结构使用[ **MRxShouldTryToCollapseThisOpen** ](https://msdn.microsoft.com/library/windows/hardware/ff550817)并[ **MRxCollapseOpen** ](https://msdn.microsoft.com/library/windows/hardware/ff549847)例程。

在网络重定向程序的上下文中，文件对象引用的文件控制块 (FCB) 结构和文件对象扩展 (FOBX) 结构。 没有文件对象和 FOBXs 之间具有一对一的对应关系。 多个文件对象将引用同一个 FCB 结构，它代表单个文件的远程服务器上的某个位置。 客户端可以对同一 FCB 几个不同的打开请求 （NtCreateFile 请求），其中每项功能将创建一个新的文件对象。 RDBSS 和网络微型-重定向程序可以选择发送更少[ **MRxCreate** ](https://msdn.microsoft.com/library/windows/hardware/ff549862)比接收，实际上共享服务器打开请求的 NtCreateFile 请求的请求数 (SRV\_打开)在多个 FOBXs。

RDBSS 和网络微型重定向不一定是关闭 SRV\_打开结构当用户关闭文件。 可以尝试重复使用 SRV RDBSS\_打开结构和数据而不显示任何与服务器联系。 某些 Windows 应用程序可以打开、 读取和关闭文件和相同的文件，快速重新打开。 在这些情况下，重复使用 SRV\_打开结构可以提高性能。

有几个例程用于关闭和完成这些数据结构并释放任何内存或当不再需要时使用其他资源。 这些例程包括[ **MRxCleanupFobx**](https://msdn.microsoft.com/library/windows/hardware/ff549841)， [ **MRxCloseSrvOpen**](https://msdn.microsoft.com/library/windows/hardware/ff549845)， [ **MRxDeallocateForFcb** ](https://msdn.microsoft.com/library/windows/hardware/ff549871)， [ **MRxDeallocateForFobx**](https://msdn.microsoft.com/library/windows/hardware/ff549872)，以及[ **MRxForceClosed**](https://msdn.microsoft.com/library/windows/hardware/ff550677)。

下表列出了可以由网络微型重定向的文件系统对象的创建和删除操作的例程。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">例程</th>
<th align="left">描述</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><a href="https://msdn.microsoft.com/library/windows/hardware/ff549838" data-raw-source="[&lt;strong&gt;MRxAreFilesAliased&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff549838)"><strong>MRxAreFilesAliased</strong></a></td>
<td align="left"><p>RDBSS 调用此例程来查询网络微型重定向，如果两个 FCB 对象表示相同的文件。 RDBSS 调用此例程时处理两个文件看上去相同但具有不同的名称 （MS-DOS 短名称和长名称，例如）。</p></td>
</tr>
<tr class="even">
<td align="left"><a href="https://msdn.microsoft.com/library/windows/hardware/ff549841" data-raw-source="[&lt;strong&gt;MRxCleanupFobx&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff549841)"><strong>MRxCleanupFobx</strong></a></td>
<td align="left"><p>RDBSS 调用此例程以请求网络微型重定向，关闭文件系统对象扩展。 RDBSS 发出响应接收对文件对象 IRP_MJ_CLEANUP 此调用。</p></td>
</tr>
<tr class="odd">
<td align="left"><a href="https://msdn.microsoft.com/library/windows/hardware/ff549845" data-raw-source="[&lt;strong&gt;MRxCloseSrvOpen&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff549845)"><strong>MRxCloseSrvOpen</strong></a></td>
<td align="left"><p>RDBSS 调用此例程以请求网络微型重定向关闭 SRV_OPEN 对象。</p></td>
</tr>
<tr class="even">
<td align="left"><a href="https://msdn.microsoft.com/library/windows/hardware/ff549847" data-raw-source="[&lt;strong&gt;MRxCollapseOpen&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff549847)"><strong>MRxCollapseOpen</strong></a></td>
<td align="left"><p>RDBSS 调用此例程以请求网络微型重定向折叠到现有 SRV_OPEN 上打开的文件系统的请求。</p></td>
</tr>
<tr class="odd">
<td align="left"><a href="https://msdn.microsoft.com/library/windows/hardware/ff549862" data-raw-source="[&lt;strong&gt;MRxCreate&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff549862)"><strong>MRxCreate</strong></a></td>
<td align="left"><p>RDBSS 调用此例程以请求网络微型重定向创建文件系统对象。 响应接收 IRP_MJ_CREATE RDBSS 颁发此调用。</p></td>
</tr>
<tr class="even">
<td align="left"><a href="https://msdn.microsoft.com/library/windows/hardware/ff549871" data-raw-source="[&lt;strong&gt;MRxDeallocateForFcb&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff549871)"><strong>MRxDeallocateForFcb</strong></a></td>
<td align="left"><p>RDBSS 调用此例程以请求网络微型重定向解除分配 FCB。 此调用是对关闭文件系统对象的请求的响应中。</p></td>
</tr>
<tr class="odd">
<td align="left"><a href="https://msdn.microsoft.com/library/windows/hardware/ff549872" data-raw-source="[&lt;strong&gt;MRxDeallocateForFobx&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff549872)"><strong>MRxDeallocateForFobx</strong></a></td>
<td align="left"><p>RDBSS 调用来请求网络微型重定向解除分配 FOBX 此例程。 此调用是对关闭文件系统对象的请求的响应中。</p></td>
</tr>
<tr class="even">
<td align="left"><a href="https://msdn.microsoft.com/library/windows/hardware/ff549878" data-raw-source="[&lt;strong&gt;MRxExtendForCache&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff549878)"><strong>MRxExtendForCache</strong></a></td>
<td align="left"><p>RDBSS 调用此例程以请求网络微型重定向扩展一个文件，则将文件缓存的缓存管理器时。</p></td>
</tr>
<tr class="odd">
<td align="left"><a href="https://msdn.microsoft.com/library/windows/hardware/ff549879" data-raw-source="[&lt;strong&gt;MRxExtendForNonCache&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff549879)"><strong>MRxExtendForNonCache</strong></a></td>
<td align="left"><p>RDBSS 调用此例程以请求网络微型重定向扩展一个文件，当缓存管理器不缓存该文件。</p></td>
</tr>
<tr class="even">
<td align="left"><a href="https://msdn.microsoft.com/library/windows/hardware/ff550669" data-raw-source="[&lt;strong&gt;MRxFlush&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff550669)"><strong>MRxFlush</strong></a></td>
<td align="left"><p>RDBSS 调用此例程以请求网络微型重定向刷新文件系统对象。 RDBSS 发出响应接收 IRP_MJ_FLUSH_BUFFERS 此调用。</p></td>
</tr>
<tr class="odd">
<td align="left"><a href="https://msdn.microsoft.com/library/windows/hardware/ff550677" data-raw-source="[&lt;strong&gt;MRxForceClosed&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff550677)"><strong>MRxForceClosed</strong></a></td>
<td align="left"><p>RDBSS 调用此例程以请求网络微型重定向强制关闭。 此例程称为 SRV_OPEN 的条件不是很好或 SRV_OPEN 标记为已关闭时。</p></td>
</tr>
<tr class="even">
<td align="left"><a href="https://msdn.microsoft.com/library/windows/hardware/ff550691" data-raw-source="[&lt;strong&gt;MRxIsLockRealizable&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff550691)"><strong>MRxIsLockRealizable</strong></a></td>
<td align="left"><p>RDBSS 调用此例程以请求网络微型重定向，指示是否在此 NET_ROOT 上支持字节范围锁。</p></td>
</tr>
<tr class="odd">
<td align="left"><a href="https://msdn.microsoft.com/library/windows/hardware/ff550817" data-raw-source="[&lt;strong&gt;MRxShouldTryToCollapseThisOpen&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff550817)"><strong>MRxShouldTryToCollapseThisOpen</strong></a></td>
<td align="left"><p>RDBSS 调用此例程以请求网络微型重定向指示是否 RDBSS 应尝试并折叠了打开请求到现有的文件系统对象。</p></td>
</tr>
<tr class="even">
<td align="left"><a href="https://msdn.microsoft.com/library/windows/hardware/ff550839" data-raw-source="[&lt;strong&gt;MRxTruncate&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff550839)"><strong>MRxTruncate</strong></a></td>
<td align="left"><p>RDBSS 调用此例程以请求网络微型重定向截断文件系统对象。</p></td>
</tr>
<tr class="odd">
<td align="left"><a href="https://msdn.microsoft.com/library/windows/hardware/ff550844" data-raw-source="[&lt;strong&gt;MRxZeroExtend&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/hardware/ff550844)"><strong>MRxZeroExtend</strong></a></td>
<td align="left"><p>RDBSS 调用此例程以请求网络微型重定向扩展用清除零填充该文件，如果文件大小大于 FCB 的有效数据长度的文件系统对象。</p></td>
</tr>
</tbody>
</table>

 

 

 



