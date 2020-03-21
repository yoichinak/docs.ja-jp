---
title: ICorDebugChain::GetStackRange メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetStackRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetStackRange
helpviewer_keywords:
- ICorDebugChain::GetStackRange method [.NET Framework debugging]
- GetStackRange method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 554284e7-3f6c-4d40-8da5-1c9317fbd484
topic_type:
- apiref
ms.openlocfilehash: 64e697323377d664b7b1e36bbf5931a44465cc51
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178956"
---
# <a name="icordebugchaingetstackrange-method"></a>ICorDebugChain::GetStackRange メソッド
このチェーンのスタック セグメントのアドレス範囲を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pStart`  
 [アウト]スタック セグメントの`CORDB_ADDRESS`開始アドレスである値へのポインター。  
  
 `pEnd`  
 [アウト]スタック セグメントの`CORDB_ADDRESS`終了アドレスである値へのポインター。  
  
## <a name="remarks"></a>解説  
 数値の範囲は、スタック フレームの位置を比較する場合にのみ意味があります。 実際にスタックに格納されている内容について、何も仮定できません。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
