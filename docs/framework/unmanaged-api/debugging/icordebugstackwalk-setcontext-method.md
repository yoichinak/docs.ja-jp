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
ms.openlocfilehash: 90156152a2c133446dedbe22426785ab63f8dfb9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131812"
---
# <a name="icordebugstackwalksetcontext-method"></a>ICorDebugStackWalk::SetContext メソッド
[オブジェクトの現在のコンテキスト](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)をスレッドの有効なコンテキストに設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetContext([in] CorDebugSetContextFlag flag,  
                   [in] ULONG32 contextSize,  
                   [in, size_is(contextSize)] BYTE context[]);  
```  
  
## <a name="parameters"></a>パラメーター  
 `flag`  
 からコンテキストがスタックのアクティブなフレームからのものであるか、またはスタックのアンワインドによって取得されたコンテキストであるかを示す[Cordebugsetcontextflag](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md)フラグ。  
  
 `contextSize`  
 から`CONTEXT` バッファーに割り当てられたサイズ。  
  
 `context`  
 から`CONTEXT` バッファー。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`ICorDebugStackWalk` オブジェクトのコンテキストが正常に設定されました。|  
|E_FAIL|`ICorDebugStackWalk` オブジェクトのコンテキストが設定されませんでした。|  
|E_INVALIDARG|コンテキストが null です。|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|コンテキストバッファーが小さすぎます。|  
  
## <a name="exceptions"></a>例外  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、スレッドの現在のコンテキストを変更しません。  
  
 現在のコンテキストを無効なコンテキストに設定すると、スタックウォーカーから予期しない結果が発生する可能性があります。  
  
 このコンテキストの完全なビットごとのコピーを取得するには、次のようにして、" [GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) " メソッドを直ちに呼び出します。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
