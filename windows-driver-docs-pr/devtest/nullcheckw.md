---
title: NullCheck 规则 (wdm)
description: NullCheck 规则验证驱动程序代码中的 NULL 值不会取消引用驱动程序中更高版本。
ms.assetid: 840906B2-E6D4-4BC8-AC38-461824B70BFA
ms.date: 05/21/2018
keywords:
- NullCheck 规则 (wdm)
topic_type:
- apiref
api_name:
- NullCheck
api_type:
- NA
ms.localizationpriority: medium
ms.openlocfilehash: 6ef14f728d73ce310d1a569284ec84598fc88c69
ms.sourcegitcommit: f663c383886d87ea762e419963ff427500cc5042
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2019
ms.locfileid: "67392074"
---
# <a name="nullcheck-rule-wdm"></a>NullCheck 规则 (wdm)


NullCheck 规则验证驱动程序代码中的 NULL 值不会取消引用驱动程序中更高版本。 如果其中一项条件为 true，此规则将报告缺陷：

-   没有为 NULL，则取消分配更高版本。
-   一个全局/参数可能为更高版本，取消引用 NULL 的驱动程序中的过程，并且没有显式签入中建议的指针的初始值可能为 NULL 的驱动程序。

与 NullCheck 规则冲突，跟踪树窗格中突出显示最相关的代码语句。 有关使用报表输出的详细信息，请参阅[静态驱动程序验证工具报告](https://docs.microsoft.com/windows-hardware/drivers/devtest/static-driver-verifier-report)并[了解跟踪查看器](https://docs.microsoft.com/windows-hardware/drivers/devtest/understanding-the-defect-viewer)。

**结构示例**

此代码片段演示如何正确使用的结构。

```
//Rule does not fail
typedef struct _B { 
    int *f; 
} B;
void GoodStruc(B *x) {
    B *y = x;
    y->f = NULL; //assign NULL
    if (x->f) {
        *(x->f) = 1;
    } //OK
    
}
```

此代码片段显示了结构错误使用。 该代码将进行编译，但会生成一个运行时错误。

```
//Rule fails
typedef struct _A {
    int *f; 
} A;

void BadStruc(A *x) {
    A *y = x;
    y->f = NULL; //assign NULL
    *(x->f) = 1; //dereferencing NULL
}
```

**函数的示例**

在此示例中，没有可能为 NULL，则取消该函数的参数更高版本。 此外，没有显式签入，建议初始指针的值可能为 NULL。

```
//Rule fails
void Bad(int *x)
{
    *x = 2; //Possibly dereferencing NULL
    if (x != NULL) //checks for null on a parameter
        *x = *x + 1;
}
```

在此示例中，任何规则冲突由于没有可能该参数是隐式不满足前提条件应为 NULL。

```
//Rule does not fail
void Good1(int *x)
{
     *x = 2;
     *x = *x + 1;
}
```

在此第二个示例中，没有显式为 NULL，在每次检查将使用此参数。

```
//Rule does not fail
void Good2(int *x)
{
    if (x != NULL)
        *x = 2; // ok
    if (x != NULL) //checks for null on a parameter
        *x = *x + 1;
}
```

|              |     |
|--------------|-----|
| 驱动程序模型 | WDM |

<a name="how-to-test"></a>如何测试
-----------

<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">在编译时</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>运行<a href="https://docs.microsoft.com/windows-hardware/drivers/devtest/static-driver-verifier" data-raw-source="[Static Driver Verifier](https://docs.microsoft.com/windows-hardware/drivers/devtest/static-driver-verifier)">Static Driver Verifier</a>并指定<strong>NullCheck</strong>规则。</p>
使用以下步骤来分析你的代码：
<ol>
<li><a href="https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers#preparing-your-source-code" data-raw-source="[Prepare your code (use role type declarations).](https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers#preparing-your-source-code)">准备你的代码 （使用角色类型声明）。</a></li>
<li><a href="https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers#running-static-driver-verifier" data-raw-source="[Run Static Driver Verifier.](https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers#running-static-driver-verifier)">运行的 Static Driver Verifier。</a></li>
<li><a href="https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers#viewing-and-analyzing-the-results" data-raw-source="[View and analyze the results.](https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers#viewing-and-analyzing-the-results)">查看和分析结果。</a></li>
</ol>
<p>有关详细信息，请参阅<a href="https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers" data-raw-source="[Using Static Driver Verifier to Find Defects in Drivers](https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers)">以找到缺陷驱动程序中使用 Static Driver Verifier</a>。</p></td>
</tr>
</tbody>
</table>

 

 





