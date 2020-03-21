---
title: GetVersionFromProcess 関数
ms.date: 03/30/2017
api_name:
- GetVersionFromProcess
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetVersionFromProcess
helpviewer_keywords:
- GetVersionFromProcess function [.NET Framework hosting]
ms.assetid: a9f7f824-64a1-408d-8607-91c7f19d21fe
topic_type:
- apiref
ms.openlocfilehash: a04a0c5e6865c3664d2cb5fb341c3625e35d4d7c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178130"
---
# <a name="getversionfromprocess-function"></a>GetVersionFromProcess 関数
指定したプロセス ハンドルに関連付けられている共通言語ランタイム (CLR) のバージョン番号を取得します。  
  
 この関数は、.NET Framework 4 では廃止されました。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetVersionFromProcess (  
    [in]  HANDLE  hProcess,
    [out] LPWSTR  pVersion,
    [in]  DWORD   cchBuffer,
    [out] DWORD  *dwLength  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `hProcess`  
 [in]プロセスへのハンドル。  
  
 `pVersion`  
 [アウト]メソッドが正常に完了したときに、バージョン番号文字列を格納するバッファー。  
  
 `cchBuffer`  
 [in]バージョン バッファーの長さ。  
  
 `pdwLength`  
 [アウト]バージョン番号文字列の長さへのポインター。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、WinError.h で定義されている次の値に加えて、標準のコンポーネント オブジェクト モデル (COM) エラー コードを返します。  
  
|リターン コード|説明|  
|-----------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
|E_INVALIDARG|`pVersion`は null`cchBuffer`で、null ではないか、またはその逆です。<br /><br /> または<br /><br /> `hProcess`はプロセスへの有効なハンドルではありません。<br /><br /> または<br /><br /> CLR が読み込まれていません。|  
|ERROR_INSUFFICIENT_BUFFER|`cchBuffer`は、バージョン文字列の長さより null か、より小さい値です。|  
|E_NOTIMPL|この方法は、Windows 95、Windows 98、またはマイクロソフトの Windows ミレニアム エディションのオペレーティング システムでは使用できません。|  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** msCorEE.h  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [GetRequestedRuntimeInfo 関数](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)
- [GetRequestedRuntimeVersion 関数](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [非推奨の CLR ホスト関数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
