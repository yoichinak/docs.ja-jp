---
title: ICorDebugStackWalk::GetFrame メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.GetFrame Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::GetFrame
helpviewer_keywords:
- GetFrame method [.NET Framework debugging]
- ICorDebugStackWalk::GetFrame method [.NET Framework debugging]
ms.assetid: 4083b505-5b59-44fb-8c5d-129db6a96c10
topic_type:
- apiref
ms.openlocfilehash: 77210edfdc954f38ff06bc43a8b41a6abe8dc3d6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131839"
---
# <a name="icordebugstackwalkgetframe-method"></a>ICorDebugStackWalk::GetFrame メソッド
テキスト[オブジェクトの現在のフレーム](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetFrame([out] ICorDebugFrame ** pFrame);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pFrame`  
 からスタック内の現在のフレームを表す、作成されたフレームオブジェクトのアドレスへのポインター。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|ランタイムは、現在のフレームを正常に返しました。|  
|E_FAIL|現在のフレームは返されませんでした。|  
|S_FALSE|現在のフレームはネイティブスタックフレームです。|  
|E_INVALIDARG|`pFrame` が null です。|  
|CORDBG_E_PAST_END_OF_STACK|フレームポインターは既にスタックの末尾にあります。そのため、追加のフレームにアクセスすることはできません。|  
  
## <a name="exceptions"></a>例外  
  
## <a name="remarks"></a>Remarks  
 `ICorDebugStackWalk` は実際のスタックフレームだけを返します。 内部フレームを返すには、 [ICorDebugThread3:: GetActiveInternalFrames](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md)メソッドを使用します。 内部フレームは、一時データを格納するためにランタイムによってスタックにプッシュされるデータ構造です。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugStackWalk インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
