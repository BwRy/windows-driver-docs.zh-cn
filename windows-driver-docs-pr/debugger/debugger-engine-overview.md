---
title: 调试器引擎概述
description: 调试器引擎概述
ms.assetid: e3cd8a1d-dd07-480b-bc3b-4f6acc647167
keywords:
- 调试器引擎
- 调试器引擎概述
ms.date: 05/23/2017
ms.localizationpriority: medium
ms.openlocfilehash: 092f1fad8cc839e4727b0c6f53c8c29b3b0039b7
ms.sourcegitcommit: 0cc5051945559a242d941a6f2799d161d8eba2a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63368125"
---
# <a name="debugger-engine-overview"></a>调试器引擎概述


*调试器引擎*(DbgEng.dll)，通常称为*引擎*，用于检查和操作中的调试目标提供一个接口*用户模式下*和*内核模式*Microsoft Windows 上。

调试器引擎可以获取目标，设置[断点](multiprocessor-syntax.md#breakpoints)，监视器[事件](events.md#events)，查询[符号](symbols.md#symbols)、 读取和写入到内存和控制[线程](controlling-threads-and-processes.md#threads)并[进程](controlling-threads-and-processes.md#processes)目标中。

调试器引擎可用于编写调试器扩展库和独立应用程序。 此类应用程序嘿 *调试器引擎应用程序*。 使用调试器引擎的完整功能的调试器引擎应用程序称为*调试器*。 例如，WinDbg、 CDB、 NTSD 和 KD 是调试器;调试器引擎提供了其功能的核心。

**引擎概念：**

[调试会话和执行模型](debugging-session-and-execution-model.md)

[客户端对象](client-objects.md)

[输入和输出](input-and-output.md)

**检查和操作的目标：**

[目标](targets.md)

[事件](events.md)

[断点](breakpoints3.md)

[符号](symbols.md)

[内存](memory.md)

[线程和进程](threads-and-processes.md)

### <a name="span-idincompletedocumentationspanspan-idincompletedocumentationspanincomplete-documentation"></a><span id="incomplete_documentation"></span><span id="INCOMPLETE_DOCUMENTATION"></span>不完整的文档

这是初步的文档，当前不完整。

对于许多概念与调试程序和调试器引擎相关，本文未尚未提供，请查看[调试技术](debugging-techniques.md)此文档的部分。

若要获取的某些调试器引擎 API 的当前未记录的功能，请使用[ **Execute** ](https://msdn.microsoft.com/library/windows/hardware/ff543208)方法以执行单个调试器命令。

 

 




