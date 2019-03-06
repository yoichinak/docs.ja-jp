---
title: ICorDebugProcess::IsTransitionStub メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.IsTransitionStub
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::IsTransitionStub
helpviewer_keywords:
- ICorDebugProcess::IsTransitionStub method [.NET Framework debugging]
- IsTransitionStub method [.NET Framework debugging]
ms.assetid: f7653317-7e48-4163-be03-f50f1a4b0f70
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 18084cb69d2c620fc892cc05e5a561e8fda3bc1c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57488189"
---
# <a name="icordebugprocessistransitionstub-method"></a>ICorDebugProcess::IsTransitionStub メソッド
マネージ コードへの遷移を発生させるスタブ内にアドレスがあるかどうかを示す値を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT IsTransitionStub(  
    [in]  CORDB_ADDRESS address,  
    [out] BOOL *pbTransitionStub);  
```  
  
## <a name="parameters"></a>パラメーター  
 `address`  
 [in]A`CORDB_ADDRESS`対象アドレスを指定する値。  
  
 `pbTransitionStub`  
 [out]ブール値へのポインター`true`場合、マネージ コードへの遷移を発生させるスタブ内で指定されたアドレスは、それ以外の場合 *`pbTransitionStub`は`false`。  
  
## <a name="remarks"></a>Remarks  
 `IsTransitionStub`をマネージ ステッパをステップ実行の制御を返すタイミングを決定するアンマネージ ステップ実行のコードでメソッドを使用できます。  
  
 こともできます identity 遷移スタブ ポータブル実行可能 (PE) ファイルに情報を参照しています。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
