---
title: ICorDebugChain::EnumerateFrames メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugChain.EnumerateFrames
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::EnumerateFrames method
helpviewer_keywords:
- EnumerateFrames method [.NET Framework debugging]
- ICorDebugChain::EnumerateFrames method [.NET Framework debugging]
ms.assetid: 9fcefa98-750d-4168-8915-8173a43accf2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7568f8ca3b92ef465ab595348f68895f389d61e4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645319"
---
# <a name="icordebugchainenumerateframes-method"></a>ICorDebugChain::EnumerateFrames メソッド
最新のフレームを開始する、チェーン内のすべてのマネージ スタック フレームを含む列挙子を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT EnumerateFrames (  
    [out] ICorDebugFrameEnum **ppFrames  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `ppFrames`  
 [out]スタック フレームの列挙子である ICorDebugFrameEnum オブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>Remarks  
 チェーンは、スレッドの物理呼び出し履歴を表します。  
  
 `EnumerateFrames`メソッドは、管理対象のチェーンに対してのみ呼び出す必要があります。 デバッグ API では、非管理対象のチェーンに含まれているフレームを取得するメソッドが提供されません。 デバッガーは、この情報を取得するのにその他の手段を使用する必要があります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
