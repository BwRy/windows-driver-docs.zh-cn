---
title: 创建属性表页
description: 创建属性表页
ms.assetid: 90b1743c-b530-408a-aa30-9ab774166306
keywords:
- 公共属性表用户界面 WDK 打印，创建属性表页面
- CPSUI WDK 打印，创建属性表页面
- 属性表页 WDK 打印，创建
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 32903e345bb331f239907ba26df44fa28e43ca03
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72842850"
---
# <a name="creating-property-sheet-pages"></a>创建属性表页





使用 CPSUI 创建的属性表页由[属性表选项](property-sheet-options.md)组成，其中每个选项表示用户可修改的值。 属性表选项的对话框是使用一组[支持 CPSUI 的窗口控件](cpsui-supported-window-controls.md)创建的，用户可以使用这些控件来修改选项的值。

CPSUI 提供的窗口控件可以在[CPSUI 提供的页和模板](cpsui-supplied-pages-and-templates.md)中显示，也可以与自定义页面一起使用。 有多种[方法可以指定页面](methods-for-specifying-pages.md)，所有这些方法都涉及到调用 CPSUI 的[**ComPropSheet**](https://docs.microsoft.com/windows-hardware/drivers/ddi/compstui/nc-compstui-pfncompropsheet)函数。

为打印机和打印文档创建属性页页面涉及到[使用 CPSUI 和打印机驱动](using-cpsui-with-printer-drivers.md)程序，需要在应用程序、打印后台处理程序、打印机接口 DLL 和 CPSUI 之间进行交互。

 

 




