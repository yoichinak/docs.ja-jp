---
title: GetCORVersion 関数
ms.date: 03/30/2017
api_name:
- GetCORVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetCORVersion
helpviewer_keywords:
- GetCORVersion function [.NET Framework hosting]
ms.assetid: 2f09cd37-bf3a-4cc5-87b0-adc42a7eed31
topic_type:
- apiref
ms.openlocfilehash: 1f40f27651d2d75cf2c3e4d7d1c21e1f47d402af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178189"
---
# <a name="getcorversion-function"></a>GetCORVersion 関数
現在のプロセスで実行されている共通言語ランタイム (CLR) のバージョン番号を返します。  
  
 この関数は、.NET Framework 4 では廃止されました。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetCORVersion (  
    [in] LPWSTR  pbuffer,  
    [in]  DWORD   cchBuffer,
    [out] DWORD*  dwlength  
);
```  
  
## <a name="parameters"></a>パラメーター  
 `pbuffer`  
 現在プロセスに読み込まれているランタイムのバージョンを指定する文字列を CLR が返すバッファーへのポインター。 返される文字列は、"v1.0.1216" のように[、CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)に渡される文字列と同じ形式になります。 ランタイムがまだプロセスに読み込まれていない場合、この関数は、コンピューターにインストールされている最新バージョンのランタイムに対応するディレクトリ情報を返します。  
  
 `cchBuffer`  
 に保持できる文字数`WCHAR``pbuffer`。  
  
 `dwLength`  
 で実際に返される文字数へのポインタ`pbuffer`。 null`pbuffer`ポインターの場合、ランタイムはE_POINTERを返します。 文字数が長い場合は`pbuffer`、ランタイムは ERROR_INSUFFICIENT_BUFFER を返します。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** msCorEE.h  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [非推奨の CLR ホスト関数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
