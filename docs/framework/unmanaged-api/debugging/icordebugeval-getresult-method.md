---
title: ICorDebugEval::GetResult メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval.GetResult
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::GetResult
helpviewer_keywords:
- ICorDebugEval::GetResult method [.NET Framework debugging]
- GetResult method [.NET Framework debugging]
ms.assetid: 50dbb9af-58a1-41f4-b56d-3da20011884f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b8e7fcb4f44d6bdf6f18c93b1046b549331621a4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57470797"
---
# <a name="icordebugevalgetresult-method"></a>ICorDebugEval::GetResult メソッド
この評価の結果を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetResult (  
    [out] ICorDebugValue    **ppResult  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `ppResult`  
 [out]評価が正常に完了した場合は、この評価の結果を表す ICorDebugValue オブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>Remarks  
 `GetResult`メソッドは、評価の完了後にのみ有効です。  
  
 通常、評価が完了すると`ppResult`結果を指定します。 例外で終了した場合にスローされる例外になります。 新しいオブジェクトの場合、評価は、新しいオブジェクトへの参照になります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
