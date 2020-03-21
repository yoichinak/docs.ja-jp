---
title: LoadStringRC 関数
ms.date: 03/30/2017
api_name:
- LoadStringRC
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- LoadStringRC
helpviewer_keywords:
- LoadStringRC function [.NET Framework hosting]
ms.assetid: 752e49b4-987c-4c28-a118-1a0c1ed510c5
topic_type:
- apiref
ms.openlocfilehash: 56ae7b7cf3b577bfe41ebd0bdd98e0da68047b44
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176241"
---
# <a name="loadstringrc-function"></a>LoadStringRC 関数
現在のスレッドの既定のカルチャを使用して、HRESULT 値をエラー メッセージに変換します。  
  
 この関数は、.NET Framework 4 では廃止されました。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT LoadStringRC (  
    [in]  UINT    iResourceID,
    [out] LPWSTR  szBuffer,
    [in]  int     iMax,
    [in]  int     bQuiet  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `iResourceID`  
 [in]HRESULT。  
  
 `szBuffer`  
 [アウト]正常終了時にエラー メッセージが格納されているバッファー。  
  
 `iMax`  
 [in]エラー メッセージ バッファーのサイズ。  
  
 `bQuiet`  
 [in]無視。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、WinError.h で定義されている次の値に加えて、標準のコンポーネント オブジェクト モデル (COM) エラー コードを返します。  
  
|リターン コード|説明|  
|-----------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
|E_INVALIDARG|`szBuffer`が null`iMax`であるか、ゼロ (0) です。|  
  
## <a name="remarks"></a>解説  
 メソッドが正常に完了しなかった場合は、`szBuffer`空の文字列が含まれます。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** msCorEE.h  
  
 **ライブラリ:** MSCorEE.dll と Mscorwks.dll. Mscorwks.dll の代わりに MSCorEE.dll を使用して、.NET Framework の正しいバージョンを対象にしていることを確認します。  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [LoadStringRCEx 関数](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)
- [非推奨の CLR ホスト関数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
