---
title: 演示如何初始化设备属性的代码示例
description: 演示如何初始化设备属性的代码示例
ms.assetid: ec25fa77-13d8-4cb0-913c-b24010355702
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 99f59aba3a32ce7b3b080331c7a64941a41dc9a8
ms.sourcegitcommit: 0cc5051945559a242d941a6f2799d161d8eba2a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63373176"
---
# <a name="code-example-for-initializing-device-properties"></a>演示如何初始化设备属性的代码示例


期间[ **IWiaMiniDrv::drvInitItemProperties** ](https://msdn.microsoft.com/library/windows/hardware/ff544989)根项，微型驱动程序的调用必须初始化该设备描述的以下 WIA 属性：

[**WIA\_DPS\_SERVICE\_ID**](https://msdn.microsoft.com/library/windows/hardware/ff551428)

[**WIA\_DPS\_DEVICE\_ID**](https://msdn.microsoft.com/library/windows/hardware/ff551374)

[**WIA\_DPS\_GLOBAL\_标识**](https://msdn.microsoft.com/library/windows/hardware/ff551395)

[**WIA\_DPA\_FIRMWARE\_VERSION**](https://msdn.microsoft.com/library/windows/hardware/ff550309)

下面的代码示例演示如何初始化 WIA\_DPS\_服务\_通过使用 ID **OpenProperyStore**并**ReadDeviceProperty**方法来读取主键\_PNPX\_ServiceId。 可以使用相同的常规方法来初始化每个设备的属性。

```cpp
HRESULT hr = S_OK;
IPropertyStore *pPropertyStore = NULL;
BSTR bstrPropertyValue = NULL;

//
// Open the current Property Store and keep it opened until all needed properties are read
//
if (SUCCEEDED(hr))
{
    hr = OpenPropertyStore(&pPropertyStore);
    if (FAILED(hr))
    {
        WIAS_ERROR((g_hInst, "Failed to open the Property Store for the current Function Instance, hr = 0x%08X", hr));
    }
}

//
// Initialize WIA_DPS_SERVICE_ID
//
if (SUCCEEDED(hr))
{
    hr = ReadDeviceProperty(pPropertyStore, &PKEY_PNPX_ServiceId, &bstrPropertyValue);
    if (FAILED(hr))
    {
        WIAS_ERROR((g_hInst, "Failed to read the PKEY_PNPX_ServiceId device property, hr = 0x%08X", hr));
    }

    if ((SUCCEEDED(hr)) && (bstrPropertyValue)) 
    {
        WIAS_TRACE((g_hInst, "Service id: %ws", (LPWSTR)bstrPropertyValue));
 
        hr = AddProperty(WIA_DPS_SERVICE_ID, WIA_DPS_SERVICE_ID_STR, RN, bstrPropertyValue);
        if (FAILED(hr)) 
        {
            WIAS_ERROR((g_hInst, "Failed to add WIA_DPS_SERVICE_ID property to the property manager, hr = 0x%08X", hr));
        }
    }

    if (bstrPropertyValue)
    {
        SysFreeString(bstrPropertyValue);
        bstrPropertyValue = NULL;
    }
}

//
// Repeat the same procedure for WIA_DPS_DEVICE_ID, WIA_DPS_GLOBAL_IDENTITY, and WIA_DPS_FIRMWARE_VERSION
//

//
// Close the Property Store
//
if (pPropertyStore)
{
    pPropertyStore->Release();
    pPropertyStore = NULL;
}
```

 

 



