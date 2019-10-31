---
title: ICorDebugModule2::SetJITCompilerFlags メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.SetJITCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::SetJITCompilerFlags
helpviewer_keywords:
- ICorDebugModule2::SetJITCompilerFlags method [.NET Framework debugging]
- SetJITCompilerFlags method [.NET Framework debugging]
ms.assetid: ea574c84-c622-4589-9a14-b55771af5e06
topic_type:
- apiref
ms.openlocfilehash: 2358cee1b3a9aa50fb1f0e61d558f164a39aa86c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137359"
---
# <a name="icordebugmodule2setjitcompilerflags-method"></a>ICorDebugModule2::SetJITCompilerFlags メソッド
この ICorDebugModule2 の just-in-time (JIT) コンパイルを制御するフラグを設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetJITCompilerFlags (  
    [in] DWORD dwFlags  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `dwFlags`  
 から[CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)列挙値のビットごとの組み合わせ。  
  
## <a name="remarks"></a>Remarks  
 `dwFlags` 値が無効な場合、`SetJITCompilerFlags` メソッドは失敗します。  
  
 `SetJITCompilerFlags` メソッドを呼び出すことができるのは、このモジュールの " [LoadModule](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md) " コールバック内からだけです。 `ICorDebugManagedCallback::LoadModule` コールバックが配信された後に呼び出しを試みると失敗します。  
  
 64ビットまたは Win9x プラットフォームでは、エディットコンティニュはサポートされていません。 このため、`dwFlags`で CORDEBUG_JIT_ENABLE_ENC フラグを設定して、これら2つのプラットフォームのいずれかで `SetJITCompilerFlags` メソッドを呼び出すと、`SetJITCompilerFlags` メソッドと、 [ICorDebugModule2:: ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md)などのエディットコンティニュに固有のすべてのメソッドが失敗します。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
