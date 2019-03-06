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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9afe4afcaefb9409edb93bd1da96a02db20dbd20
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466736"
---
# <a name="getcorsystemdirectory-function"></a>GetCORSystemDirectory 関数
プロセスに読み込まれる共通言語ランタイム (CLR) のインストール ディレクトリを返します。 インストール ディレクトリは、完全修飾"c:\windows\microsoft.net\framework\v1.0.3705"など。  
  
 この関数が非推奨とされます。 それは置き換えられて、 [iclrruntimeinfo::getruntimedirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md)メソッドで提供される、 [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetCORSystemDirectory (   
    [out] LPWSTR  pbuffer,     
    [in]  DWORD   cchBuffer,   
    [out] DWORD*  dwlength  
);   
```  
  
## <a name="parameters"></a>パラメーター  
 `pbuffer`  
 [out]ランタイムがプロセスに読み込まれたランタイムのインストール ディレクトリの完全修飾名を含む文字列を返すバッファー。 ランタイムがプロセスにまだ読み込まれていない場合は、コンピューターにインストールされているランタイムの最新バージョンの適切なディレクトリ情報を返します。  
  
 `cchBuffer`  
 [in]サイズ (バイト単位) の`pbuffer`します。  
  
 `dwLength`  
 [out]返される文字数`pbuffer`します。  
  
## <a name="remarks"></a>Remarks  
  
> [!CAUTION]
>  CLR の version 4 を実行しているプロセスでは、この関数は使用しないでください。 CLR の以前のバージョンは、コンピューターにインストールされて、この関数はそのバージョンのインストール ディレクトリを返します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [非推奨の CLR ホスト関数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
