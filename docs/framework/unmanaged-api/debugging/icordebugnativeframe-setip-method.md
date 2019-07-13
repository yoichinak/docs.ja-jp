---
title: ICorDebugNativeFrame::SetIP メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.SetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::SetIP
helpviewer_keywords:
- ICorDebugNativeFrame::SetIP method [.NET Framework debugging]
- SetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 57784a51-c76d-48f8-9392-584d0e1946d9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc442e0bcd8d392041284269e46821e0642d0891
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765882"
---
# <a name="icordebugnativeframesetip-method"></a>ICorDebugNativeFrame::SetIP メソッド
命令ポインターをネイティブ コードで指定されたオフセット位置に設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `nOffset`  
 [in]ネイティブ コード内のオフセット位置。  
  
## <a name="remarks"></a>Remarks  
 呼び出す`SetIP`すぐにすべてのフレームと現在のスレッドのチェーンが無効にします。 デバッガーには、呼び出しの後にフレーム情報が必要がある場合`SetIP`、新しいスタック トレースを実行する必要があります。  
  
 [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)有効な状態でスタック フレームを保持します。 ただし、場合でも、ランタイムがに関する限り、フレームは有効な状態では、まだある可能性があります、初期化されていないローカル変数などの問題。 呼び出し元は、実行中のプログラムの一貫性を保証します。  
  
 64 ビットのプラットフォームでのうち、命令ポインターを移動できません、`catch`または`finally`ブロックします。 場合`SetIP`というはエラーを示す HRESULT を返す、64 ビット プラットフォームで、このような移動するために、します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目
