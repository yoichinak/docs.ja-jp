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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5fd8314c018653703a262c8c43e6113886c25047
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56978684"
---
# <a name="icordebugmodule-interface"></a>ICorDebugModule インターフェイス

実行可能ファイルまたはダイナミック リンク ライブラリ (DLL) のいずれかである共通言語ランタイム (CLR) モジュールを表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[CreateBreakpoint メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-createbreakpoint-method.md)|実装されていません。|  
|[EnableClassLoadCallbacks メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enableclassloadcallbacks-method.md)|決定かどうか、 [icordebugmanagedcallback::loadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)と[icordebugmanagedcallback::unloadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)このモジュールのコールバックが呼び出されます。|  
|[EnableJITDebugging メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enablejitdebugging-method.md)|ジャストイン タイム (JIT) コンパイラがこのモジュール内でメソッドのデバッグ情報を保持するかどうかを判断します。|  
|[GetAssembly メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)|このモジュールを格納しているアセンブリを取得します。|  
|[GetBaseAddress メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getbaseaddress-method.md)|モジュールのベース アドレスを取得します。|  
|[GetClassFromToken メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md)|メタデータ ICorDebugClass を取得します。|  
|[GetEditAndContinueSnapshot メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-geteditandcontinuesnapshot-method.md)|非推奨。|  
|[GetFunctionFromRVA メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromrva-method.md)|実装されていません。|  
|[GetFunctionFromToken メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromtoken-method.md)|メタデータ トークンで指定されている関数を取得します。|  
|[GetGlobalVariableValue メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getglobalvariablevalue-method.md)|指定のグローバル変数の値オブジェクトを取得します。|  
|[GetMetaDataInterface メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getmetadatainterface-method.md)|モジュールのメタデータの検査に使用できるメタデータ インターフェイス ポインターを取得します。|  
|[GetName メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)|モジュールのファイル名を取得します。|  
|[GetProcess メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getprocess-method.md)|このモジュールを格納しているプロセスを取得します。|  
|[GetSize メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)|モジュールのサイズをバイト単位で取得します。|  
|[GetToken メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-gettoken-method.md)|このモジュールのテーブルのエントリのトークンを取得します。|  
|[IsDynamic メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isdynamic-method.md)|モジュールが動的かどうかを示します。|  
|[IsInMemory メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isinmemory-method.md)|このモジュールは、メモリ内にのみ存在するかどうかを示します。|  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [ICorDebug インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
