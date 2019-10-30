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
ms.openlocfilehash: 95183701987d3ddec3835a17c5d256c25c2c4c64
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132068"
---
# <a name="icordebugtypegetstaticfieldvalue-method"></a>ICorDebugType::GetStaticFieldValue メソッド
指定したスタックフレーム内の指定したフィールドトークンによって参照される静的フィールドの値を格納する、ICorDebugValue オブジェクトへのインターフェイスポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef        fieldDef,  
    [in]  ICorDebugFrame    *pFrame,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `fieldDef`  
 から静的フィールドを指定する `mdFieldDef` トークンです。  
  
 `pFrame`  
 からスタックフレームを表す、テキストフレームへのポインター。  
  
 `ppValue`  
 入出力静的フィールドの値を格納している `ICorDebugValue` のアドレスへのポインター。  
  
## <a name="remarks"></a>Remarks  
 `GetStaticFieldValue` メソッドは、型が ELEMENT_TYPE_CLASS または ELEMENT_TYPE_VALUETYPE の場合にのみ使用できます。この場合、は、[型:: GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)メソッドによって示されます。  
  
 非ジェネリック型の場合、`GetStaticFieldValue` によって実行される操作は、によって返される、は、によって返された、テキスト:: [GetStaticFieldValue](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md)と同じにすることができます、には、[テキスト:: getclass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md)です。  
  
 ジェネリック型の場合、静的フィールド値は特定のインスタンス化に対して相対的になります。 また、静的フィールドがスレッド、コンテキスト、またはアプリケーションドメインに対して相対的である可能性がある場合は、デバッガーが適切な値を決定するためにスタックフレームが役立ちます。  
  
## <a name="remarks"></a>Remarks  
 `GetStaticFieldValue` は、`ICorDebugType::GetType` の呼び出しが ELEMENT_TYPE_CLASS または ELEMENT_TYPE_VALUETYPE の値を返す場合にのみ使用できます。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
