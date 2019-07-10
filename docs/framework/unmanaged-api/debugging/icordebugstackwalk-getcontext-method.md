---
title: ICorDebugStackWalk::GetContext メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.GetContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::GetContext
helpviewer_keywords:
- GetContext method, ICorDebugStackWalk interface [.NET Framework debugging]
- ICorDebugStackWalk::GetContext method [.NET Framework debugging]
ms.assetid: 081d1c95-152b-4797-8552-18453eb7b14b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f453e950a79b0f929ec8f813cc13eb2e01ab8c87
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760926"
---
# <a name="icordebugstackwalkgetcontext-method"></a>ICorDebugStackWalk::GetContext メソッド
現在のフレームのコンテキストを返します、 [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetContext([in]  ULONG32 contextFlags,  
                   [in]  ULONG32 contextBufSize,  
                   [out] ULONG32* contextSize,  
                   [out, size_is(contextBufSize)] BYTE contextBuf[]);  
```  
  
## <a name="parameters"></a>パラメーター  
 `contextFlags`  
 [in]要求された (WinNT.h で定義されている) コンテキスト バッファーの内容を示すフラグです。  
  
 `contextBufSize`  
 [in]コンテキスト バッファーの割り当てサイズ。  
  
 `contextSize`  
 [out]コンテキストの実際のサイズ。 この値は、コンテキスト バッファーのサイズ以下である必要があります。  
  
 `contextBuf`  
 [out]コンテキストのバッファー。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|現在のフレームのコンテキストが正常に返されました。|  
|E_FAIL|コンテキストは返されませんでした。|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT BUFFER)|コンテキスト バッファーが小さすぎます。|  
|CORDBG_E_PAST_END_OF_STACK|フレーム ポインターがスタックの末尾に達してそのため、追加のフレームにはアクセスできません。|  
  
## <a name="exceptions"></a>例外  
  
## <a name="remarks"></a>Remarks  
 アンワインド非 volatile レジスタなどのレジスタのサブセットのみが復元されるため、コンテキストの呼び出しの時点でレジスタの状態が一致も一致しないです。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
