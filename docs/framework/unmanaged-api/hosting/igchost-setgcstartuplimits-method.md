---
title: IGCHost::SetGCStartupLimits メソッド
ms.date: 03/30/2017
api_name:
- IGCHost.SetGCStartupLimits
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCStartupLimits
helpviewer_keywords:
- SetGCStartupLimits method, IGCHost interface [.NET Framework hosting]
- IGCHost::SetGCStartupLimits method [.NET Framework hosting]
ms.assetid: cae53926-82ac-4d1d-b297-0bde0bd1bebb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 365261883f0b81884bb7cf70614628c05f9067c5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59221008"
---
# <a name="igchostsetgcstartuplimits-method"></a>IGCHost::SetGCStartupLimits メソッド
ジェネレーション 0 のセグメントのサイズと最大サイズを設定します。  
  
> [!IMPORTANT]
>  以降では、[!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]セグメントのサイズを設定して、サイズの最大のジェネレーション 0 の値より大きい、`DWORD`を使用して、 [igchost 2::setgcstartuplimitsex](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)メソッド。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,  
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `SegmentSize`  
 [in]ガベージ コレクション システムによって使用されるセグメントのサイズ。  
  
 `MaxGen0Size`  
 [in]ジェネレーション 0 の最大サイズ。  
  
## <a name="remarks"></a>Remarks  
 `SetGCStartupLimits`メソッドを 1 回だけ呼び出すことができます。 これらの値は、後で変更することはできません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** GCHost.idl、GCHost.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IGCHost インターフェイス](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
