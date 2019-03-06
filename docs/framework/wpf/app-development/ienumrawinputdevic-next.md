---
title: IEnumRAWINPUTDEVIC:Next
ms.date: 03/30/2017
helpviewer_keywords:
- Next method [WPF]
ms.assetid: 3698b44d-510e-4d18-b32b-85f17188ee26
ms.openlocfilehash: 05867af48b64cd1898b13fa055859c8cc0367c8c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494182"
---
# <a name="ienumrawinputdevicnext"></a>IEnumRAWINPUTDEVIC:Next
次の列挙`celt` [RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice)構造体、列挙子の一覧で、それらを返す`rgelt`で列挙された要素の実際の数とともに`pceltFetched`します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Next(  
      [in] ULONG celt,  
      [out, size_is(celt), length_is(*pceltFetched)] RAWINPUTDEVICE *rgelt,  
      [out] ULONG *pceltFetched);  
```  
  
## <a name="parameters"></a>パラメーター  
 `celt`  
  
 [in]数[RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice)構造体で返される`rgelt`します。  
  
 `rgelt`  
  
 [out] 列挙された RAWINPUTDEVICE 構造体を受け取る size celt (またはそれ以上) の配列。  
  
 `pceltFetched`  
  
 [out] `rgelt` に実際に指定された要素の数へのポインター。 `rgelt` が 1 の場合、呼び出し元は `NULL` に渡すことができます。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 HRESULT:指定された要素の数は場合は S_OK `celt`;それ以外の場合は S_FALSE。
