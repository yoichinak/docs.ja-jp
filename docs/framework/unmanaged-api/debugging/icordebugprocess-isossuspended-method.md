---
title: ICorDebugProcess::IsOSSuspended メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.IsOSSuspended
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::IsOSSuspended
helpviewer_keywords:
- IsOSSuspended method [.NET Framework debugging]
- ICorDebugProcess::IsOSSuspended method [.NET Framework debugging]
ms.assetid: 83406cb2-5797-4402-872d-89c9516aefec
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 039dc0d9befb038e643abc4e2524c133234f460b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775571"
---
# <a name="icordebugprocessisossuspended-method"></a>ICorDebugProcess::IsOSSuspended メソッド
このプロセスを停止するデバッガーの結果として、指定したスレッドが中断されたかどうかを示す値を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT IsOSSuspended(  
    [in]  DWORD threadID,  
    [out] BOOL  *pbSuspended);  
```  
  
## <a name="parameters"></a>パラメーター  
 `threadID`  
 [in]対象のスレッドの ID。  
  
 `pbSuspended`  
 [out]ブール値へのポインター`true`中断されている以外の場合、指定したスレッドがされている場合 *`pbSuspended`は`false`します。  
  
## <a name="remarks"></a>Remarks  
 指定したスレッドの Win32 中断回数でデバッガーがこのプロセスの停止の結果として、指定されたスレッドが中断されたときに 1 ずつインクリメントされます。 デバッガー ユーザー インターフェイス (UI) が、オペレーティング システムに表示される場合は、アカウントには、この情報を取得する可能性があります (OS) がユーザーに、スレッドの数を中断します。  
  
 `IsOSSuspended`メソッドがアンマネージ デバッグのコンテキストでのみ意味します。 マネージ デバッグ中のスレッドは協調的中断なく OS 中断です。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
