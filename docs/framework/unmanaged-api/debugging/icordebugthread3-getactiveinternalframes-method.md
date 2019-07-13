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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 58aaf0445fe42d083c12541056cb362f9a994944
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765211"
---
# <a name="icordebugthread3getactiveinternalframes-method"></a>ICorDebugThread3::GetActiveInternalFrames メソッド
内部フレームの配列を返します ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)オブジェクト)、スタックにします。  
  
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
 [in]期待される内部のフレーム数`ppInternalFrames`します。  
  
 `pcInternalFrames`  
 [out]ポインターを`ULONG32`内部スタック フレームの数を格納しています。  
  
 `ppInternalFrames`  
 [入力、出力]内部スタック フレームの配列のアドレスへのポインター。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|[ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)オブジェクトが正常に作成します。|  
|E_INVALIDARG|`cInternalFrames` 0 でないと`ppInternalFrames`は`null`、または`pcInternalFrames`は`null`します。|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|`ppInternalFrames` 内部のフレームの数よりも小さくなります。|  
  
## <a name="exceptions"></a>例外  
  
## <a name="remarks"></a>Remarks  
 内部フレームは、一時データを格納する、ランタイムによってスタックにプッシュするデータ構造です。  
  
 呼び出すと`GetActiveInternalFrames`、設定する必要があります、`cInternalFrames`パラメーターを 0 (ゼロ) と`ppInternalFrames`パラメーターを null にします。 ときに`GetActiveInternalFrames`最初を返します、`pcInternalFrames`スタックには、内部のフレーム数が含まれています。  
  
 `GetActiveInternalFrames` 呼び出すことが 2 番目の時間。 適切な数を渡す必要があります (`pcInternalFrames`) で、`cInternalFrames`パラメーターで適切なサイズの配列へのポインターを指定して`ppInternalFrames`します。  
  
 使用して、 [icordebugstackwalk::getframe](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md)メソッドを返す実際のスタック フレーム。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
