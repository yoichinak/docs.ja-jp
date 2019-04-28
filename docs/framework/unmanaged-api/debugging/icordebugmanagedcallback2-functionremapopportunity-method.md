---
title: ICorDebugManagedCallback2::FunctionRemapOpportunity メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.FunctionRemapOpportunity
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::FunctionRemapOpportunity
helpviewer_keywords:
- FunctionRemapOpportunity method [.NET Framework debugging]
- ICorDebugManagedCallback2::FunctionRemapOpportunity method [.NET Framework debugging]
ms.assetid: 0d6471bc-ad9b-4b1d-a307-c10443918863
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 14291ced9a606cc0b2a3792c2157b7bc2a3460a3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756235"
---
# <a name="icordebugmanagedcallback2functionremapopportunity-method"></a>ICorDebugManagedCallback2::FunctionRemapOpportunity メソッド
コードの実行が編集された関数の以前のバージョンでシーケンス ポイントに達したことをデバッガーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT FunctionRemapOpportunity (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pOldFunction,  
    [in] ICorDebugFunction    *pNewFunction,  
    [in] ULONG32              oldILOffset  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pAppDomain`  
 [in]編集された関数を格納しているアプリケーション ドメインを表す ICorDebugAppDomain オブジェクトへのポインター。  
  
 `pThread`  
 [in]リマップ ブレークポイントが発生しました、スレッドを表す ICorDebugThread オブジェクトへのポインター。  
  
 `pOldFunction`  
 [in]現在のスレッドで実行されている関数のバージョンを表す ICorDebugFunction オブジェクトへのポインター。  
  
 `pNewFunction`  
 [in]関数の最新バージョンを表す ICorDebugFunction オブジェクトへのポインター。  
  
 `oldILOffset`  
 [in]命令ポインターの古いバージョンの関数での Microsoft intermediate language (MSIL) オフセット。  
  
## <a name="remarks"></a>Remarks  
 このコールバックは、デバッガーを呼び出すことによって、新しいバージョンの指定された関数内の正しい場所に、命令ポインターを再マップする営業案件、 [icordebugilframe 2::remapfunction](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md)メソッド。 デバッガーが要求されていない場合`RemapFunction`呼び出す前に、 [icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)メソッド、ランタイムは、古いコードの実行を継続し、別に起動されます`FunctionRemapOpportunity`次のシーケンス ポイントでコールバックします。  
  
 デバッガーが S_OK を返すまで、以前のバージョンの指定された関数を実行しているすべてのフレームには、このコールバックが呼び出されます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugManagedCallback2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
