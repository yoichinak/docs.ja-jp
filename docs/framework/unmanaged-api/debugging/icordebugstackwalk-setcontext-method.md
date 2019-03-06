---
title: ICorDebugStackWalk::SetContext メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.SetContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::SetContext
helpviewer_keywords:
- SetContext method [.NET Framework debugging]
- ICorDebugStackWalk::SetContext method [.NET Framework debugging]
ms.assetid: bac0b156-31a3-4e7f-be4d-ab21789c81f1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3bbd215b2fefc662da4867a0a8700ca130c4e14c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57470193"
---
# <a name="icordebugstackwalksetcontext-method"></a>ICorDebugStackWalk::SetContext メソッド
セット、 [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)オブジェクトの現在のスレッドの有効なコンテキストのコンテキスト。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetContext([in] CorDebugSetContextFlag flag,  
                   [in] ULONG32 contextSize,  
                   [in, size_is(contextSize)] BYTE context[]);  
```  
  
## <a name="parameters"></a>パラメーター  
 `flag`  
 [in]A [CorDebugSetContextFlag](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md)かどうか、コンテキストは、スタックのアクティブなフレームから、またはスタックのアンワインドで取得したコンテキストを示すフラグです。  
  
 `contextSize`  
 [in]割り当てのサイズ、`CONTEXT`バッファー。  
  
 `context`  
 [in]`CONTEXT`バッファー。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`ICorDebugStackWalk`オブジェクトのコンテキストが正常に設定します。|  
|E_FAIL|`ICorDebugStackWalk`オブジェクトのコンテキストが設定されませんでした。|  
|E_INVALIDARG|コンテキストが null です。|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|コンテキスト バッファーが小さすぎます。|  
  
## <a name="exceptions"></a>例外  
  
## <a name="remarks"></a>Remarks  
 このメソッドでは、スレッドの現在のコンテキストは変更されません。  
  
 無効なコンテキストを現在のコンテキストを設定すると、スタック ウォーカーから予期しない結果があります可能性。  
  
 このコンテキストの正確なビットごとのコピーを取得するにはすぐに呼び出すことによって、 [icordebugstackwalk::getcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md)メソッド。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
