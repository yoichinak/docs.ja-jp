---
title: GetRequestedRuntimeVersionForCLSID 関数
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeVersionForCLSID
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeVersionForCLSID
helpviewer_keywords:
- GetRequestedRuntimeVersionForCLSID function [.NET Framework hosting]
ms.assetid: 5bb12f9a-0612-434b-b4ed-2db636a20bec
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0ca125932ede48aa43bc51e3d5a7851fb7762547
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490319"
---
# <a name="getrequestedruntimeversionforclsid-function"></a>GetRequestedRuntimeVersionForCLSID 関数
適切な共通言語ランタイム (CLR) のバージョン情報と、指定したクラスを取得します。`CLSID`します。  
  
 この関数は、.NET Framework 4 では廃止されました。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetRequestedRuntimeVersionForCLSID (  
    [in]  REFCLSID   rclsid,   
    [out]  LPWSTR     pVersion,   
    [in]  DWORD      cchBuffer,   
    [out] DWORD*     dwLength,   
    [in]  CLSID_RESOLUTION_FLAGS dwResolutionFlags  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `rclsid`  
 [in] `CLSID`のコンポーネント。  
  
 `pVersion`  
 [out] 正常完了時にバージョン番号の文字列を格納するバッファー。  
  
 `cchBuffer`  
 [in] ワイド文字単位のサイズの`pVersion`バッファー。  
  
 `dwLength`  
 [out]返されたバッファーの長さ、(バイト単位)。  
  
 `dwResolutionFlags`  
 [in] CLSID_RESOLUTION_FLAGS 値の 1 つ。 次の値がサポートされています。  
  
- CLSID_RESOLUTION_DEFAULT:(0x0) 既定の相互運用機能の動作を使用することを指定します。  
  
- CLSID_RESOLUTION_REGISTERED:(0x1)、レジストリを検索する必要があるし、shim のポリシーを適用することを指定します。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|関数が正常に返されます。|  
|E_INVALIDARG|パラメーターの 1 つに、無効な型または形式。|  
|ERROR_INSUFFICIENT_BUFFER|`pVersion`バッファーはバージョン文字列全体を保持するために十分な大きさがありません。|  
|REGDB_E_CLASSNOTREG|クラスの指定した登録がない`CLSID`します。|  
|E_POINTER|`dwLength` null の場合または`cchBuffer`バージョン文字列を保持するために十分な大きさが`pVersion`が null です。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [非推奨の CLR ホスト関数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
