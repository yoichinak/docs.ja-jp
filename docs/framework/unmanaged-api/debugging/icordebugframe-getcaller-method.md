---
title: ICorDebugFrame::GetCaller メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetCaller
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetCaller
helpviewer_keywords:
- GetCaller method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetCaller method [.NET Framework debugging]
ms.assetid: bfdc946b-8238-4eb9-8a85-884049fb0fd4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 82902e6a395fe62464065ccea4cca5b52c960f0d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988814"
---
# <a name="icordebugframegetcaller-method"></a>ICorDebugFrame::GetCaller メソッド
このフレームと呼ばれる現在のチェーンで ICorDebugFrame オブジェクトへのポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetCaller (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `ppFrame`  
 [out]アドレスへのポインター、`ICorDebugFrame`呼び出し元のフレームを表すオブジェクト。 この値が呼び出されたフレームが現在のチェーン内の最も外側のフレームの場合は null です。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
