---
title: 使用网络驱动程序中的共享内存
description: 使用网络驱动程序中的共享内存
ms.assetid: f7dfe785-6c1a-4f56-9018-76be9cdec7fc
keywords:
- 网络驱动程序 WDK，共享内存
- 内存 WDK 网络
- 共享的内存 WDK 网络
- 共享内存地址空间
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 806c597dcb2e7193567c5b757ea541a3c5cba99a
ms.sourcegitcommit: 0cc5051945559a242d941a6f2799d161d8eba2a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63373783"
---
# <a name="using-shared-memory-in-network-drivers"></a>使用网络驱动程序中的共享内存





总线 master 直接内存访问 (DMA) 设备的微型端口驱动程序分配的网络接口卡 (NIC) 和微型端口驱动程序使用共享的内存。

[**NdisMAllocateSharedMemory** ](https://msdn.microsoft.com/library/windows/hardware/ff562782)可以由总线 master 微型端口驱动程序分配内存来存放永久共享之间的网络适配器和微型端口驱动程序调用。 此函数返回虚拟地址和共享内存的物理地址。 直到调用到的地址是有效[ **NdisMFreeSharedMemory** ](https://msdn.microsoft.com/library/windows/hardware/ff563589)释放的内存。

 

 




