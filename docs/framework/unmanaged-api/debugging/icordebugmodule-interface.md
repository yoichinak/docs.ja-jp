---
title: ICorDebugModule インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule
helpviewer_keywords:
- ICorDebugModule interface [.NET Framework debugging]
ms.assetid: 32e4d6fa-e5a3-413e-9166-d5e2871d3114
topic_type:
- apiref
ms.openlocfilehash: 971d6a6a2157c48dcb9105e9f523b1f077098479
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129480"
---
# <a name="icordebugmodule-interface"></a>ICorDebugModule インターフェイス

実行可能ファイルまたはダイナミックリンクライブラリ (DLL) のいずれかである共通言語ランタイム (CLR) モジュールを表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[CreateBreakpoint メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-createbreakpoint-method.md)|実装されていません。|  
|[EnableClassLoadCallbacks メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enableclassloadcallbacks-method.md)|このモジュールに対して、" [UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) " コール[バック:: loadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)との各コールバックを呼び出すかどうかを決定します。|  
|[EnableJITDebugging メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enablejitdebugging-method.md)|Just-in-time (JIT) コンパイラが、このモジュール内のメソッドのデバッグ情報を保持するかどうかを決定します。|  
|[GetAssembly メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)|このモジュールの格納アセンブリを取得します。|  
|[GetBaseAddress メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getbaseaddress-method.md)|モジュールのベースアドレスを取得します。|  
|[GetClassFromToken メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md)|メタデータから、このクラスを取得します。|  
|[GetEditAndContinueSnapshot メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-geteditandcontinuesnapshot-method.md)|非推奨。|  
|[GetFunctionFromRVA メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromrva-method.md)|実装されていません。|  
|[GetFunctionFromToken メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromtoken-method.md)|メタデータトークンによって指定された関数を取得します。|  
|[GetGlobalVariableValue メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getglobalvariablevalue-method.md)|指定したグローバル変数の値オブジェクトを取得します。|  
|[GetMetaDataInterface メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getmetadatainterface-method.md)|モジュールのメタデータを調べるために使用できるメタデータインターフェイスポインターを取得します。|  
|[GetName メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)|モジュールのファイル名を取得します。|  
|[GetProcess メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getprocess-method.md)|このモジュールの格納プロセスを取得します。|  
|[GetSize メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)|モジュールのサイズ (バイト単位) を取得します。|  
|[GetToken メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-gettoken-method.md)|このモジュールのテーブルエントリのトークンを取得します。|  
|[IsDynamic メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isdynamic-method.md)|モジュールが動的かどうかを示します。|  
|[IsInMemory メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isinmemory-method.md)|このモジュールがメモリ内にのみ存在するかどうかを示します。|  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebug インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
