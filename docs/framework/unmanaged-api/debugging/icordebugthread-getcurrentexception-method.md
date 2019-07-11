---
title: ICorDebugThread::GetCurrentException メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetCurrentException
helpviewer_keywords:
- ICorDebugThread::GetCurrentException method [.NET Framework debugging]
- GetCurrentException method [.NET Framework debugging]
ms.assetid: 331ed465-a195-4359-8584-b82c6098b29b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a6d53ebfebb8c883065ce119c2338a2225f0472
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762482"
---
# <a name="icordebugthreadgetcurrentexception-method"></a>ICorDebugThread::GetCurrentException メソッド
マネージ コードによってスローされる例外を表す ICorDebugValue オブジェクトへのインターフェイス ポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetCurrentException (  
    [out] ICorDebugValue **ppExceptionObject  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `ppExceptionObject`  
 [out]アドレスへのポインター、`ICorDebugValue`によってスローされる例外を表すオブジェクトをマネージ コード。  
  
## <a name="remarks"></a>Remarks  
 例外オブジェクトが存在してが終わるまで、例外がスローされたときから、`catch`ブロックします。 ICorDebugEval メソッドによって実行される関数の評価は、セットアップの例外オブジェクトをクリアし、完了時に復元します。  
  
 例外は、(たとえば、フィルターまたは関数の評価で例外がスローされた) 場合、入れ子になんだことができます、単一のスレッドで複数の未処理の例外が発生する可能性があります。 `GetCurrentException` 最新の例外を返します。  
  
 例外オブジェクトと型は、例外の有効期間にわたって変更可能性があります。 たとえば、x の型の例外がスローされた後共通言語ランタイム (CLR) 可能性がありますメモリが不足し、メモリ不足の例外に昇格させることです。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
