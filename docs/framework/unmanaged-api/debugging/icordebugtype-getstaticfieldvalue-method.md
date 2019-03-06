---
title: ICorDebugType::GetStaticFieldValue メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetStaticFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetStaticFieldValue
helpviewer_keywords:
- GetStaticFieldValue method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::GetStaticFieldValue method [.NET Framework debugging]
ms.assetid: 62eb5d55-53ee-4fb3-8d47-7b6c96808f9e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c6b86c5ce3cc246af600d9b65d2fe12a0427f9f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485396"
---
# <a name="icordebugtypegetstaticfieldvalue-method"></a>ICorDebugType::GetStaticFieldValue メソッド
指定したスタック フレームでトークンを指定したフィールドによって参照される静的フィールドの値を含む ICorDebugValue オブジェクトにインターフェイス ポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef        fieldDef,  
    [in]  ICorDebugFrame    *pFrame,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `fieldDef`  
 [in]`mdFieldDef`トークンを静的フィールドを指定します。  
  
 `pFrame`  
 [in]スタック フレームを表す、ICorDebugFrame へのポインター。  
  
 `ppValue`  
 [out]アドレスへのポインター、`ICorDebugValue`静的フィールドの値を格納します。  
  
## <a name="remarks"></a>Remarks  
 `GetStaticFieldValue`メソッドは使用できます、型が ELEMENT_TYPE_CLASS または ELEMENT_TYPE_VALUETYPE 場合に、のみで示されている、 [icordebugtype::gettype](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)メソッド。  
  
 非ジェネリック型の場合、操作を実行して`GetStaticFieldValue`を呼び出すことと同じ[icordebugclass::getstaticfieldvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md) ICorDebugClass オブジェクトによって返される[icordebugtype::getclass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md).  
  
 ジェネリック型は、静的フィールドの値は、特定のインスタンス化を基準になります。 また、静的フィールドがスレッド、コンテキスト、またはアプリケーション ドメインを基準とした可能性がある場合は、スタック フレームをデバッガーで適切な値の確認は役立ちます。  
  
## <a name="remarks"></a>Remarks  
 `GetStaticFieldValue` 呼び出す場合にのみ使用できます`ICorDebugType::GetType`ELEMENT_TYPE_CLASS または ELEMENT_TYPE_VALUETYPE の値を返します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
