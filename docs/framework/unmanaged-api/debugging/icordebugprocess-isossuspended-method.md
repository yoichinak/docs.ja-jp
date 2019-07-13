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
ms.openlocfilehash: 275f62c8211f71f067d310dd4b3af2ddb11e93d7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755462"
---
# <a name="icordebugprocessisossuspended-method"></a>ICorDebugProcess::IsOSSuspended メソッド
このプロセスを停止するデバッガーの結果として、指定したスレッドが中断されたかどうかを示す値を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
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
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
