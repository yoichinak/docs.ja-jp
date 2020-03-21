---
title: GetCORSystemDirectory 関数
ms.date: 03/30/2017
api_name:
- GetCORSystemDirectory
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetCORSystemDirectory
helpviewer_keywords:
- GetCORSystemDirectory function [.NET Framework hosting]
ms.assetid: 3dcd16a7-dafc-4ca8-b5cd-20ffb37db91d
topic_type:
- apiref
ms.openlocfilehash: bdafacfe52d678aacfcd44de1e924bcb88547424
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178202"
---
# <a name="getcorsystemdirectory-function"></a>GetCORSystemDirectory 関数
プロセスに読み込まれる共通言語ランタイム (CLR) のインストール ディレクトリを返します。 インストール ディレクトリは、"c:\windows\microsoft.net\framework\v1.0.3705" など、完全修飾ディレクトリです。  
  
 この関数の使用は非推奨とされます。 これは、.NET フレームワーク 4 で提供[されるメソッドに](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md)置き換えられます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetCORSystemDirectory (
    [out] LPWSTR  pbuffer,
    [in]  DWORD   cchBuffer,
    [out] DWORD*  dwlength  
);
```  
  
## <a name="parameters"></a>パラメーター  
 `pbuffer`  
 [アウト]プロセスに読み込まれるランタイムのインストール ディレクトリの完全修飾名を含む文字列をランタイムが返すバッファー。 ランタイムがまだプロセスに読み込まれていない場合、この関数は、コンピューターにインストールされている最新バージョンのランタイムに対応するディレクトリ情報を返します。  
  
 `cchBuffer`  
 [in]のサイズ (バイト単位)`pbuffer`です。  
  
 `dwLength`  
 [アウト]で返される文字数`pbuffer`。  
  
## <a name="remarks"></a>解説  
  
> [!CAUTION]
> CLR のバージョン 4 を実行しているプロセスでは、この関数を使用しないでください。 以前のバージョンの CLR がコンピューターにインストールされている場合、この関数は、そのバージョンのインストール ディレクトリを返します。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** msCorEE.h  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [非推奨の CLR ホスト関数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
