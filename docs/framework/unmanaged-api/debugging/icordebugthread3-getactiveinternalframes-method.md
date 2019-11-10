---
title: ICorDebugThread3::GetActiveInternalFrames メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread3.GetActiveInternalFrames Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3::GetActiveInternalFrames
helpviewer_keywords:
- ICorDebugThread3::GetActiveInternalFrames method [.NET Framework debugging]
- GetActiveInternalFrames method [.NET Framework debugging]
ms.assetid: d69796b4-5b6d-457c-85f6-2cf42e8a8773
topic_type:
- apiref
ms.openlocfilehash: b4f228d55c9ffd6b85ebd0b430a7f5db404320f6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124347"
---
# <a name="icordebugthread3getactiveinternalframes-method"></a>ICorDebugThread3::GetActiveInternalFrames メソッド
スタック上の内部フレーム ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objects) の配列を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp 
HRESULT GetActiveInternalFrames  
      (  
      [in] ULONG32 cInternalFrames,  
      [out] ULONG32 *pcInternalFrames,  
      [in, out,size_is(cInternalFrames), length_is(*pcInternalFrames)]  
            ICorDebugInternalFrame2 * ppInternalFrames[]  
      );  
```  
  
## <a name="parameters"></a>パラメーター  
 `cInternalFrames`  
 から`ppInternalFrames`に必要な内部フレームの数。  
  
 `pcInternalFrames`  
 入出力スタック上の内部フレームの数を格納している `ULONG32` へのポインター。  
  
 `ppInternalFrames`  
 [入力、出力]スタック上の内部フレームの配列のアドレスへのポインター。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|[ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)オブジェクトが正常に作成されました。|  
|E_INVALIDARG|`cInternalFrames` が0ではなく、`ppInternalFrames` が `null`か、または `pcInternalFrames` が `null`。|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|`ppInternalFrames` が内部フレームの数よりも小さくなっています。|  
  
## <a name="exceptions"></a>例外  
  
## <a name="remarks"></a>Remarks  
 内部フレームは、一時データを格納するためにランタイムによってスタックにプッシュされるデータ構造です。  
  
 最初に `GetActiveInternalFrames`を呼び出すときは、`cInternalFrames` パラメーターを 0 (ゼロ) に設定し、`ppInternalFrames` パラメーターを null に設定する必要があります。 `GetActiveInternalFrames` 最初にを返すと、`pcInternalFrames` にはスタック上の内部フレームの数が含まれます。  
  
 `GetActiveInternalFrames` は、2回目に呼び出す必要があります。 `cInternalFrames` パラメーターに適切なカウント (`pcInternalFrames`) を渡し、`ppInternalFrames`で適切にサイズ設定された配列へのポインターを指定する必要があります。  
  
 実際のスタックフレームを返すには、の[テキスト](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md)を使用します。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
