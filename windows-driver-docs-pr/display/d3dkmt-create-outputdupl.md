---
title: D3DKMT\_创建\_OUTPUTDUPL 结构
description: 保留供系统使用。 不要在您的驱动程序中使用。
ms.assetid: 3fdbf129-331d-4dd5-a417-79c88b7e7947
keywords:
- D3DKMT_CREATE_OUTPUTDUPL 结构显示设备
topic_type:
- apiref
api_name:
- D3DKMT_CREATE_OUTPUTDUPL
api_location:
- D3dkmthk.h
api_type:
- HeaderDef
ms.date: 01/05/2018
ms.localizationpriority: medium
ms.openlocfilehash: 58fcae3dd7aaa378688ea55fa177eeb3b66d1522
ms.sourcegitcommit: 0cc5051945559a242d941a6f2799d161d8eba2a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63382954"
---
# <a name="d3dkmtcreateoutputdupl-structure"></a>D3DKMT\_创建\_OUTPUTDUPL 结构


保留供系统使用。 不要在您的驱动程序中使用。

<a name="syntax"></a>语法
------

```ManagedCPlusPlus
typedef struct _D3DKMT_CREATE_OUTPUTDUPL {
  D3DKMT_HANDLE                  hAdapter;
  D3DDDI_VIDEO_PRESENT_SOURCE_ID VidPnSourceId;
  D3DKMT_HANDLE                  hSharedSurfaceGlobal;
  D3DKMT_HANDLE                  hGPUFencefaceGlobal;
  D3DKMT_HANDLE                  hKeyedMutexGlobal;
} D3DKMT_CREATE_OUTPUTDUPL;
```

<a name="members"></a>成员
-------

**hAdapter**

**VidPnSourceId**

**hSharedSurfaceGlobal**

**hGPUFencefaceGlobal**

**hKeyedMutexGlobal**

<a name="requirements"></a>要求
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>最低受支持的客户端</p></td>
<td align="left"><p>Windows 8</p></td>
</tr>
<tr class="even">
<td align="left"><p>最低受支持的服务器</p></td>
<td align="left"><p>Windows Server 2012</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Header</p></td>
<td align="left">D3dkmthk.h （包括 D3dkmthk.h）</td>
</tr>
</tbody>
</table>

 

 





