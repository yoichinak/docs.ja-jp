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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ac40927ac9469e4a2fb74fb550287130b9bb9f83
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61989457"
---
# <a name="icordebugchaingetstackrange-method"></a>ICorDebugChain::GetStackRange メソッド
このチェーンの履歴のセグメントのアドレス範囲を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pStart`  
 [out]ポインターを`CORDB_ADDRESS`値が履歴のセグメントの開始アドレスです。  
  
 `pEnd`  
 [out]ポインターを`CORDB_ADDRESS`スタック セグメントの終了アドレスである値。  
  
## <a name="remarks"></a>Remarks  
 数値の範囲は、スタック フレームの場所の比較についてのみ有効です。 実際にスタックに格納されているものを想定することはできません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
