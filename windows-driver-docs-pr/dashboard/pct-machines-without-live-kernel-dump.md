---
title: 没有实时内核转储的计算机所占的百分比
description: 该度量将 14 天滑动窗口中的遥测数据聚合为未经历实时内核转储的计算机所占的百分比
ms.topic: article
ms.date: 05/20/2019
ms.localizationpriority: medium
ms.openlocfilehash: 0d02ee5456656e9d39f5c49cb93301f3a9958e4c
ms.sourcegitcommit: b33dff0fc9b5b90ee8bd07f62713c58c5f60b40f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/16/2019
ms.locfileid: "71017016"
---
# <a name="percent-of-machines-without-a-live-kernel-dump"></a>没有实时内核转储的计算机所占的百分比

## <a name="description"></a>描述

实时内核转储 (LKD) 是内核错误的结果，遇到这种情况时，计算机可以恢复而不发生崩溃。 如果用户遇到 LKD，其应用程序可能会挂起或崩溃。 一种常见类型的 LKD 是超时检测和恢复 (TDR)，在此情况下，在驱动程序恢复之前，显卡驱动程序会崩溃，并且显示器会暂时变黑。

## <a name="measure-attributes"></a>度量属性

|属性|值|
|----|----|
|受众 |Standard|
|时间段 |14 天滑动窗口|
|度量标准 |计算机的聚合|
|最小总体数量 |100 台计算机|
|通过标准 |>= 90% 的计算机未遇到 LKD|
|度量 ID |19888731|

## <a name="calculation"></a>计算

1. 该度量将 14 天滑动窗口中的遥测数据聚合为未经历 LKD 的计算机所占的百分比 
2. 没有 LKD 的计算机数 = 计数（安装了驱动程序且没有 LKD 的计算机数） 
3. 计算机总数 = 计数（已成功安装驱动程序的计算机数） 

### <a name="final-calculation"></a>最终计算

没有 LKD 的计算机的百分比 = 没有 LKD 的计算机数/计算机总数 
