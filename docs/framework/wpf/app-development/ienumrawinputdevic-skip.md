---
title: IEnumRAWINPUTDEVIC:Skip
ms.date: 03/30/2017
helpviewer_keywords:
- Skip method [WPF]
ms.assetid: c967b0f8-1c6a-459c-8c16-d4f08918ab65
ms.openlocfilehash: f7d7df77c54d4551025aa5a344c96083c263f455
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57467169"
---
# <a name="ienumrawinputdevicskip"></a>IEnumRAWINPUTDEVIC:Skip
列挙子は、[次へ] をスキップするように指示します`celt`列挙体の要素に、[次へ] を呼び出せるように[IEnumRAWINPUTDEVIC:Next](ienumrawinputdevic-next.md)それらの要素は返されません。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Skip( [in] ULONG celt);  
```  
  
## <a name="parameters"></a>パラメーター  
 `celt`  
  
 [in]スキップする要素の数。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 HRESULT:指定された要素の数は場合は S_OK `celt`;それ以外の場合は S_FALSE。
