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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c71ccbc62ea026a55a7e84f6925a78850594a813
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57473788"
---
# <a name="icordebugmodule2setjitcompilerflags-method"></a>ICorDebugModule2::SetJITCompilerFlags メソッド
この ICorDebugModule2 の・ イン タイム (JIT) コンパイルを制御するフラグを設定します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetJITCompilerFlags (  
    [in] DWORD dwFlags  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `dwFlags`  
 [in]ビットごとの組み合わせ、 [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)列挙値。  
  
## <a name="remarks"></a>Remarks  
 場合、`dwFlags`値が有効で、`SetJITCompilerFlags`メソッドは失敗します。  
  
 `SetJITCompilerFlags`メソッド内からのみ呼び出すことができます、 [icordebugmanagedcallback::loadmodule](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md)このモジュールのコールバック。 後の呼び出しを行う、`ICorDebugManagedCallback::LoadModule`コールバック配信されたが失敗します。  
  
 64 ビット プラットフォームまたは Win9x プラットフォームでは、エディット コンティニュはサポートされていません。 そのため、呼び出す場合、 `SetJITCompilerFlags` CORDEBUG_JIT_ENABLE_ENC フラグで設定を使用してこれら 2 つのプラットフォームのいずれかのメソッド`dwFlags`、`SetJITCompilerFlags`メソッドと特定のすべてのメソッドの編集し、続行などを[ICorDebugModule2:。ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md)は失敗します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
