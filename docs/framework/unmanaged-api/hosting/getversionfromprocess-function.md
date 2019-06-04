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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3055ac73f15329015f532f42c1f922eab38828cb
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490306"
---
# <a name="getversionfromprocess-function"></a>GetVersionFromProcess 関数
指定されたプロセスのハンドルに関連付けられている共通言語ランタイム (CLR) のバージョン番号を取得します。  
  
 この関数は、.NET Framework 4 では廃止されました。  
  
## <a name="syntax"></a>構文  
  
```  
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
 [out]正常に終了メソッドのバージョン番号の文字列を格納するバッファー。  
  
 `cchBuffer`  
 [in]バージョンのバッファーの長さ。  
  
 `pdwLength`  
 [out]バージョン番号の文字列の長さへのポインター。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の値だけでなく、WinError.h で定義されている標準のコンポーネント オブジェクト モデル (COM) エラー コードを返します。  
  
|リターン コード|説明|  
|-----------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
|E_INVALIDARG|`pVersion` null と`cchBuffer`が null でないまたはその逆です。<br /><br /> - または -<br /><br /> `hProcess` プロセスに有効なハンドルではありません。<br /><br /> - または -<br /><br /> CLR は読み込まれません。|  
|ERROR_INSUFFICIENT_BUFFER|`cchBuffer` null か、バージョン文字列の長さよりも小さい。|  
|E_NOTIMPL|このメソッドは、Microsoft Windows 95、Microsoft Windows 98、または Microsoft Windows Millennium Edition オペレーティング システムでご利用いただけません。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [GetRequestedRuntimeInfo 関数](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)
- [GetRequestedRuntimeVersion 関数](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [非推奨の CLR ホスト関数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
