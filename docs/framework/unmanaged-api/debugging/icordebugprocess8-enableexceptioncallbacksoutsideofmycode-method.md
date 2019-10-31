---
title: ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode メソッド
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: b3af44ec-7d41-425b-aed9-0c4379e5cbe9
ms.openlocfilehash: b6bfd258f35f19719be5e5169a1edc22a358371c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123385"
---
# <a name="icordebugprocess8enableexceptioncallbacksoutsideofmycode-method"></a>ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode メソッド
[.NET Framework 4.6 以降のバージョンでサポートされています]  
  
 特定の種類の[ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)例外コールバックを有効または無効にします。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT EnableExceptionCallbacksOutsideOfMyCode(  
   [in] BOOL enableExceptionsOutsideOfJMC  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `enableExceptionsOutsideOfJMC`  
 [入力]  
  
## <a name="remarks"></a>Remarks  
 `enableExceptionsOutsideOfJMC` の値が `false` の場合:  
  
- DEBUG_EXCEPTION_FIRST_CHANCE 例外が発生しても、デバッガーへのコールバックは行われません。  
  
- 例外がユーザーコードをエスケープしない場合 (つまり、例外の発生元から例外ハンドラーへのパスには、ジャスト Mycode または JMC としてマークされたメソッドがない場合)、DEBUG_EXCEPTION_CATCH_HANDLER_FOUND 例外によってデバッガーへのコールバックが発生することはありません。  
  
 `enableExceptionsOutsideOfJMC` の既定値は `true`です。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugProcess8 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
