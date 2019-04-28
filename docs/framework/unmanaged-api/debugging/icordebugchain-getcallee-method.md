---
title: ICorDebugChain::GetCallee メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetCallee
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetCallee method
helpviewer_keywords:
- ICorDebugChain::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 19560c79-abdc-4bdf-a5fe-eb362a59edc0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ed5a7657affde335acf79952d77bbdb7ac42c7a0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645299"
---
# <a name="icordebugchaingetcallee-method"></a>ICorDebugChain::GetCallee メソッド
このチェーンによって呼び出されたチェーンを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetCallee (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `ppChain`  
 [out]呼び出されたチェーンを表す ICorDebugChain オブジェクトのアドレスへのポインター。 場合 (つまり、このチェーンを返すと呼ばれるチェーンが待機していない) 場合、このチェーンは現在実行中、`ppChain`は null になります。  
  
## <a name="remarks"></a>Remarks  
 このチェーンは、呼び出されたチェーンに戻りますが、実行を再開する前に待機します。 スレッド間マーシャ リングされた呼び出しの場合、別のスレッドで呼び出されたチェーンがあります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
