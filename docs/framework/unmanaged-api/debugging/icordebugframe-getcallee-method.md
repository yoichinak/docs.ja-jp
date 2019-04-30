---
title: ICorDebugFrame::GetCallee メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetCallee
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetCallee
helpviewer_keywords:
- ICorDebugFrame::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 92d8136d-0436-4c7e-a6b2-80765f892a0d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a179b68e2196eeadc712ae8f7d023b2943533335
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995853"
---
# <a name="icordebugframegetcallee-method"></a>ICorDebugFrame::GetCallee メソッド
このフレームと呼ばれる現在のチェーンで ICorDebugFrame オブジェクトへのポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetCallee (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `ppFrame`  
 [out]アドレスへのポインター、`ICorDebugFrame`呼び出されたフレームを表すオブジェクト。 この値は、呼び出し元のフレームが現在のチェーン内の最も内側のフレームである場合は null です。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
