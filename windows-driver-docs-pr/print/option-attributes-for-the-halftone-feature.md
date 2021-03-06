---
title: 半色调功能的选项属性
description: 半色调功能的选项属性
ms.assetid: a188908a-ddf7-4b4d-a46d-e3550ffb0418
keywords:
- 半色调功能
ms.date: 04/20/2017
ms.localizationpriority: medium
ms.openlocfilehash: 3d6a6f3813cfa045061ac9be072fd9a25ad6210c
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72843054"
---
# <a name="option-attributes-for-the-halftone-feature"></a>半色调功能的选项属性





下表列出了与半色调功能相关的属性。 有关半色调功能的详细信息，请参阅[标准功能](standard-features.md)。

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>属性名称</th>
<th>Attribute 参数</th>
<th>备注</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em><strong>HTCallbackID</strong></p></td>
<td><p>传递给呈现插件的<a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/prcomoem/nf-prcomoem-iprintoemuni-halftonepattern" data-raw-source="[&lt;strong&gt;IPrintOemUni::HalftonePattern&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/prcomoem/nf-prcomoem-iprintoemuni-halftonepattern)"><strong>IPrintOemUni：： HalftonePattern</strong></a>方法的正数值作为其<em>dwCallbackID</em>参数。</p></td>
<td><p>如果提供了<strong>IPrintOemUni：： HalftonePattern</strong>方法，则为必需。 请参阅<a href="halftoning-with-unidrv.md" data-raw-source="[Halftoning with Unidrv](halftoning-with-unidrv.md)">Unidrv 的半色调</a>。</p></td>
</tr>
<tr class="even">
<td><p></em><strong>HTNumPatterns</strong></p></td>
<td><p>表示所提供的半色调模式数的数值。</p>
<p>请参阅<a href="halftoning-with-unidrv.md" data-raw-source="[Halftoning with Unidrv](halftoning-with-unidrv.md)">Unidrv 的半色调</a>。</p></td>
<td><p>可选。 可以是1或3，其中3表示按顺序为红色、绿色和蓝色分别采用不同的模式。 如果未指定，则默认值为1。 可以与 <em><strong>rcHTPatternID</strong>或 *<strong>HTCallbackID</strong>一起使用。</p></td>
</tr>
<tr class="odd">
<td><p></em><strong>HTPatternSize</strong></p></td>
<td><p>表示 <em><strong>rcHTPatternID</strong>指定模式的宽度和高度（以像素为单位<a href="pairs.md" data-raw-source="[Pair](pairs.md)">）的数字</a>值。</p></td>
<td><p>如果指定 *<strong>rcHTPatternID</strong> ，则是必需的。 最大模式大小为成对（256，256）。 将存储的宽度和高度相乘的宽度和高度必须可被4整除为 Dword。</p></td>
</tr>
<tr class="even">
<td><p></em><strong>rcHTPatternID</strong></p></td>
<td><p>表示半色调模式数据的 RC_HTPATTERN 资源的资源标识符。</p></td>
<td><p>如果资源 DLL 中提供了半色调模式，则是必需的。 请参阅<a href="halftoning-with-unidrv.md" data-raw-source="[Halftoning with Unidrv](halftoning-with-unidrv.md)">Unidrv 的半色调</a>。</p></td>
</tr>
</tbody>
</table>

 

有关示例，请参阅[示例 GPD 文件](sample-gpd-files.md)。

有关使用这些属性的详细信息，请参阅[使用 Unidrv 的半色调](halftoning-with-unidrv.md)。 这些属性不与[微型驱动程序提供的半色调](minidriver-supplied-halftoning.md)一起使用。

 

 




