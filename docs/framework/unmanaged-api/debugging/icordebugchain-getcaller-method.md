---
title: ICorDebugChain::GetCaller メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetCaller
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetCaller
helpviewer_keywords:
- ICorDebugChain::GetCaller method [.NET Framework debugging]
- GetCaller method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: d0b8ab4b-d7d2-4fa0-945f-3d2b87e7e991
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fd65de77209f5a981c0a4c291f8573a61cf6335b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645280"
---
# <a name="icordebugchaingetcaller-method"></a>ICorDebugChain::GetCaller メソッド
このチェーンと呼ばれるチェーンを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetCaller (  
    [out] ICorDebugChain      **ppChain  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `ppChain`  
 [out]呼び出し元のチェーンを表す ICorDebugChain オブジェクトのアドレスへのポインター。  
  
 このチェーンが自発的に呼び出された場合 (このチェーンやデバッガーに呼び出し履歴が初期化されている場合、ケースになります) として、`ppChain`は null になります。  
  
## <a name="remarks"></a>Remarks  
 呼び出しがスレッド間でマーシャ リングされた場合、別のスレッドで呼び出しチェーンがあります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
