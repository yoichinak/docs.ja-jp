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
ms.openlocfilehash: 3a6da0e845fa50d090cdf0808b211a5806c40961
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178213"
---
# <a name="_corvalidateimage-function"></a>_CorValidateImage 関数
マネージド モジュール イメージを検証し、それらが読み込まれると、オペレーティング システム ローダーに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
STDAPI _CorValidateImage (
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `ImageBase`  
 [in]マネージ コードとして検証するイメージの開始位置へのポインター。 イメージはメモリに読み込まれている必要があります。  
  
 `FileName`  
 [in]イメージのファイル名。  
  
## <a name="return-value"></a>戻り値  
 この関数は、標準値`E_INVALIDARG` `E_OUTOFMEMORY`、 `E_UNEXPECTED`、 `E_FAIL`、および 、 、および 、 を返します。  
  
|戻り値|説明|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|イメージが無効です。 この値は、HRESULT 0xC000007BL を持ちます。|  
|`STATUS_SUCCESS`|イメージは有効です。 この値は、HRESULT 0x0000000L を持ちます。|  
  
## <a name="remarks"></a>解説  
 Windows XP 以降のバージョンでは、オペレーティング システム ローダーは、共通オブジェクト ファイル形式 (COFF) ヘッダーの COM 記述子ディレクトリ ビットを調べることによって、マネージ モジュールをチェックします。 セット ビットは、マネージ モジュールを示します。 ローダーがマネージ モジュールを検出すると、MsCorEE.dll`_CorValidateImage`が読み込まれ、次のアクションが実行されます。  
  
- イメージが有効なマネージ モジュールであることを確認します。  
  
- イメージ内のエントリ ポイントを共通言語ランタイム (CLR) のエントリ ポイントに変更します。  
  
- 64 ビット バージョンの Windows では、メモリ内のイメージを PE32 から PE32+ 形式に変換して変更します。  
  
- マネージ モジュール イメージが読み込まれたときにローダーに戻ります。  
  
 実行可能イメージの場合、オペレーティング システム ローダーは、実行可能ファイルで指定されたエントリ ポイントに関係なく[、_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md)関数を呼び出します。 DLL アセンブリ イメージの場合、ローダーは[_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md)関数を呼び出します。  
  
 `_CorExeMain`または`_CorDllMain`、次のアクションを実行します。  
  
- CLR を初期化します。  
  
- アセンブリの CLR ヘッダーからマネージ エントリ ポイントを検索します。  
  
- 実行を開始します。  
  
 ローダーは、マネージ モジュール イメージがアンロードされるときに[_CorImageUnloading](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md)関数を呼び出します。 ただし、この関数はアクションを実行しません。それはちょうど戻ります。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれる  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ グローバル静的関数](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
