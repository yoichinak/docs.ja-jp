---
title: ICLRDebugging::OpenVirtualProcess メソッド
ms.date: 03/30/2017
api_name:
- ICLRDebugging.OpenVirtualProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging::OpenVirtualProcess
helpviewer_keywords:
- OpenVirtualProcess method [.NET Framework debugging]
- ICLRDebugging::OpenVirtualProcess method [.NET Framework debugging]
ms.assetid: e8ab7c41-d508-4ed9-8a31-ead072b5a314
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a313ea62455067fb36b94d942b0ce21589677e3b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122578"
---
# <a name="iclrdebuggingopenvirtualprocess-method"></a>ICLRDebugging::OpenVirtualProcess メソッド
ICorDebugProcess インターフェイスに対応するプロセスに読み込まれている共通言語ランタイム (CLR) モジュールを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT OpenVirtualProcess(  
    [in] ULONG64 moduleBaseAddress,  
    [in] IUnknown * pDataTarget,  
    [in] ICLRDebuggingLibraryProvider * pLibraryProvider,  
    [in] CLR_DEBUGGING_VERSION * pMaxDebuggerSupportedVersion,  
    [in] REFIID riidProcess,  
    [out, iid_is(riidProcess)] IUnknown ** ppProcess,  
    [in, out] CLR_DEBUGGING_VERSION * pVersion,  
    [out] CLR_DEBUGGING_PROCESS_FLAGS * pdwFlags);  
```  
  
## <a name="parameters"></a>パラメーター  
 `moduleBaseAddress`  
 [in]ターゲット プロセスのモジュールのベース アドレス。 COR_E_NOT_CLR が、指定したモジュールが CLR モジュールではない場合に返されます。  
  
 `pDataTarget`  
 [in]マネージ デバッガーがプロセスの状態を検査できるデータ ターゲット抽象化します。 デバッガーを実装する必要があります、 [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)インターフェイス。 実装する必要があります、 [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md)デバッグ中に CLR がインストールされていないローカル コンピューターのシナリオをサポートするインターフェイス。  
  
 `pLibraryProvider`  
 [in]バージョン固有のデバッグ ライブラリを検索しに読み込む要求を許可するライブラリのプロバイダーのコールバック インターフェイス。 このパラメーターは必要な場合にのみ`ppProcess`または`pFlags`ない`null`します。  
  
 `pMaxDebuggerSupportedVersion`  
 [in]このデバッガーでデバッグできる CLR の最新バージョン。 メジャー、マイナーを指定し、このデバッガーをサポートする最新の CLR バージョンからバージョンをビルドおよびリビジョン番号を将来のインプレース CLR サービス リリースの対応するために 65535 に設定する必要があります。  
  
 `riidProcess`  
 [in]取得する ICorDebugProcess インターフェイスの ID。 現時点では、可能な値は IID_CORDEBUGPROCESS3、IID_CORDEBUGPROCESS2、および IID_CORDEBUGPROCESS です。  
  
 `ppProcess`  
 [out]識別される COM インターフェイスへのポインター`riidProcess`します。  
  
 `pVersion`  
 [入力、出力]CLR のバージョン。 この値は、入力の`null`します。 指していることも、 [CLR_DEBUGGING_VERSION](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md)構造の場合、構造体の`wStructVersion`フィールドは、0 (ゼロ) に初期化する必要があります。  
  
 出力で返された`CLR_DEBUGGING_VERSION`CLR のバージョン情報が格納される構造体。  
  
 `pdwFlags`  
 [out]指定したランタイムの概要情報フラグです。 参照してください、 [CLR_DEBUGGING_PROCESS_FLAGS](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md)フラグの説明のトピックです。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
|E_POINTER|`pDataTarget` `null`します。|  
|CORDBG_E_LIBRARY_PROVIDER_ERROR|[ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md)コールバックがエラーを返しますまたは、有効なハンドルは実現されません。|  
|CORDBG_E_MISSING_DATA_TARGET_INTERFACE|`pDataTarget` このバージョンのランタイムの必要なデータ ターゲットのインターフェイスを実装しません。|  
|CORDBG_E_NOT_CLR|指定されたモジュールが CLR モジュールではありません。 メモリが破損している、モジュールが使用できないか、CLR のバージョンが shim バージョンより新しいために、CLR モジュールを検出できない場合にも、この HRESULT が返されます。|  
|CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL|このランタイム バージョンは、このデバッグ モデルをサポートしていません。 現在、デバッグのモデルは前に、のバージョンの CLR によってサポートされていません、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]します。 `pwszVersion`出力パラメーターが設定されて、適切な値にこのエラーが発生後します。|  
|CORDBG_E_UNSUPPORTED_FORWARD_COMPAT|CLR のバージョンでは、このデバッガーでサポートされるバージョンを超えています。 `pwszVersion`出力パラメーターが設定されて、適切な値にこのエラーが発生後します。|  
|E_NO_INTERFACE|`riidProcess`インターフェイスは利用できません。|  
|CORDBG_E_UNSUPPORTED_VERSION_STRUCT|`CLR_DEBUGGING_VERSION`構造体には、認識されている値はありません。`wStructVersion`します。 この時点でのみ使用できる値は 0 です。|  
  
## <a name="exceptions"></a>例外  
  
## <a name="remarks"></a>Remarks  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
