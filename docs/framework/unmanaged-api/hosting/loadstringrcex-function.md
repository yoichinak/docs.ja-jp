---
title: LoadStringRCEx 関数
ms.date: 03/30/2017
api_name:
- LoadStringRCEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- LoadStringRCEx
helpviewer_keywords:
- LoadStringRCEx function [.NET Framework hosting]
ms.assetid: bc789636-ca14-4f07-8f77-9305874d7495
topic_type:
- apiref
ms.openlocfilehash: a300c2679ef11a84edb2ab89c8dea96e445c9ee3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177982"
---
# <a name="loadstringrcex-function"></a>LoadStringRCEx 関数
HRESULT 値を、指定したカルチャの適切なエラー メッセージに変換します。  
  
 この関数は、.NET Framework 4 では廃止されました。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT LoadStringRCEx (  
    [in]  LCID    lcid,
    [in]  UINT    iResouceID,
    [out] LPWSTR  szBuffer,
    [in]  int     iMax,
    [in]  int     bQuiet,
    [out] int    *pcwchUsed  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `lcid`  
 [in]カルチャ識別子。 既定のカルチャを`lcid`使用するには、-1 を渡します。  
  
 `iResourceID`  
 [in]HRESULT。  
  
 `szBuffer`  
 [アウト]正常終了時にエラー メッセージが格納されているバッファー。  
  
 `iMax`  
 [in]エラー メッセージ バッファーのサイズ。  
  
 `bQuiet`  
 [in]無視。  
  
 `pcwchUsed`  
 [アウト]エラー メッセージの長さへのポインター。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、WinError.h で定義されている標準 COM エラー コードを返します。  
  
|リターン コード|説明|  
|-----------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
|E_INVALIDARG|`szBuffer`は null`iMax`であるか、ゼロ (0) です。|  
  
## <a name="remarks"></a>解説  
 メソッドが正常に完了しなかった場合は、`szBuffer`空の文字列が含まれます。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** msCorEE.h  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Globalization.CultureInfo.LCID%2A?displayProperty=nameWithType>
- [LoadStringRC 関数](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)
- [非推奨の CLR ホスト関数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
