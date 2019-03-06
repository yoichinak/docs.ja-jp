---
title: ICorDebugEval2::NewParameterizedObjectNoConstructor メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedObjectNoConstructor
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedObjectNoConstructor
helpviewer_keywords:
- NewParameterizedObjectNoConstructor method [.NET Framework debugging]
- ICorDebugEval2::NewParameterizedObjectNoConstructor method [.NET Framework debugging]
ms.assetid: f15b5b78-94f4-4eb9-b3b3-a621272f357c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6feef7b1e1f09107cd2a57555df07bebec86effa
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466984"
---
# <a name="icordebugeval2newparameterizedobjectnoconstructor-method"></a>ICorDebugEval2::NewParameterizedObjectNoConstructor メソッド
コンス トラクター メソッドを呼び出さずに、指定したクラスの新しい型のパラメーター化されたオブジェクトをインスタンス化します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT NewParameterizedObjectNoConstructor (  
    [in] ICorDebugClass        *pClass,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[]  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pClass`  
 [in]ICorDebugClass を表すオブジェクトをインスタンス化されるオブジェクトのクラスへのポインター。  
  
 `nTypeArgs`  
 [in]型引数の数が渡されます。  
  
 `ppTypeArgs`  
 [in]ICorDebugType を表すオブジェクトをインスタンス化されているオブジェクトの型引数が指す各ポインターの配列。  
  
## <a name="remarks"></a>Remarks  
 `NewParameterizedObjectNoConstructor`メソッドには、型引数の数が正しくない場合は失敗または間違った型の引数の型が渡されます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
