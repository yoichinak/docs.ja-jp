---
title: ICorDebugEval::CreateValue メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval.CreateValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::CreateValue
helpviewer_keywords:
- ICorDebugEval::CreateValue method [.NET Framework debugging]
- CreateValue method [.NET Framework debugging]
ms.assetid: 9a1c0b47-6f10-4fcb-844a-4ab2d7990140
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c16f6d1334888fc389a7c39cf0a3865afca2085
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934746"
---
# <a name="icordebugevalcreatevalue-method"></a>ICorDebugEval::CreateValue メソッド
0 または null の初期値を持つ指定した型の値を作成します。  
  
 このメソッドは、.NET Framework version 2.0 で廃止されています。 使用[icordebugeval 2::createvaluefortype](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)代わりにします。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CreateValue (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `elementType`  
 [in]値、 [CorElementType](../../../../docs/framework/unmanaged-api/metadata/corelementtype-enumeration.md)列挙値の型を指定します。  
  
 `pElementClass`  
 [in]ポインター、 [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)型がプリミティブ型でない場合、値のクラスを指定するオブジェクト。  
  
 `ppValue`  
 [out]値を表す"ICorDebugValue"オブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>Remarks  
 `CreateValue` 作成、`ICorDebugValue`の関数の評価で使用する目的で指定された型のオブジェクト。 この値オブジェクトは、ユーザーの定数をパラメーターとして渡すために使用できます。  
  
 その初期値は 0 で、値の型がプリミティブ型の場合は null です。 使用[icordebuggenericvalue::setvalue](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md)プリミティブ型の値を設定します。  
  
 場合の値`elementType`ELEMENT_TYPE_CLASS は、"ICorDebugReferenceValue"を取得する (で返される`ppValue`) null オブジェクト参照を表します。 このオブジェクトを使用して、オブジェクト参照のパラメーターを持つ関数の評価に null を渡すことができます。 設定することはできません、`ICorDebugValue`に何も常に null です。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** 1.1, 1.0  
  
## <a name="see-also"></a>関連項目

- [CreateValueForType メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)
- [ICorDebugEval インターフェイス](icordebugeval-interface.md)
