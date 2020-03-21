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
ms.openlocfilehash: 6132e94544b30486b70ecfec49c1ddd5e3c0f50b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178116"
---
# <a name="getrequestedruntimeversionforclsid-function"></a>GetRequestedRuntimeVersionForCLSID 関数
指定した クラスの共通言語ランタイム (CLR) のバージョン情報を取得`CLSID`します。  
  
 この関数は、.NET Framework 4 では廃止されました。  
  
## <a name="syntax"></a>構文  
  
```cpp  
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
 [in] コンポーネント`CLSID`の  
  
 `pVersion`  
 [アウト] 正常終了した場合に、バージョン番号文字列を格納するバッファー。  
  
 `cchBuffer`  
 [in] `pVersion`バッファーのサイズ (ワイド文字)。  
  
 `dwLength`  
 [アウト]返されたバッファーの長さ (バイト単位)。  
  
 `dwResolutionFlags`  
 [in] CLSID_RESOLUTION_FLAGS値の 1 つ。 次の値がサポートされています。  
  
- CLSID_RESOLUTION_DEFAULT: (0x0) 既定の相互運用動作を使用することを指定します。  
  
- CLSID_RESOLUTION_REGISTERED: (0x1) レジストリを検索し、shim ポリシーを適用する必要があることを指定します。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|関数が正常に返されました。|  
|E_INVALIDARG|パラメータの 1 つに無効な型または形式があります。|  
|ERROR_INSUFFICIENT_BUFFER|バッファー`pVersion`の大きさが、バージョン文字列全体を保持するのに十分ではありません。|  
|REGDB_E_CLASSNOTREG|指定された`CLSID`に登録されているクラスがありません。|  
|E_POINTER|`dwLength`は null`cchBuffer`であるか、バージョン文字列を保持するのに十分な`pVersion`大きさですが、null です。|  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** msCorEE.h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [非推奨の CLR ホスト関数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
