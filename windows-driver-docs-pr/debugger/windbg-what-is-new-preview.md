---
title: WinDbg 预览版 - 新增功能
description: 本主题提供有关 WinDbg 预览调试器的新增 inofmration。
ms.date: 04/04/2019
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-devices
ms.localizationpriority: medium
ms.openlocfilehash: ff41adbef91d70e3a9c6952cc381148512c8f210
ms.sourcegitcommit: 944535d8e00393531f6b265317a64da3567e4f2c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/06/2019
ms.locfileid: "65106411"
---
# <a name="windbg-preview---whats-new"></a>WinDbg 预览版 - 新增功能

本主题提供在 WinDbg 预览调试器中新增的信息。

## <a name="10190418001"></a>1.0.1904.18001

**修复了 SymSetDiaSession 错误**-我们已将报告一个错误，导致在某些情况下启动的 WinDbg 预览版的一段时间。 有几个外部应用程序尝试之前将其加载到我们的进程注入 DbgHelp 的版本。 其中一些与缺少的功能，这会导致此错误，当我们尝试使用这些功能时使用 DbgHelp 版本。 我们已为此添加修补程序，仍有其中发生的情况下将跟踪。

**字体控件**-我们添加了用于控制字体和字体大小设置。 有两个不同的设置，一个用于文本窗口 (mono 夹角 windows 反汇编、 源、 命令和等)，一个用于工具窗口 （局部变量、 堆栈等）。 仍然是我们将在将来更新这些选项，不会影响的几个方面。

**突出显示改进**-持久的突出显示命令窗口将中的文本现在还在源和说明窗口中的突出显示文本。

**源加载改进**-我们已将更改如何加载源文件的工作原理。 以前在打开源文件时，如运行其他命令的引擎操作不是可能或不可预测。 我们已更改加载发生以启用提高了并行度和更可靠的源打开操作取消。

其他的更改和 bug 修复：
* 添加到源窗口的上下文菜单中"转到反汇编"。
* 添加一个复选框以在反汇编窗口中的"沿用当前指令"。
* 修复了导致命令窗口中执行慢输出大量文本时的 bug。
* 更改过的页面向上和向下箭头键来执行类似于 Visual Studio 的页。
* 当在源窗口中打开 ASM 文件它现在将具有基本注释、 字符串和指令突出显示


## <a name="10181212001"></a>1.0.1812.12001

此版本包含这些更新。

**调试器数据模型C++标头**-新增了一个C++标头，DbgModel.h，用于扩展调试程序数据的 Windows SDK 的一部分包含模型通过C++。 你可以找到详细信息中的[调试程序数据模型C++概述](https://docs.microsoft.com/windows-hardware/drivers/debugger/data-model-cpp-overview)。 此版本包括将一些更多的"API style"功能添加到可以访问通过 dx 命令、 JavaScript 和新 DbgModel.h 标头的调试程序数据模型的新扩展。 此扩展扩展数据模型以包括通过，程序集和代码来执行有关的知识[Debugger.Utility.Code](https://docs.microsoft.com/windows-hardware/drivers/debugger/dbgmodel-namespace-code)命名空间，并通过本地文件系统[Debugger.Utility.FileSystem命名空间](https://docs.microsoft.com/windows-hardware/drivers/debugger/dbgmodel-namespace-file-system)。

**综合类型扩展**使用此新的 API 扩展，我们的新样本上有 GitHub 存储库此处- https://github.com/Microsoft/WinDbg-Samples/tree/master/SyntheticTypes。 此 JavaScript 扩展读取基本 C 头文件，并定义结构和联合标头中定义的综合类型信息。 Dx 命令中，通过内存可查看结构化如同具有包含这些类型的类型信息的 PDB。

其他的更改和 bug 修复：

- 现在的详细信息以智能方式处理使 WinDbg 预览版将源窗口或前台时单步执行反汇编窗口。
- 重新排列 WinDbgNext 的窗口标题开始时具有更重要的信息时内核调试。
- 在命令窗口中交替的背景对比应略有更明显。

## <a name="1018102001"></a>1.0.1810.2001 

此版本包含这些更新。

- 从文件菜单或在主页功能区访问的新设置对话框。 
- 事件和异常设置对话框。 此菜单更改调试器如何处理事件和异常、 sx 命令或 WinDbg 的事件筛选器对话框的等效项。 选择**设置**在主功能区，然后，单击"事件和异常"管理那些在左侧。
- 改进了性能更佳 TTD 索引器。 这会增加 TTD 跟踪文件 （之间 x-10 2x) 更快地进行索引进程，同时进行多较小 （50%左右较小) 的索引文件编制索引的性能。 在计算机使用多个 CPU 内核 （8 +） 时，性能改进是最为明显超过 4 GB 的大小，或跟踪的。 新索引器，使更切合实际调试非常大的跟踪 （50 GB +）。
- 新*debugArch*启动标记用于指定体系结构。 WinDbg 预览尝试启动调试器引擎并更好地支持调试托管的代码的目标的正确位数。 一些的情况，它无法确定正确的位数或您可能想要覆盖它决定。 使用-debugArch x86 | amd64 来控制调试器引擎的体系结构。

其他的更改和 bug 修复：

-  修复了 bug 会导致黑色长条显示在浮动窗口中打开一个全屏调试器。
-  修复了 bug 会导致符号选项无意中清除。
-  现在，启动从最新的目标时，将保留命令历史记录。
-  在数据模型窗口中，您现在可以编辑值。
-  未索引 TTD 跟踪现在将更清晰，它们是不编入索引。
-  改进了局部变量窗口的性能
-  添加用于将命令窗口日志保存到文件的功能区按钮。
-  添加。 SelectMany (<projection>) 到默认的 LINQ 方法集。

## <a name="10180711002"></a>1.0.1807.11002 

此版本包含这些更新。

**自动保存和加载的断点**。 这是将工作区的第一步。 我们正在向该路由下通过启用保存和加载的断点。 启动在调试之前从文件菜单的"最近使用的项目"选项卡的内容将立即加载断点从该会话。 该计划是要展开此功能以在会话之间保留的详细信息。 硬件断点 (ba) 和断点上的其他各种属性，如线程和进程特定上下文，以及条件不当前正在保存。
 
次要更改和 bug 修补程序：

- 添加了命令行选项-x、-xe-xd，-xn，和用于控制处理的异常和事件 xi。 这些命令行选项的行为就像其命令副部分一样。
- 说明窗口现在支持粗体、 下划线和斜体格式设置。
- 修复了某些缩放和滚动问题。
- 在命令、 内存、 源或反汇编窗口中选择文本现在将显示浅色突出显示对所选文本的其他实例。
- 修复了 bug 的中断符号加载会导致符号加载失败的会话的其余部分。
- NatVis 在重新启动一个会话下将现在重新正确加载。

## <a name="10180517002"></a>1.0.1805.17002

此版本包含这些更新。

**新的反汇编窗口**-反汇编窗口现在包括：
- 向上或向下滚动将连续加载更多的反汇编，只要有可能。
- 语法突出显示的数字、 代码地址和操作码。
- 单击代码符号将跳到该位置的反汇编窗口。
- 将鼠标悬停数字将显示工具提示，可将该数字转换为其他基数。
- 表示一个函数的开头的标头。

**更快的源窗口**-源窗口已更新，以更快和更多资源有效。

细微的更改和 bug 修复

- 修复了围绕符号缓存问题
- 修复了某些情况下，如果目标不中断切换初始中断，没有可用
- 如果达到选项卡中无任何可用操作的命令窗口，游标将现在处于输入字段
- WinDbgNext 将立即自动检测位数打开 CAB 文件时

## <a name="10180418003"></a>1.0.1804.18003

此版本包含这些更新。

**符号状态和取消改进**-有时间，调试器显示*忙*加载符号和它很难确定正在进行的工作及其原因，而无需 ！ 符号干扰性启用。 我们已更新 WinDbg 预览，具有一些更好的沟通围绕它的作用时加载的符号以帮助排查任何问题。
除了轻松地看到到底发生了什么，我们做出了一些更改，应取消符号更可靠的品牌和日志窗口中将包含一些通常具有输出时的详细信息 ！ 启用符号干扰。 如果达到视图-> 的日志将获得完整干扰符号加载输出，而无需将其打开并尝试重新加载符号。

**实验性说明窗口**-WinDbg 预览版现在具有一个窗口，以记录。 只需点击查看->"说明"以将其打开。 如果要复制/粘贴到其中，DML 链接将保留，并仍起作用就像它是在命令窗口。 您还可以保存并从"注释"功能区加载说明文件，当窗口处于打开状态。 

**实验性更快的源窗口**-若要帮助提高的 WinDbg 预览性能那里我们实验性新源发挥更有效的窗口。 还有一些缺口周围上下文菜单和语法突出显示，但我们想要为每个人在完成向我们提供早期反馈之前试用的选项。 运行 $UseFastSourceWindow 若要使用它。 如果你想要回到旧密码，运行 $UseMonacoSourceWindow。 该设置将保留在会话之间，将需要关闭并重新打开源窗口，以获取最新版本。

**JSProvider API 版本 1.2** -用于声明对 API 版本 1.2 的支持的 JavaScript 扩展：

- 退出该脚本的.compareTo 方法具有的任何对象上将具有自定义比较运算符 (比较运算符可以处理 DX 计算器中和其他位置： 例如：IModelObject::Compare)
- 退出该脚本的.equals 方法具有的任何对象上将具有自定义相等运算符 (= = 和 ！ = 将工作 DX 计算器和其他位置中： 例如：IModelObject::IsEqualTo)
- 输入脚本的本机磁盘或数据模型对象上的允许访问的任何自定义比较运算符或自定义等同性实现将有.compareTo 和.equals。
 
次要更改和 bug 修补程序：

- 短名称的前后的域问题时，.server 现在将列出以方便使用的完全限定的域名。
- Ctrl + G 现在可在源窗口中。
- 反汇编窗口为添加的地址栏。
- WinDbg 预览版现在将更多预期的方式处理 _NT_SYMBOL_PATH。
- 已添加-server 命令行选项。
- TTD 数据模型查询可以现在显示以渐进方式，因此如果你中断该操作仍将看到一些结果。 此功能是仍实验和可选。 运行`dx @$cursession.TTD.AsyncQueryEnabled = 1`来启用它。
- 分发点命令现在具有到它引用的源文件的链接。

## <a name="11801190010"></a>1.1801.19001.0

此版本包含这些更新。

**文本突出显示**-现在可以突出显示所选文本直接在调试器中的所有实例。 若要使用此功能，只需在命令窗口中选择一些文本然后单击"突出显示"命令功能区中或按 CTRL + ALT + H。 使用其中一个已突出显示的文本上将删除突出显示。

如果想要使用的命令，可以使用"$hl"命令：

`$hl ["someValueHere"]` -突出显示为文本 （或取消突出显示如果尚未突出显示）

`$hl clearAll` -清除所有突出显示的条目

`$hl caseSensitive [1|0]` 集突出显示匹配的区分大小写或不区分大小写 （默认为不区分大小写）

此版本还包括一些小的 bug 修复。


## <a name="11712150030"></a>1.1712.15003.0

此版本包含这些更新。

**TTD 内存查询**-内存访问类似于如何查询调用今天，现在可以查询 TTD。 这可以用来查找所有的读取、 写入和执行访问特定范围的内存。

读取和写入的示例： `dx @$cursession.TTD.Memory(startAddress, endAddress, "rw")`

唯一执行示例： `dx @$cursession.TTD.Memory(startAddress, endAddress, "ec")`

**设置更改**-WinDbg 预览版现在会自动保存会话，包括你的符号路径和源路径之间的设置。

**JavaScript 改进**

- 64 位数字和 JavaScript 中的数字现在包含取模方法允许，则返回 true 64 位取模运算。
- 在 JavaScript 中定义的对象可以使用标准的 dx 现在实现一个自定义比较或是可以相等的概念，将起作用C++运算符或 LINQ 操作中。 若要使用此功能，该脚本必须声明 initializeScript 数组中，它支持新版本的宿主 API 的方法是插入记录"新 host.apiVersionSupport （1，2）"。 完成该操作后可以使用任何 dx 或数据模型窗口 LINQ 查询中的这些函数。 如果该方法实现.compareTo(other)，它是可比较 （比较运算符适用 dx 和 LINQ 中）。 如果该方法返回一个负值，如"这 < 其他"。 如果该方法将返回 0，"这 = = 其他"。 如果该方法返回一个正值"这 > 其他"。 如果该方法实现.equals(other)，它就是可以相等 （= = dx 和 LINQ 中的工作原理）。 该方法必须返回 true 或 false。

次要更改和 bug 修补程序：

- 修复了 bug，其中堆栈和局部变量窗口无法正常运行期间启动调试
- 更新 LM 更准确地报告 ProductVersion 和类似字段的输出
- 在 TTD 会话过程中启用"出后单步"按钮
- 添加了的对-lsrcpath
- 在向下滚动时，局部变量、 观看和模型现在 windows 中的标头不会消失
- ALT + tab 键回 WinDbg 预览，当命令窗口将正确保留光标所在的位置
- 添加用于切换详细模式下的 CTRL + ALT + V 快捷方式
- 右键单击命令窗口选项卡并选择"关闭自动滚动"可以立即禁用自动滚动的命令窗口
- 现在可以调试子进程通过可执行文件启动高级页。


## <a name="10140"></a>1.0.14.0

此版本包含这些更新。

**改进了进程服务器体验**-连接到新的通知文件菜单中显示哪些进程服务器并添加与交互。 根据这些更改，结束调试会话时，进程服务器连接将保持不变，并可以在文件菜单中断开连接。

**查看功能区中的新预设的布局选项**-新的"布局"选项"视图"功能区中。 目前有三种布局： 默认值，一个侧重于反汇编，，最少一个。 

**时间旅行调试功能区**-有增强时间旅行，功能区是按时间顺序查看调试跟踪在调试时显示。

**元数据从 JavaScript 脚本**-JavaScript 扩展现在可以返回的属性和其他构造元数据。 这意味着该扩展可以提供帮助字符串，指示值，和的详细信息的显示基数。 通过将元数据描述符放上通过对 host.metadata.defineMetadata 的显式调用存在 Symbol.metadataDescriptor 对象提供元数据。 函数返回时，循环访问的值和其他值上下文可以返回其值的元数据通过 host.metadata.valueWithMetadata。

**JavaScript API 更新**的一些可能对 JavaScript 提供程序 （包括新的投影的方法和本机对象的属性） 内的 Api 进行了源级别的重大更改。 现有的扩展不会看到任何潜在的重大更改而不需要指示它们支持 JsProvider API 的新版本。 通过使用一个声明的支持版本 1.1 initializeScript 返回的数组中放入 host.apiVersionSupport 记录指示支持新的 API 版本。 也许？ .. 使用一个值，该值对于 1.1 版的支持。

API 版本 1.1 中的更改包括：

- host.getModuleSymbol 和 host.getModuleType 返回; 如果找不到符号而不是引发异常。
- 所有的本机对象除了.targetLocation 上有地址属性。 如果该对象不具有一个地址，在访问该属性时，将引发异常。
- 所有的本机对象来访问与 JavaScript 置于该对象的名称可能会发生冲突的对象上的属性上有新的.getObjectValue 和.setObjectValue 方法 (例如: address)。

**其他 JavaScript 更改**

- JavaScript 扩展现在可以添加和删除通过 Object.defineProperty 和 delete 运算符的数据模型对象的属性。 添加或注册一个 JavaScript 类的父模型或类型签名仍操作对象模型的强首选的方法。
- JavaScript 扩展现在可以修改新 host.setModuleSymbol API 通过调试目标中的模块中的全局变量。
- 数学函数，它们是 64 位库类型上的所有 (例如：.add，.subtract、.multiply、.divide，等等) 现在均存在于 JavaScript 的数字。
- JavaScript 函数和属性现在可以返回值，这些通过自定义封送处理的枚举值。 函数或属性访问器可以返回 host.typeSystem.marshalAs 值 (类型...） 以向此类自定义封送处理。
- 脚本调试程序中的断点命令现在可以中断对函数名称和行/列的位置。
- JavaScript 扩展中的类型对象有权访问通过.containingModule 属性及其包含的模块。

次要更改和 bug 修补程序：

- 固定条件的功能区选项卡为不太令人困惑的格式设置。
- 要分析以提高性能更严格的重新工作的 DML。
- 各种修复程序的性能和行为的 CTRL + F。
- 运行之前尝试使用 TTD 未提升的权限时，请添加一条警告。
- 添加用于覆盖自动目标位数检测的选项。
- 它们不能使用 （如"Go"转储文件中) 时，请禁用各种文件菜单和功能区选项。

已知的问题：
- SOS 不起在 x86 上的跟踪。

## <a name="10130"></a>1.0.13.0

此版本添加了时间旅行跟踪。 时间旅行调试，使你可以记录过程中，然后更高版本同时向前和向后对其进行重播。 时间旅行调试 (TTD) 可帮助你调试问题更容易通过让你"后退"到调试器会话，而无需重现此问题，直到找到 bug。 有关详细信息，请参阅[时间旅行调试-概述](time-travel-debugging-overview.md)。

## <a name="10120"></a>1.0.12.0

此版本是 WinDbg Preview 的第一个版本。 有关一般信息在 WinDbg 预览版中提供的功能[调试使用 WinDbg 预览版](debugging-using-windbg-preview.md)。

---
 
## <a name="see-also"></a>请参阅

[调试使用 WinDbg 预览](debugging-using-windbg-preview.md)