---
title: ICorDebugClass::GetStaticFieldValue メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugClass.GetStaticFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass::GetStaticFieldValue
helpviewer_keywords:
- GetStaticFieldValue method, ICorDebugClass interface [.NET Framework debugging]
- ICorDebugClass::GetStaticFieldValue method [.NET Framework debugging]
ms.assetid: 56e718b4-fabd-418b-a5b3-3cc33c745683
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6b67f5ec233679461f61715d7562b47c2a195fb8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61750852"
---
# <a name="icordebugclassgetstaticfieldvalue-method"></a>ICorDebugClass::GetStaticFieldValue メソッド
指定された静的フィールドの値を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef         fieldDef,  
    [in]  ICorDebugFrame     *pFrame,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `fieldDef`  
 [in]フィールド`Def`トークンを取得するフィールドを参照します。  
  
 `pFrame`  
 [in]スレッド、コンテキスト、またはアプリケーション ドメインの静的変数の間であいまいさを解消するために使用するフレームを表す ICorDebugFrame オブジェクトへのポインター。  
  
 静的フィールドが、スレッド、コンテキスト、またはアプリケーション ドメインを基準にある場合は、フレームは、適切な値を決定します。  
  
 `ppValue`  
 [out]静的フィールドの値を表す ICorDebugValue オブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>Remarks  
 パラメーター化された型は、静的フィールドの値は特定のインスタンス化します。 そのため、クラス コンス トラクターが型のパラメーターを受け取る場合<xref:System.Type>、呼び出す[icordebugtype::getstaticfieldvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md)の代わりに`ICorDebugClass::GetStaticFieldValue`します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
