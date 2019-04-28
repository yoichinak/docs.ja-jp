---
title: ICorDebugProcess::GetThreadContext メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetThreadContext
helpviewer_keywords:
- ICorDebugProcess::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: 5b132ef1-8d4b-4525-89b3-54123596c194
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 28d54becc2d7cd4359c78415f25f579b968cb3f4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775610"
---
# <a name="icordebugprocessgetthreadcontext-method"></a>ICorDebugProcess::GetThreadContext メソッド
このプロセスで特定のスレッドのコンテキストを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
## <a name="parameters"></a>パラメーター  
 `threadID`  
 [in]コンテキストを取得する対象のスレッドの ID。  
  
 `contextSize`  
 [in] `context` 配列のサイズ。  
  
 `context`  
 [入力、出力]スレッドのコンテキストを表すバイトの配列。  
  
 コンテキストには、スレッドが実行されているプロセッサのアーキテクチャを指定します。  
  
## <a name="remarks"></a>Remarks  
 デバッガーは、Win32 ではなく、このメソッドを呼び出す必要があります`GetThreadContext`メソッド、スレッドは、「ハイジャック」をそのコンテキストが一時的に変更された状態で実際にできるためです。 ネイティブ コードでスレッドがある場合にのみ、このメソッドを使用する必要があります。 使用[ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)マネージ コード内のスレッドにします。  
  
 返されるデータは、現在のプラットフォームのコンテキスト構造です。 Win32 と同様に、`GetThreadContext`メソッドを呼び出し元を初期化する必要があります、`context`このメソッドを呼び出す前にパラメーター。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
