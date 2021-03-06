---
title: INF InboxVersionRequired 指令
description: INF InboxVersionRequired 指令
ms.assetid: 75a07ca7-d279-4815-b644-10b58753f885
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: bc6c21a886d3d7f4c7a1e0c037bde1278ed7c9b5
ms.sourcegitcommit: fb7d95c7a5d47860918cd3602efdd33b69dcf2da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2019
ms.locfileid: "67372378"
---
# <a name="inf-inboxversionrequired-directive"></a>INF InboxVersionRequired 指令


有关识别包的驱动程序，可以使用**InboxVersionRequired** INF 指令指定的最小可接受的版本，所有核心驱动程序 INF 引用。 可以使用**UseDriverVer**关键字来指定最低版本。 此最低版本适用于所有被引用的核心驱动程序 INF 中。

下面的示例包的识别驱动程序部分演示如何插入**InboxVersionRequired** INF 指令：

```cpp
[PrinterPackageInstallation.amd64]
PackageAware=TRUE
CoreDriverDependencies={D20EA372-DD35-4950-9ED8-A6335AFE79F0},{D20EA372-DD35-4950-9ED8-A6335AFE79F3}
InboxVersionRequired=UseDriverVer
```

如果**UseDriverVer**的值使用关键字**InboxVersionRequired**， **UseDriverVer**告知类安装程序以使用**DriverVer**从正在分析的任何核心驱动程序可接受的最低版本为 INF 指令版本字符串。 服务使用的驱动程序时必须小心**UseDriverVer**关键字。 INF 引用的所有核心驱动程序必须都为相同或更高版本才能都成功安装。

您还可以指定特定版本字符串的值作为**InboxVersionRequired**。 这些版本字符串遵循相同的格式**DriverVer**中指定的字符串[ **INF 版本部分**](https://docs.microsoft.com/windows-hardware/drivers/install/inf-version-section)。 有关详细信息**DriverVer**的字符串格式，请参阅[ **INF DriverVer 指令**](https://docs.microsoft.com/windows-hardware/drivers/install/inf-driverver-directive)。

下面的示例演示如何设置**InboxVersionRequired**到特定的版本字符串：

```cpp
InboxVersionRequired=09/28/1999,5.00.2136.1
```

 

 




