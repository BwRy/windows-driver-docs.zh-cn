---
title: 处理事件
description: 处理事件
ms.assetid: 2cd7ccf3-12f5-4ad0-a7c9-a0f437b72445
keywords:
- Stream .sys 类驱动程序 WDK Windows 2000 内核，事件
- 流式处理微型驱动程序 WDK Windows 2000 内核，事件
- 微型驱动程序 WDK Windows 2000 内核流式处理，事件
- 事件 WDK 流式处理微型驱动程序
- 事件集 WDK 流式处理微型驱动程序
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 91151bbacd9f268cd878d12f277bfd487903c47f
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72843356"
---
# <a name="handling-events"></a>处理事件





微型驱动程序可以支持事件集。 同时，整个设备和单个流都可以接收启用或禁用事件的请求。 类驱动程序处理事件 enable 和 disable 请求。 它将每个启用的事件排队，并为每个流和设备提供单独的队列。 如果某个事件处于禁用状态，则该类驱动程序会将其从队列中删除。 请注意，类驱动程序将每个启用的事件排队，无论微型驱动程序是否执行其自己的同步。

微型驱动程序在[**HW\_STREAM\_标头**](https://docs.microsoft.com/windows-hardware/drivers/ddi/strmini/ns-strmini-_hw_stream_header)结构的**DeviceEventsArray**成员中提供它支持的事件集。 每个流都提供它在**StreamEventsArray**中支持的事件集， [ **\_流的\_信息**](https://docs.microsoft.com/windows-hardware/drivers/ddi/strmini/ns-strmini-_hw_stream_information)结构。

微型驱动程序定义了一个通过[**KSEVENT\_集**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ks/ns-ks-ksevent_set)数据结构处理的事件集，该结构依次指向[**KSEVENT\_项**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ks/ns-ks-ksevent_item)结构的数组，事件集中的每个事件各有一个。

如果可接收事件请求，微型驱动程序将为每个可接收事件请求的流提供[*StrMiniEvent*](https://docs.microsoft.com/windows-hardware/drivers/ddi/strmini/nc-strmini-phw_event_routine)回调例程，并为设备本身提供回调。 如果*StrMiniEvent*例程返回的状态代码不是 "成功"，则类驱动程序将不会将事件排队。

当客户端发出事件启用请求时，它会传递[**KSEVENTDATA**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ks/ns-ks-kseventdata)结构，该结构描述事件发生后应如何发出信号，可选择后跟事件特定的参数。 当类驱动程序收到请求时，它会生成一个[**KSEVENT\_条目**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ks/ns-ks-_ksevent_entry)结构，用于描述应如何触发事件。 它将每个事件的 KSEVENT\_条目结构排队。 微型驱动程序可以使用[**StreamClassGetNextEvent**](https://docs.microsoft.com/windows-hardware/drivers/ddi/strmini/nf-strmini-streamclassgetnextevent)例程来检查事件队列。

事件实际发生时，微型驱动程序通过调用[**StreamClassDeviceNotification**](https://docs.microsoft.com/windows-hardware/drivers/ddi/strmini/nf-strmini-streamclassdevicenotification)或[**StreamClassStreamNotification**](https://docs.microsoft.com/windows-hardware/drivers/ddi/strmini/nf-strmini-streamclassstreamnotification)发出信号，指示类驱动程序。 微型驱动程序可以通过几种不同的方式发出事件信号：它可以指示发生了特定事件，或者可以指示发生了特定类型的所有事件。 有关详细信息，请参阅**StreamClassDeviceNotification**或**StreamClassStreamNotification** 。

类驱动程序可以分析[**KSEVENTDATA**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ks/ns-ks-kseventdata)结构，以创建其[**KSEVENT\_条目**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ks/ns-ks-_ksevent_entry)结构，但不能对在原始请求中跟随任何特定于事件的参数执行相同操作。 微型驱动程序可以为特定类型的事件在 KSEVENT\_进入结构之后分配额外的空间，方法是为它用于声明事件的 KSEVENT\_项的**ExtraEntryData**成员提供一个非零值。 为该事件类型调用*StrMiniEvent*时，它应将任何特定于事件的参数从 KSEVENTDATA 存储在此内存中。

 

 




