---
title: ICorDebugMutableDataTarget::ContinueStatusChanged メソッド
ms.date: 03/30/2017
ms.assetid: 5a66d3f4-dd16-4d62-9dcc-0eab7041d894
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f9d182dbf7371dfdb572b7ab989eb90288b2006a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492557"
---
# <a name="icordebugmutabledatatargetcontinuestatuschanged-method"></a>ICorDebugMutableDataTarget::ContinueStatusChanged メソッド
指定されたスレッド上の未処理のデバッグ イベントの継続状態を変更します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ContinueStatusChanged(  
   [in] DWORD dwThreadId,  
   [in] CORDB_CONTINUE_STATUS continueStatus);  
```  
  
## <a name="parameters"></a>パラメーター  
 `dwThreadId`  
 オペレーティング システム定義のスレッド識別子です。  
  
 `continueStatus`  
 新たに要求された継続状態を表す [COREDB_CONTINUE_STATUS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) 値。  
  
## <a name="remarks"></a>Remarks  
 デバッガーは、通常の方法とは異なることがある方法で現在のデバッグ イベントを処理するように要求する ICorDebug メソッドを呼び出すときに、`ContinueStatusChanged` メソッドを呼び出します。 たとえば、未処理の例外が発生して、デバッガーが例外をキャンセルする操作 ([ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) または `FuncEval` など) を要求する場合、この API は例外のキャンセルを要求するために使用されます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [ICorDebugMutableDataTarget インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
