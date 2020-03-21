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
ms.openlocfilehash: 680af5afa3ebef5bcaf9e34580e421dcc8093aaf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178463"
---
# <a name="icordebugthread3getactiveinternalframes-method"></a>ICorDebugThread3::GetActiveInternalFrames メソッド
スタック上の内部フレーム[(ICorDebugInternalFrame2](icordebuginternalframe2-interface.md)オブジェクト) の配列を返します。  
  
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
 [in]で想定される内部フレームの`ppInternalFrames`数。  
  
 `pcInternalFrames`  
 [アウト]スタック上の内部`ULONG32`フレームの数を含むを指すポインター。  
  
 `ppInternalFrames`  
 [イン、アウト]スタック上の内部フレームの配列のアドレスへのポインター。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|オブジェクト[が](icordebuginternalframe2-interface.md)正常に作成されました。|  
|E_INVALIDARG|`cInternalFrames`は 0`ppInternalFrames`ではない`null`か、`pcInternalFrames`または`null`です。|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|`ppInternalFrames`は内部フレームの数より小さい。|  
  
## <a name="exceptions"></a>例外  
  
## <a name="remarks"></a>解説  
 内部フレームは、一時データを格納するためにランタイムによってスタックにプッシュされるデータ構造です。  
  
 最初に 呼`GetActiveInternalFrames`び出すときは、`cInternalFrames`パラメーターを 0 (ゼロ)`ppInternalFrames`に設定し、パラメーターを null に設定する必要があります。 最初`GetActiveInternalFrames`に戻るとき`pcInternalFrames`、スタックの内部フレームの数を格納します。  
  
 `GetActiveInternalFrames`その後、もう一度呼び出す必要があります。 パラメータに適切なカウント(`pcInternalFrames`) を渡し、 で適切なサイズの配列へのポインタを指定`ppInternalFrames`する必要があります。 `cInternalFrames`  
  
 実際の[スタック](icordebugthread3-getactiveinternalframes-method.md)フレームを返すためには、メソッドを使用します。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](debugging-interfaces.md)
- [デバッグ](index.md)
