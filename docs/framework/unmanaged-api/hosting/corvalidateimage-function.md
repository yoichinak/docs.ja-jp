---
title: _CorValidateImage 関数
ms.date: 03/30/2017
api_name:
- _CorValidateImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorValidateImage
helpviewer_keywords:
- _CorValidateImage function [.NET Framework hosting]
ms.assetid: 0117e080-05f9-4772-885d-e1847230947c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: df9cc0cc86237b1ec439a4ec4fa6a75429c416d9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111177"
---
# <a name="corvalidateimage-function"></a>_CorValidateImage 関数
マネージド モジュール イメージを検証し、それらが読み込まれると、オペレーティング システム ローダーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
STDAPI _CorValidateImage (   
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `ImageBase`  
 [in]イメージを検証する際の開始位置へのポインターはマネージ コードです。 イメージは、メモリに既に読み込まれている必要があります。  
  
 `FileName`  
 [in]イメージのファイル名。  
  
## <a name="return-value"></a>戻り値  
 この関数は、標準の値を返します`E_INVALIDARG`、 `E_OUTOFMEMORY`、 `E_UNEXPECTED`、および`E_FAIL`、次の値。  
  
|戻り値|説明|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|イメージが無効です。 この値は、HRESULT 0xC000007BL を持っています。|  
|`STATUS_SUCCESS`|イメージが無効です。 この値は、HRESULT 0x00000000L を持っています。|  
  
## <a name="remarks"></a>Remarks  
 Windows XP およびそれ以降のバージョンでは、オペレーティング システム ローダーがマネージ モジュールの一般的なオブジェクト ファイルの形式 (COFF) ヘッダーで COM 記述子ディレクトリ ビットを調べることでチェックします。 設定済みビットでは、マネージ モジュールを示します。 MsCorEE.dll と呼び出しを読み込む場合は、ローダーは、マネージ モジュールを検出、 `_CorValidateImage`、次の操作を実行します。  
  
-   有効なマネージ モジュール イメージがあることを確認します。  
  
-   共通言語ランタイム (CLR) のエントリ ポイントにイメージ内のエントリ ポイントを変更します。  
  
-   Windows の 64 ビット バージョンでは、PE32 から pe 32 + 形式に変換することによってメモリにある画像を変更します。  
  
-   マネージ モジュール イメージが読み込まれるときにローダーに戻ります。  
  
 実行可能イメージでは、オペレーティング システム ローダーを呼び出して、 [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md)関数の実行可能ファイルで指定されたエントリ ポイントに関係なく、します。 ローダーの呼び出し、DLL アセンブリのイメージ、 [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md)関数。  
  
 `_CorExeMain` または`_CorDllMain`は、次の操作を実行します。  
  
-   CLR を初期化します。  
  
-   アセンブリの CLR ヘッダーからマネージ エントリ ポイントを検索します。  
  
-   実行を開始します。  
  
 ローダーの呼び出し、 [_CorImageUnloading](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md)を管理するときに関数モジュール イメージは読み込まれません。 ただし、この関数が任意のアクションを実行しません返すだけです。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ グローバル静的関数](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
