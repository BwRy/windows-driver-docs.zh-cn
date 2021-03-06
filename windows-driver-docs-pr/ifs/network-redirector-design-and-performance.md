---
title: 网络重定向程序的设计和性能
description: 网络重定向程序的设计和性能
ms.assetid: 60ee4548-f81c-4d10-91ef-0e31e2837268
keywords:
- 网络重定向程序 WDK，性能
- 重定向程序驱动程序 WDK，性能
- 性能 WDK 网络重定向程序
- 运行在线方法 WDK 网络重定向程序
- 带宽 WDK 网络重定向程序
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 8f126c86e0224f9f9f9a3d55089f3a1476a33349
ms.sourcegitcommit: 0cc5051945559a242d941a6f2799d161d8eba2a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63379469"
---
# <a name="network-redirector-design-and-performance"></a>网络重定向程序的设计和性能


## <span id="ddk_network_redirector_design_and_performance_if"></span><span id="DDK_NETWORK_REDIRECTOR_DESIGN_AND_PERFORMANCE_IF"></span>


有两种不同方法实现中网络重定向程序的高性能。 第一个方法强调到网络，最重要的是其他快速入门。 第二种方法会尝试使用先进的技术来最小化网络操作;这些操作通常花费较长时间，并使用向上稀缺网络资源 （例如可用带宽）。 它们是在第一个不成功，开发人员通常将到第二种方法。

时永远不会再短代码路径的优势，"运行到-在线"方法提供更好的性能，仅当系统操作不会遇到一些基本的瓶颈时。 例如，考虑实际传输速率限于 1.25 MB/秒的 10 个兆位以太网网络。 这是比一些磁盘，而是仍比内存访问速度慢得。 出于此原因，提供内存中缓存经常访问的数据的系统将提供更好的性能，在许多情况下，一个不比。 相反，如果在客户端上的网络重定向程序坚持的对尝试缓存在不利的情况下，可能会降低性能。 例如，如果缓存管理器依赖于基于 x86 的硬件页粒度，然后这可能意味着将读取和编写每次启动应用程序的 32 字节写入到响应中完整的 4 KB 的块。 很明显，若要获得最佳性能，网络重定向程序必须实现复杂的缓存管理策略，但必须也是同样已准备好以动态地确定是否使用它们。 并且，如果禁用了缓存，必须准备好以运行适用于网络网络重定向程序。

在 CPU 饱和的服务器的情况下提供了第二个示例。 如果不采取措施来缓解拥塞在服务器上的远程文件系统的性能可能会显著妨碍。 例如，饱和度条件下的服务器可能有更大的可能性为丢弃数据包而不卸载服务器。 客户端网络重定向程序会好好考虑，步伐安排为了缩小丢弃的数据包的概率的方式发送的数据包。 更为可喜的是，重定向程序可能需要尝试合并成单个数据包的多个操作的度量值。 合并操作，以便服务器获取每个数据包的更多操作是在饱和的服务器的情况下一优点。

当系统使用的类型的流量和可能的网络条件不适当的网络模式时，还减少了性能。 经验表明，使用基于数据报的模式和具有更好的性能，对于较小的 I/O 请求之间可能相关。 它是不清除此项改进是功能或是否仅适用于这些情况下，数据报传输的概率非常高。 但可用数据的实现是当然值得除了面向连接的模式下的"无连接"模式。 理想的情况是网络重定向器时会这两种模式可能会受支持的网络协议并可供使用，因此，重定向程序无法动态地选择应执行流量的方式。

最后，如果在操作过程中获取相应的数据可用于做出明智的决策，可能会提高性能。 有许多这在 Windows 中的示例。 例如，缓存管理器保留读取命令的简短历史记录和跟踪缓存命中数和未命中数，用于指导在预读计划决策。 第二个示例可能是在使用"环境信息"为做出决策。 可能有信息可在文件名的共享名称，或从用户或管理员可以极大地提高了性能。 例如，响应，有时可以优化通过只更改缓存大小参数，捕获正在使用的数据文件来提高性能。 此"环境知识"的访问模式的某些情况下可能可用来提供动态更改 （提示） 建议用于提高性能。

 

 




