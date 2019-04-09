---
title: ICorDebugStackWalk インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk
helpviewer_keywords:
- ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 16d695e8-975d-431b-8421-e9e6c3e3f476
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e33e9be112a6a10f89b88005496ce2e63dff2d54
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080684"
---
# <a name="icordebugstackwalk-interface"></a>ICorDebugStackWalk インターフェイス
スレッドのスタック上のマネージド メソッド (フレーム) を取得するメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetContext メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md)|現在のフレームのコンテキストを返します、`ICorDebugStackWalk`オブジェクト。|  
|[SetContext メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md)|セット、`ICorDebugStackWalk`オブジェクトの現在のスレッドの有効なコンテキストのコンテキスト。|  
|[Next メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md)|移動、`ICorDebugStackWalk`次のフレームにオブジェクト。|  
|[GetFrame メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getframe-method.md)|内の現在のフレームを取得、`ICorDebugStackWalk`オブジェクト。|  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
