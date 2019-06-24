---
title: 添加组件
description: 添加组件
ms.assetid: f8177904-77a2-4d1a-8c72-0b47a100bc37
keywords:
- 通知对象 WDK 网络添加组件
- 网络通知对象 WDK，添加组件
- 添加网络组件
- 网络的组件添加 WDK
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: e9fc5f79e9a754f0b1e0e68f6345c1addb5a4037
ms.sourcegitcommit: 0cc5051945559a242d941a6f2799d161d8eba2a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63367857"
---
# <a name="adding-a-component"></a>添加组件





子系统添加网络组件时，网络配置子系统可以通知的通知对象。 初始化后通知对象，该子系统调用通知对象的[ **INetCfgComponentNotifyGlobal::GetSupportedNotifications** ](https://msdn.microsoft.com/library/windows/hardware/ff547734)方法来检索通知所需的类型对象。 如果通知对象指定它需要通知，添加网络组件时，该子系统调用通知对象的[ **INetCfgComponentNotifyGlobal::SysNotifyComponent** ](https://msdn.microsoft.com/library/windows/hardware/ff547736)方法，并传递 NCN\_添加通知通知对象子系统安装网络组件。 如果该通知对象所属的组件应绑定到指定的组件，通知对象应执行操作，以便绑定。 例如，下面的代码演示如何通知对象可以为指定的组件绑定其组件，如果指定的组件是必需的物理网卡。

```cpp
HRESULT CSample::SysNotifyComponent(DWORD dwChangeFlag,
        INetCfgComponent* pnccItem)
{
    HRESULT hr = S_OK;
    INetCfgComponentBindings *pncfgcompbind;
    // Retrieve bindings for the notify object's component (m_pncc)
    hr = m_pncc->QueryInterface(IID_INetCfgComponentBindings, 
                                (LPVOID*)&pncfgcompbind);
    // Determine if notification is about adding a component
    if (SUCCEEDED(hr) && (NCN_ADD & dwChangeFlag)) {
        // Retrieve the characteristics of the added component
        DWORD dwcc;
        hr = pnccItem->GetCharacteristics(&dwcc);
        // Determine if the added component is a physical adapter
        if (SUCCEEDED(hr) && (dwcc & NCF_PHYSICAL)) {
            // Determine the component's ID
            LPWSTR pszwInfId;
            hr = pnccItem->GetId(&pszwInfId);
            if (SUCCEEDED(hr)) {
                // Compare the component's ID to the required ID
                // and if they are the same perform the binding.
                static const TCHAR c_szCompId[] = TEXT("BINDTO_NIC");
                if (!_tcsicmp(pszwInfId, c_szCompId)) {
                    hr = pncfgcompbind->BindTo(pnccItem);
                }
            }
        }
    }
    return hr;
}
```

 

 




