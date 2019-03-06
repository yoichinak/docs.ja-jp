---
title: ICorDebugChain::GetActiveFrame メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetActiveFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetActiveFrame
helpviewer_keywords:
- ICorDebugChain::GetActiveFrame method [.NET Framework debugging]
- GetActiveFrame method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 36887017-670b-4f21-b406-8fab956f84a3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c14b48a29993a65a0a0ab9fcb63bcb1e0d882042
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494072"
---
# <a name="icordebugchaingetactiveframe-method"></a>ICorDebugChain::GetActiveFrame メソッド
アクティブなを取得します (つまり、最新) チェーン上のフレーム。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `ppFrame`  
 [out]アクティブなを表す ICorDebugFrame オブジェクトのアドレスへのポインター (つまり、最新) チェーン上のフレーム。  
  
## <a name="remarks"></a>Remarks  
 マネージ スタック フレームが使用できない場合`ppFrame`設定を null にします。  
  
 アクティブなフレームを使用できない場合、呼び出しが成功し、`ppFrame`は null になります。 アクティブなフレーム チェーン CHAIN_ENTER_UNMANAGED、により開始されると CHAIN_CLASS_INIT により開始されたいくつかのチェーンで利用できるされません。 CorDebugChainReason 列挙型を参照してください。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
