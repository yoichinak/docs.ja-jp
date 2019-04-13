---
title: ICLRRuntimeInfo::GetVersionString メソッド
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetVersionString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetVersionString
helpviewer_keywords:
- ICLRRuntimeInfo::GetVersionString method [.NET Framework hosting]
- GetVersionString method, ICLRRuntimeInfo interface [.NET Framework hosting]
ms.assetid: 98b097ef-2276-4dd9-8551-b03c972e8179
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d6e320936430307dab066eecc835ac5c84bd22bc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59202327"
---
# <a name="iclrruntimeinfogetversionstring-method"></a>ICLRRuntimeInfo::GetVersionString メソッド
関連付けられている共通言語ランタイム (CLR) バージョン情報を取得する指定された[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)インターフェイス。  
  
 このメソッドは、次の関数よりも優先されます。  
  
-   [GetRequestedRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
  
-   [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetVersionString(  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out]  DWORD *pcchBuffer);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pwzBuffer`  
 [out].NET Framework のコンパイル バージョン形式で"v*A*.*B*[.*X*]"。 *A*、 *B*、および*X*はメジャー バージョン、マイナー バージョン、およびビルド番号に対応する 10 進数。 *X*は省略可能です。 場合*X*が存在しない場合は末尾のピリオドです。  
  
> [!NOTE]
>  このパラメーターは、C:\Windows\Microsoft.NET\Framework 下に表示されます、.NET Framework のバージョンのディレクトリ名を一致する必要があります。  
  
 例の値は、"v1.0.3705"、"v1.1.4322"、"v2.0.50727"および"v4.0 です。*x*"ここで、 *x*インストールされているビルドの数によって異なります。 "V"プレフィックスが必須であるに注意してください。  
  
 `pchBuffer`  
 [入力、出力]サイズを示す`pwzBuffer`バッファー オーバーランを回避します。 場合`pwzBuffer`は`null`、`pchBuffer`の必要なサイズを返します`pwzBuffer`事前割り当てを許可します。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
|E_POINTER|`pwzBuffer` または`pchBuffer`が null です。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MetaHost.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRRuntimeInfo インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [.NET Framework 4 および 4.5 で追加された CLR ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [ホスト](../../../../docs/framework/unmanaged-api/hosting/index.md)
