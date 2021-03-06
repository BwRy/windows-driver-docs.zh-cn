---
title: Bug 检查 0x170 CRYPTO_LIBRARY_INTERNAL_ERROR
description: CRYPTO_LIBRARY_INTERNAL_ERROR bug 检查具有 0x00000170 值。 它指示发生了内部错误中的加密库。
keywords:
- Bug 检查 0x170 CRYPTO_LIBRARY_INTERNAL_ERROR
- CRYPTO_LIBRARY_INTERNAL_ERROR
ms.date: 01/10/2019
topic_type:
- apiref
api_name:
- CRYPTO_LIBRARY_INTERNAL_ERROR
api_type:
- NA
ms.localizationpriority: medium
ms.openlocfilehash: ca19aa7abdebfc5fccba7424dbd6458d48d9d7d6
ms.sourcegitcommit: d03b44343cd32b3653d0471afcdd3d35cb800c0d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2019
ms.locfileid: "67519920"
---
# <a name="bug-check-0x170-cryptolibraryinternalerror"></a>Bug 检查 0x170：CRYPTO\_LIBRARY\_INTERNAL\_ERROR 

CRYPTO\_库\_内部\_错误 bug 检查的值为 0x00000170。 它指示发生了内部错误中的加密库。

> [!IMPORTANT]
> 本主题面向程序员。 如果你已使用计算机时收到一个蓝色的屏幕，错误代码的客户，请参阅[疑难解答蓝屏错误](https://www.windows.com/stopcode)。



 ## <a name="cryptolibraryinternalerror--parameters"></a>CRYPTO\_库\_内部\_错误参数

|参数|描述|
|--- |--- |
|1| 失败的 ID。|
|2| 保留。|
|3| 保留。 |
|4| 保留。 |


## <a name="cause"></a>原因
-----

此检测错误表明加密库命中其中应永远不会发生异常，并且库的信号给调用方错误没有安全方法。  这可能是攻击活动的症状。


## <a name="see-also"></a>请参阅
----------

[Bug 检查代码参考](bug-check-code-reference2.md)

[加密 API:下一代](https://docs.microsoft.com/windows/desktop/SecCNG/cng-portal) 


