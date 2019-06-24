---
title: 使用 Winsock 内核函数与事件回调函数
description: 使用 Winsock 内核函数与
ms.assetid: 63a3f933-f74a-4cb8-a7a9-9498e1c17afa
keywords:
- 网络、 Winsock 内核 WDK 函数
- 网络、 WSK WDK 函数
- 网络、 Winsock 内核 WDK 事件
- WSK WDK 网络、 事件
- 事件 WDK Winsock 内核
- WDK Winsock 内核函数
- 事件回调函数 WDK Winsock 内核
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 2362f1c9194a4a55442a6d65a007ea8056e32249
ms.sourcegitcommit: 0cc5051945559a242d941a6f2799d161d8eba2a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63368916"
---
# <a name="using-winsock-kernel-functions-vs-event-callback-functions"></a>使用 Winsock 内核函数与事件回调函数


对于某些套接字操作 Winsock Kernel (WSK) 应用程序可以调用一个套接字的 WSK 函数以执行该操作或实现以及使 WSK 子系统调用时在套接字上一个事件的回调函数[事件](winsock-kernel-events.md)与操作关联时发生。 例如，在接收时面向连接的套接字上的数据，WSK 应用程序可以使对套接字的调用[ **WskReceive** ](https://msdn.microsoft.com/library/windows/hardware/ff571139)函数，或实现并启用[ *WskReceiveEvent* ](https://msdn.microsoft.com/library/windows/hardware/ff571140)套接字上的事件的回调函数。 WSK 应用程序的要求规定应用程序应使用哪种方法。 整个 WSK 文档提供了有关如何使用这两种方法的示例。

以下列表汇总了每种方法的一些要点。

### <a name="using-winsock-kernel-functions"></a>使用 Winsock 内核函数

-   WSK 应用程序驱动器发生套接字操作时，这意味着 WSK 应用程序控制的套接字操作。 这可能会简化 WSK 应用程序所需的同步。

-   WSK 应用程序提供 Irp 到套接字函数。 这些 Irp 进行排队 WSK 子系统，直到在套接字操作完成。 有关 Irp 用于 WSK 函数的详细信息，请参阅[Winsock 内核函数使用 Irp](using-irps-with-winsock-kernel-functions.md)。

-   WSK 应用程序可以通过为每个操作 IRP，要完成 WSK 子系统正在等待执行阻塞套接字操作。

-   WSK 应用程序可能需要在某些情况下保留多个套接字操作排入队列，以确保高性能上的数据传输的面向连接的套接字，以阻止传入的数据报数据报套接字上拖放或防止正在删除在侦听套接字上的传入连接。

-   WSK 应用程序提供的数据传输操作的数据缓冲区。 这将减少的数据可能需要复制的次数。 但是，如果 WSK 应用程序都保留多个数据传输操作排入队列，应用程序必须提供到每个队列的数据传输操作的 WSK 子系统的数据缓冲区。 因此，WSK 应用程序可能需要更多的内存资源。

### <a name="using-event-callback-functions"></a>使用事件的回调函数

-   WSK 子系统驱动器套接字操作，这意味着 WSK 子系统通过调用回调函数的套接字的事件通知 WSK 应用程序的套接字的事件。 WSK 应用程序可能需要更复杂的同步来处理事件的回调函数的异步特性。

-   WSK 应用程序不使用 Irp 的套接字操作。

-   WSK 应用程序不需要向队列套接字操作。 WSK 子系统调用 WSK 应用程序的事件就立即出现套接字的事件时，此回调函数。 如果 WSK 应用程序可承受速率套接字的事件回调函数调用，使用事件的回调函数可以提供最高的性能和最低的删除数据报或传入的连接的可能性。

-   WSK 子系统提供数据传输操作的数据的缓冲区。 WSK 应用程序必须释放回 WSK 子系统这些数据缓冲区立即或在合理的时间，以便 WSK 子系统不会用尽内存资源。 因此，WSK 应用程序可能需要将数据复制到其自己的数据缓冲区的 WSK 子系统所拥有的数据缓冲区中。

**请注意**  上述列表并不一定详尽。 可能有其他选择哪种方法是特定 WSK 应用程序的最佳选择时要考虑的点。

 

 

 




