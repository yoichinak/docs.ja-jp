---
title: ICorDebugEval2::CreateValueForType メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.CreateValueForType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::CreateValueForType
helpviewer_keywords:
- CreateValueForType method [.NET Framework debugging]
- ICorDebugEval2::CreateValueForType method [.NET Framework debugging]
ms.assetid: ea38ae20-7e0a-427a-be77-d78fae719d82
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b27e40618d6128c21e99745ca45e139a9c21c843
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57475035"
---
# <a name="icordebugeval2createvaluefortype-method"></a>ICorDebugEval2::CreateValueForType メソッド
0 または null の初期値を持つ指定した型の新しい ICorDebugValue へのポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CreateValueForType (  
    [in] ICorDebugType         *pType,  
    [out] ICorDebugValue       **ppValue  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pType`  
 [in]型を表す ICorDebugType オブジェクトへのポインター。  
  
 `ppValue`  
 [out]アドレスへのポインター、`ICorDebugValue`値を表すオブジェクト。  
  
## <a name="remarks"></a>Remarks  
 `CreateValueForType` 一般化[icordebugeval::createvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md)任意のオブジェクトの種類を指定できるためなど構築型など`List<int>`します。 このメソッドの唯一の目的では、関数の評価に渡すことができる値を生成します。  
  
 種類は、クラスまたは値型である必要があります。 このメソッドを使用して、配列の値または文字列値を作成することはできません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
