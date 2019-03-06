---
title: ICorDebugProcess::SetThreadContext メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::SetThreadContext
helpviewer_keywords:
- ICorDebugProcess::SetThreadContext method [.NET Framework debugging]
- SetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: a7b50175-2bf1-40be-8f65-64aec7aa1247
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e281022cd7bc9b2095fdbd3964061b811ef60e0d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496964"
---
# <a name="icordebugprocesssetthreadcontext-method"></a>ICorDebugProcess::SetThreadContext メソッド
このプロセスでは、特定のスレッドのコンテキストを設定します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
## <a name="parameters"></a>パラメーター  
 `threadID`  
 [in]コンテキストを設定する対象のスレッドの ID。  
  
 `contextSize`  
 [in] `context` 配列のサイズ。  
  
 `context`  
 [in]スレッドのコンテキストを表すバイトの配列。  
  
 コンテキストには、スレッドが実行されているプロセッサのアーキテクチャを指定します。  
  
## <a name="remarks"></a>Remarks  
 デバッガーは、Win32 ではなく、このメソッドを呼び出す必要があります`SetThreadContext`関数は、スレッドは、「ハイジャック」をそのコンテキストが一時的に変更された状態で実際にできるためです。 ネイティブ コードでスレッドがある場合にのみ、このメソッドを使用する必要があります。 使用[ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)マネージ コード内のスレッドにします。 帯域外の (OOB) のデバッグ イベント時に、スレッドのコンテキストを変更する必要はありません。  
  
 渡されたデータは、現在のプラットフォームの context 構造体である必要があります。  
  
 このメソッドは、誤って使用すると、ランタイムを破壊できます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
