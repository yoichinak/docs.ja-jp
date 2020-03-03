---
title: IEnumRAWINPUTDEVIC:Skip
ms.date: 03/30/2017
helpviewer_keywords:
- Skip method [WPF]
ms.assetid: c967b0f8-1c6a-459c-8c16-d4f08918ab65
ms.openlocfilehash: a74f71345a22f6d766c2d5966ca5d2cb33ab756e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053376"
---
# <a name="ienumrawinputdevicskip"></a>IEnumRAWINPUTDEVIC:Skip
列挙子に対して、次`celt`に[IEnumRAWINPUTDEVIC: next](ienumrawinputdevic-next.md)を呼び出すときにこれらの要素が返されないように、列挙体の次の要素をスキップするように指示します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Skip( [in] ULONG celt);  
```  
  
## <a name="parameters"></a>パラメーター  
 `celt`  
  
 からスキップする要素の数。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 HRESULT:指定された要素の数が`celt`の場合は S_OK。それ以外の場合は S_FALSE。
