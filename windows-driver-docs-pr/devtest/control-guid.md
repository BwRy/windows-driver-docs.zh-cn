---
title: 控制 GUID
description: 控制 GUID
ms.assetid: a85a5e1a-c4c1-40d4-a0ef-d8e552590f03
keywords:
- 控件 Guid WDK
- Guid WDK 软件跟踪
- 标识符 WDK 软件跟踪
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 9c85ba1f2c4b887260e039ca7bbafe5bfebaa2fd
ms.sourcegitcommit: fb7d95c7a5d47860918cd3602efdd33b69dcf2da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2019
ms.locfileid: "67360377"
---
# <a name="control-guid"></a>控制 GUID

## <span id="ddk_control_guid_tools"></span><span id="DDK_CONTROL_GUID_TOOLS"></span>

每个[跟踪提供程序](trace-provider.md)定义*控制 GUID*用于唯一标识提供程序。 使用此 GUID 来启用或禁用跟踪提供程序通过[事件跟踪 Windows (ETW)](event-tracing-for-windows--etw-.md)。

控件 GUID 随即出现在[WPP\_控制\_GUID](https://docs.microsoft.com/previous-versions/windows/hardware/previsioning-framework/ff556186(v=vs.85))检测的跟踪提供程序的源代码文件中的宏。

```C
#define WPP_CONTROL_GUIDS \
    WPP_DEFINE_CONTROL_GUID(GUIDFriendlyName, (ControlGUID),  \
        WPP_DEFINE_BIT(NameOfTraceFlag1)  \
        WPP_DEFINE_BIT(NameOfTraceFlag2)  \
        .............................   \
        .............................   \
        WPP_DEFINE_BIT(NameOfTraceFlag31) )
```

[Tracepdb](tracepdb.md)创建[跟踪 (MOF) 文件](trace-managed-object-format--mof--file.md)，其中包含控件的 GUID 和 PDB 文件中表示每个跟踪提供程序的跟踪级别。 MOF 文件的名称是跟踪提供程序的模块名称。 如果您使用，Tracepdb 还可能会产生 TMC 文件 **-c**选项。

控件 GUID 标识到 ETW 跟踪提供程序，因为您可以使用控件 GUID 来定义和重新定义的作用域[跟踪提供程序](trace-provider.md)。 例如，多个驱动程序可以通过指定相同的控件的 GUID 是单个跟踪提供程序的一部分。 或者，单个驱动程序可以通过指定不同的控件的 Guid 的每个实例中包含多个跟踪提供程序[WPP\_控制\_GUID](https://docs.microsoft.com/previous-versions/windows/hardware/previsioning-framework/ff556186(v=vs.85))宏。
