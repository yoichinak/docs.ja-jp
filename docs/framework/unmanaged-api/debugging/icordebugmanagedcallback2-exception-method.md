---
title: ICorDebugManagedCallback2::Exception メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.Exception
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::Exception
helpviewer_keywords:
- ICorDebugManagedCallback2::Exception method [.NET Framework debugging]
- Exception method, ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: 78b0f14f-2fae-4e63-8412-4df119ee8468
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1f776f20f163df91d65509e5dbab31fe9c29a965
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492102"
---
# <a name="icordebugmanagedcallback2exception-method"></a>ICorDebugManagedCallback2::Exception メソッド
例外ハンドラーの検索が開始されたことをデバッガーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Exception (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFrame       *pFrame,  
    [in] ULONG32              nOffset,  
    [in] CorDebugExceptionCallbackType dwEventType,  
    [in] DWORD                dwFlags  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pAppDomain`  
 [in]例外がスローされたスレッドを格納しているアプリケーション ドメインを表す ICorDebugAppDomain オブジェクトへのポインター。  
  
 `pThread`  
 [in]例外がスローされたスレッドを表す ICorDebugThread オブジェクトへのポインター。  
  
 `pFrame`  
 [in]によって決定されたように、フレームを表す ICorDebugFrame オブジェクトへのポインター、`dwEventType`パラメーター。 詳細については、「解説」セクションの表を参照してください。  
  
 `nOffset`  
 [in]によって決定される単位のオフセットを指定する整数、`dwEventType`パラメーター。 詳細については、「解説」セクションの表を参照してください。  
  
 `dwEventType`  
 [in]この例外コールバックの種類を指定する CorDebugExceptionCallbackType 列挙型の値。  
  
 `dwFlags`  
 [in]値、 [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md)例外に関する追加情報を指定する列挙体  
  
## <a name="remarks"></a>Remarks  
 `Exception`例外処理プロセスの検索フェーズ中にさまざまな時点でコールバックが呼び出されます。 これは、呼び出すことができますよりも 1 回、例外のアンワインド中に。  
  
 によって参照される ICorDebugThread オブジェクトから処理される例外を取得できる、`pThread`パラメーター。  
  
 特定のフレームとのオフセットによって決定されます、`dwEventType`パラメーターとして次のとおりです。  
  
|`dwEventType` の値|`pFrame` の値|`nOffset` の値|  
|----------------------------|-----------------------|------------------------|  
|DEBUG_EXCEPTION_FIRST_CHANCE|例外をスローしたフレーム。|フレーム内の命令ポインター。|  
|DEBUG_EXCEPTION_USER_FIRST_CHANCE|スローされた例外のポイントに最も近いユーザー コード フレーム。|フレーム内の命令ポインター。|  
|DEBUG_EXCEPTION_CATCH_HANDLER_FOUND|このフレームは、catch ハンドラーが含まれています。|Catch ハンドラーの先頭の Microsoft intermediate language (MSIL) オフセット。|  
|DEBUG_EXCEPTION_UNHANDLED|NULL|定義されていません。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [ICorDebugManagedCallback2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
