---
title: APN 示例
description: APN 示例
ms.assetid: 3cf74bc4-a334-4213-8138-ebfc91b459e8
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 5fe9c2f55cbfe34f28b2948efc393bb28c1582d8
ms.sourcegitcommit: 0cc5051945559a242d941a6f2799d161d8eba2a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63351291"
---
# <a name="apn-example"></a>APN 示例


下面的 XML 文档使用[APN XML 架构](apn-xml-schema.md)来指定服务的 APN 信息：

``` syntax
<?xml version="1.0" encoding="utf-8"?>
<OperatorList 
  <Operator name="Contoso">
    <HardwareIdList>
      <HardwareId id="MBAE:0:XSDR^EREDER^F">
      </HardwareId>
    </HardwareIdList>
    <ConnectionInfoList>
      <ConnectionInfo AccessString="ContosoAPN" Username="user" Password="pass" FriendlyName="Prepaid Contoso Mobile Broadband" Internet="Y" Purchase="N" AutoConnectOrder="1"/>
    </ConnectionInfoList>
  </Operator>
</OperatorList>
```

 

 





