---
title: 转换用于即插即用的 Windows NT 4.0 SCSI 微型端口概述
description: 转换用于即插即用的 Windows NT 4.0 SCSI 微型端口概述
ms.assetid: 46e5eb41-ff41-4054-856b-cc32f286e543
keywords:
- SCSI 微型端口驱动程序 WDK 存储，PnP
- PnP WDK SCSI
- 即插即用 WDK SCSI
- 转换 SCSI 微型端口驱动程序
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: d2590249a6f28d2f0ebe2bad129dad4bb88e184c
ms.sourcegitcommit: e1ff1dd43b87dfb7349cebf70ed2878dc8d7c794
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/02/2020
ms.locfileid: "75606555"
---
# <a name="converting-a-windows-nt-40-scsi-miniport-for-plug-and-play-overview"></a>转换用于即插即用的 Windows NT 4.0 SCSI 微型端口概述

即使微型端口驱动程序已在注册表中启用了即插即用，驱动程序在初始化期间也会出错，除非它在使用*HwContext*指针和端口驱动程序提供的资源方面存在某些限制。 如果小型小型驱动程序依赖于驱动程序的可预测初始化顺序，则它可能也会在初始化过程中出错。

若要在即插即用下成功运行，可能需要修改 Microsoft Windows NT 4.0 微型端口驱动程序的源代码，如以下各节所述。
