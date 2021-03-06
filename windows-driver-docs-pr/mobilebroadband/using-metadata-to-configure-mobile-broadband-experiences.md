---
title: 使用元数据来配置移动宽带体验的概述
description: 使用元数据来配置移动宽带体验的概述
ms.assetid: d3ceab6e-550f-4852-8ee0-4a261c238434
ms.date: 07/02/2019
ms.localizationpriority: medium
ms.openlocfilehash: add18828a06b1ff69f394d19cc337edc58abab7d
ms.sourcegitcommit: 6f74454e7ed5e703e4e4b363b6816652950e6a51
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2019
ms.locfileid: "67608554"
---
# <a name="overview-of-using-metadata-to-configure-mobile-broadband-experiences"></a>使用元数据来配置移动宽带体验的概述

> [!IMPORTANT] 
> 从 Windows 10，版本 1703，开始 APN 数据库将替换为新格式称为 COSA。 Windows 8、 Windows 8.1 和 Windows 10 1703年将继续使用 APN 数据库存在时 Windows 10 之前的版本，版本 1703年及更高版本使用 COSA。 有关 COSA 详细信息，请参阅[COSA 概述](cosa-overview.md)。
>
> 从 Windows 10，版本 1803，开始 MBAE 应用体验将替换为 uWP 应用的月概述。 MO 概述有关 uWP 应用的详细信息，请参阅[uWP 移动宽带应用程序的概述](uwp-mobile-broadband-apps.md)。

你可以提供元数据以自定义 Windows 8、 Windows 8.1 和 Windows 10 移动宽带的应用程序体验的各个方面。 其中包括使用运算符品牌、 集成的移动宽带应用和 Windows 连接管理器中，提供 Windows APN 数据库的已更新的信息和提供数据来预配 PC 自定义 Windows 连接管理器。 Windows 8、 Windows 8.1 和 Windows 10 包括元数据可以使用三个的来源：

-   **Windows APN 数据库**Windows APN 数据库包含预先预配第一次连接到操作员的网络所需的数据。 数据库是 Windows 8、 Windows 8.1 和 Windows 10 的一部分，并且更新通过 Windows 更新的概述。 Windows APN 数据库都始终在 PC 上可用。 COSA 和 APN 数据库的详细信息，请参阅[COSA/APN 数据库](cosa-apn-database.md)。

-   **服务元数据**订阅购买和品牌的运算符所需的信息。 提供此信息作为服务元数据包的一部分。 它是存储在 Windows 元数据和 Internet 服务 (WMIS) 上，下载后移动宽带设备检测到使用任何可用的 Internet 连接。 此元数据可以还预安装到一台 PC 上由 OEM，但必须预安装从 Windows 开发人员中心-硬件的硬件开发人员部分下载的包。 有关服务元数据的详细信息，请参阅[服务元数据](service-metadata.md)。

-   **帐户预配的元数据**订阅购买，包括 Wi-fi 凭据和计划信息后生成的信息。 此元数据由你提供到 Windows 付款验证后，可以通过使用预配刷新机制进行更新。 有关帐户设置元数据的详细信息，请参阅[帐户预配](account-provisioning.md)。

下图显示了不同的元数据源相关的方式和它们提供服务。 服务元数据优先于 Windows APN 数据库中的信息。

![这是移动宽带概述](images/mbae-sxs-overview.jpg)

概述使用在本部分中的链接，若要了解有关不同类型的移动宽带元数据的详细信息：

-   [帐户预配](account-provisioning.md)

-   [COSA/APN 数据库](cosa-apn-database.md)

-   [服务元数据](service-metadata.md)
