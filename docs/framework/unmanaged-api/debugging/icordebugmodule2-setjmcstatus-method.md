---
title: ICorDebugModule2::SetJMCStatus メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::SetJMCStatus
helpviewer_keywords:
- SetJMCStatus method, ICorDebugModule2 interface [.NET Framework debugging]
- ICorDebugModule2::SetJMCStatus method [.NET Framework debugging]
ms.assetid: 8c6d2089-4dbb-4715-b9e9-2a4491c8c9ce
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d20c640d6a6a43b7bde4c7d46df470c7bc8c5aa2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61942511"
---
# <a name="icordebugmodule2setjmcstatus-method"></a>ICorDebugModule2::SetJMCStatus メソッド
この ICorDebugModule2 を除く、指定された値でのすべてのクラスのすべてのメソッドだけマイ コードのみ (JMC) 状態を設定、`pTokens`配列で、逆の値に設定します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL                        bIsJustMyCode,  
    [in] ULONG32                     cTokens,  
    [in, size_is(cTokens)] mdToken   pTokens[]  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `bIsJustMycode`  
 [in]設定`true`コードは、デバッグ対象以外の場合に場合に、設定`false`します。  
  
 `cTokens`  
 [in] `pTokens` 配列のサイズ。  
  
 `pTokens`  
 [in]配列の`mdToken`値、その JMC ステータスに設定するメソッドを指す各!`bIsJustMycode`します。  
  
## <a name="remarks"></a>Remarks  
 指定されている各メソッドの JMC 状態、`pTokens`の反対に配列が設定されている、`bIsJustMycode`値。 このモジュールで他のすべてのメソッドの状態に設定、`bIsJustMycode`値。  
  
 `SetJMCStatus`メソッドは、このモジュール内のすべての以前 JMC 設定を消去します。  
  
 `SetJMCStatus`メソッドは、すべての関数が正常に設定されている場合に S_OK HRESULT を返します。 いくつかの関数の場合は、CORDBG_E_FUNCTION_NOT_DEBUGGABLE HRESULT がマークされている返します`true`デバッグ可能ではありません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
