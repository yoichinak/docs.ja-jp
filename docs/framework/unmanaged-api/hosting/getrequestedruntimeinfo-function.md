---
title: GetRequestedRuntimeInfo 関数
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeInfo
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeInfo
helpviewer_keywords:
- GetRequestedRuntimeInfo function [.NET Framework hosting]
ms.assetid: 0dfd7cdc-c116-4e25-b56a-ac7b0378c942
topic_type:
- apiref
ms.openlocfilehash: db721e1ef774c87de0fa7da178463d832a3da756
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178154"
---
# <a name="getrequestedruntimeinfo-function"></a>GetRequestedRuntimeInfo 関数
アプリケーションが要求した共通言語ランタイム (CLR) に関するバージョン情報とディレクトリ情報を取得します。  
  
 この関数は、.NET Framework 4 では廃止されました。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetRequestedRuntimeInfo (  
    [in]  LPCWSTR  pExe,
    [in]  LPCWSTR  pwszVersion,
    [in]  LPCWSTR  pConfigurationFile,
    [in]  DWORD    startupFlags,
    [in]  DWORD    runtimeInfoFlags,
    [out] LPWSTR   pDirectory,
    [in]  DWORD    dwDirectory,
    [out] DWORD   *dwDirectoryLength,
    [out] LPWSTR   pVersion,
    [in]  DWORD    cchBuffer,
    [out] DWORD   *dwlength  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pExe`  
 [in]アプリケーションの名前。  
  
 `pwszVersion`  
 [in]ランタイムのバージョン番号を指定する文字列。  
  
 `pConfigurationFile`  
 [in]に関連付けられている`pExe`構成ファイルの名前。  
  
 `startupFlags`  
 [in][STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)列挙値の 1 つ以上。  
  
 `runtimeInfoFlags`  
 [in]1 つ以上の[RUNTIME_INFO_FLAGS](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md)列挙値。  
  
 `pDirectory`  
 [アウト]正常終了したランタイムへのディレクトリ パスを格納するバッファー。  
  
 `dwDirectory`  
 [in]ディレクトリ バッファの長さ。  
  
 `dwDirectoryLength`  
 [アウト]ディレクトリ パス文字列の長さへのポインター。  
  
 `pVersion`  
 [アウト]正常終了したランタイムのバージョン番号を格納するバッファー。  
  
 `cchBuffer`  
 [in]バージョン文字列バッファーの長さ。  
  
 `dwlength`  
 [アウト]バージョン文字列の長さへのポインター。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、WinError.h で定義されている次の値に加えて、標準のコンポーネント オブジェクト モデル (COM) エラー コードを返します。  
  
|リターン コード|説明|  
|-----------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
|ERROR_INSUFFICIENT_BUFFER|ディレクトリ バッファのサイズが、ディレクトリ パスを格納するのに十分ではありません。<br /><br /> - または -<br /><br /> バージョン バッファーのサイズが、バージョン文字列を格納するのに十分ではありません。|  
  
## <a name="remarks"></a>解説  
 この`GetRequestedRuntimeInfo`メソッドは、プロセスに読み込まれたバージョンに関する実行時情報を返します。  
  
 .NET Framework Version 2.0 では、次の方法を使用して、インストールされている`GetRequestedRuntimeInfo`最新バージョンに関する情報を取得できます。  
  
- `pExe`、 、`pwszVersion`および`pConfigurationFile`パラメーターを null として指定します。  
  
- パラメーターの`RUNTIME_INFO_FLAGS`列挙体にRUNTIME_INFO_UPGRADE_VERSIONフラグを`runtimeInfoFlags`指定します。  
  
 この`GetRequestedRuntimeInfo`メソッドは、次の状況では最新の CLR バージョンを返しません。  
  
- 特定の CLR バージョンの読み込みを指定するアプリケーション構成ファイルが存在します。 パラメータに null を指定した場合でも、.NET Framework では構成`pConfigurationFile`ファイルが使用されます。  
  
- メソッド[は](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)、以前の CLR バージョンを指定して呼び出されました。  
  
- 以前の CLR バージョン用にコンパイルされたアプリケーションが現在実行されています。  
  
 パラメーターには`runtimeInfoFlags`、`RUNTIME_INFO_FLAGS`一度に列挙のアーキテクチャ定数の 1 つだけを指定できます。  
  
- RUNTIME_INFO_REQUEST_IA64  
  
- RUNTIME_INFO_REQUEST_AMD64  
  
- RUNTIME_INFO_REQUEST_X86  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** msCorEE.h  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [GetRequestedRuntimeVersion 関数](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [GetVersionFromProcess 関数](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [非推奨の CLR ホスト関数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
