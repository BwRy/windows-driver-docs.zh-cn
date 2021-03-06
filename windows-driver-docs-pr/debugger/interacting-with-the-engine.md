---
title: 与引擎交互
description: 与引擎交互
ms.assetid: 80f5320f-ed34-4839-a16e-b3ff5d8edbfe
keywords:
- 调试器引擎 API，使用
ms.date: 05/23/2017
ms.localizationpriority: medium
ms.openlocfilehash: c9e78d21cf3656f2b63c468a7c2b96a6f65c4934
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72826390"
---
# <a name="interacting-with-the-engine"></a>与引擎交互


### <a name="span-idcommands_and_expressionsspanspan-idcommands_and_expressionsspancommands-and-expressions"></a><span id="commands_and_expressions"></span><span id="COMMANDS_AND_EXPRESSIONS"></span>命令和表达式

调试器引擎 API 提供执行命令和计算表达式的方法，就像在 WinDbg 的[调试器命令窗口](the-debugger-command-window.md)中键入的那样。 若要执行调试器命令，请使用[**execute**](https://docs.microsoft.com/windows-hardware/drivers/ddi/dbgeng/nf-dbgeng-idebugcontrol3-execute)。 或者，若要执行文件中的所有命令，请使用[**ExecuteCommandFile**](https://docs.microsoft.com/windows-hardware/drivers/ddi/dbgeng/nf-dbgeng-idebugcontrol3-executecommandfile)。

方法[**评估**](https://docs.microsoft.com/windows-hardware/drivers/ddi/dbgeng/nf-dbgeng-idebugcontrol3-evaluate)将使用C++或 MASM 语法来计算表达式。 调试器引擎用来计算表达式的语法（例如，在**计算**方法中）由[**GetExpressionSyntax**](https://docs.microsoft.com/windows-hardware/drivers/ddi/dbgeng/nf-dbgeng-idebugcontrol3-getexpressionsyntax)提供，可以使用[**SetExpressionSyntaxByName**](https://docs.microsoft.com/windows-hardware/drivers/ddi/dbgeng/nf-dbgeng-idebugcontrol3-setexpressionsyntaxbyname)和[**SetExpressionSyntax**](https://docs.microsoft.com/windows-hardware/drivers/ddi/dbgeng/nf-dbgeng-idebugcontrol3-setexpressionsyntax)进行更改。 [**GetNumberExpressionSyntaxes**](https://docs.microsoft.com/windows-hardware/drivers/ddi/dbgeng/nf-dbgeng-idebugcontrol3-getnumberexpressionsyntaxes)将返回由调试器识别的不同语法的数目，并由[**GetExpressionSyntaxNames**](https://docs.microsoft.com/windows-hardware/drivers/ddi/dbgeng/nf-dbgeng-idebugcontrol3-getexpressionsyntaxnames)返回它们的名称。

**计算**返回的值的类型由所计算的字符串中使用的符号和常量决定。 该值包含在[**调试\_值**](https://docs.microsoft.com/windows-hardware/drivers/ddi/dbgeng/ns-dbgeng-_debug_value)结构中，可以使用[**CoerceValue**](https://docs.microsoft.com/windows-hardware/drivers/ddi/dbgeng/nf-dbgeng-idebugcontrol3-coercevalue)和[**CoerceValues**](https://docs.microsoft.com/windows-hardware/drivers/ddi/dbgeng/nf-dbgeng-idebugcontrol3-coercevalues)强制转换为不同的类型。

### <a name="span-idaliasesspanspan-idaliasesspanaliases"></a><span id="aliases"></span><span id="ALIASES"></span>别名

*别名*是在调试器命令和表达式中使用时，将自动替换为其他字符串的字符串。 有关别名的概述，请参阅[使用别名](using-aliases.md)。 调试器引擎具有几类别名。

*固定名称的别名*按编号编制索引，名称 **$u 0**， **$u 1**，...， **$u 9**。 可以使用[**SetTextMacro**](https://docs.microsoft.com/windows-hardware/drivers/ddi/dbgeng/nf-dbgeng-idebugcontrol3-settextmacro)方法设置这些别名的值，并且可以使用[**GetTextMacro**](https://docs.microsoft.com/windows-hardware/drivers/ddi/dbgeng/nf-dbgeng-idebugcontrol3-gettextmacro)方法进行检索。

*自动别名*和*用户命名别名*可以具有任何名称。 自动别名由调试器引擎定义，用户命名的别名由用户通过调试器命令或调试器引擎 API 定义。 若要定义或删除用户命名的别名，请使用[**SetTextReplacement**](https://docs.microsoft.com/windows-hardware/drivers/ddi/dbgeng/nf-dbgeng-idebugcontrol3-settextreplacement)方法。 [**GetTextReplacement**](https://docs.microsoft.com/windows-hardware/drivers/ddi/dbgeng/nf-dbgeng-idebugcontrol3-gettextreplacement)方法返回自动别名或用户命名别名的名称和值。 可以使用[**RemoveTextReplacements**](https://docs.microsoft.com/windows-hardware/drivers/ddi/dbgeng/nf-dbgeng-idebugcontrol3-removetextreplacements)方法删除所有用户命名的别名。 [**GetNumberTextReplacements**](https://docs.microsoft.com/windows-hardware/drivers/ddi/dbgeng/nf-dbgeng-idebugcontrol3-getnumbertextreplacements)方法将返回用户名和自动别名;这可与**GetTextReplacement**一起使用，以循环访问所有这些别名。 [**OutputTextReplacements**](https://docs.microsoft.com/windows-hardware/drivers/ddi/dbgeng/nf-dbgeng-idebugcontrol3-outputtextreplacements)方法将打印所有用户命名别名的列表，包括它们的名称和值。

**请注意**   如果为用户命名的别名指定了与自动别名相同的名称，则用户命名的别名将隐藏自动别名，以便在按名称检索别名的值时，将使用用户命名的别名。

 

### <a name="span-idengine_optionsspanspan-idengine_optionsspanengine-options"></a><span id="engine_options"></span><span id="ENGINE_OPTIONS"></span>引擎选项

引擎提供了很多控制其行为的选项。 [**调试\_ENGOPT\_XXX**](https://docs.microsoft.com/previous-versions/ff541475(v=vs.85))中列出了这些选项。 它们由[**GetEngineOptions**](https://docs.microsoft.com/windows-hardware/drivers/ddi/dbgeng/nf-dbgeng-idebugcontrol3-getengineoptions)返回，可使用[**SetEngineOptions**](https://docs.microsoft.com/windows-hardware/drivers/ddi/dbgeng/nf-dbgeng-idebugcontrol3-setengineoptions)进行设置。 可以使用[**AddEngineOptions**](https://docs.microsoft.com/windows-hardware/drivers/ddi/dbgeng/nf-dbgeng-idebugcontrol3-addengineoptions)设置单独的选项，并使用[**RemoveEngineOptions**](https://docs.microsoft.com/windows-hardware/drivers/ddi/dbgeng/nf-dbgeng-idebugcontrol3-removeengineoptions)进行设置。

### <a name="span-idinterruptsspanspan-idinterruptsspaninterrupts"></a><span id="interrupts"></span><span id="INTERRUPTS"></span>中断

中断是一种强制进入调试器或通知引擎停止处理当前命令的方法，例如，通过在 WinDbg 中按 Ctrl + Break。

若要请求中断调试器或中断调试器的当前任务，请使用[**SetInterrupt**](https://docs.microsoft.com/windows-hardware/drivers/ddi/dbgeng/nf-dbgeng-idebugcontrol3-setinterrupt)。 若要检查是否有中断，请使用[**GetInterrupt**](https://docs.microsoft.com/windows-hardware/drivers/ddi/dbgeng/nf-dbgeng-idebugcontrol3-getinterrupt)。

**请注意**   从调试器扩展进行长时间的任务时，建议在请求中断后定期检查**GetInterrupt**并停止处理。

 

当请求中断调试器时，如果目标需要很长时间才能执行中断，则引擎可能会超时。 如果目标处于无响应状态，或者在资源争用中阻止或延迟中断请求，则可能会发生这种情况。 引擎将等待的时间长度由[**GetInterruptTimeout**](https://docs.microsoft.com/windows-hardware/drivers/ddi/dbgeng/nf-dbgeng-idebugcontrol3-getinterrupttimeout)返回，可使用[**SetInterruptTimeout**](https://docs.microsoft.com/windows-hardware/drivers/ddi/dbgeng/nf-dbgeng-idebugcontrol3-setinterrupttimeout)进行设置。

 

 





