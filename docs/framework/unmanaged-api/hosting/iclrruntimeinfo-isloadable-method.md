---
title: ICLRRuntimeInfo::IsLoadable メソッド
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsLoadable
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsLoadable
helpviewer_keywords:
- IsLoadable method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoadable method [.NET Framework hosting]
ms.assetid: 205ca53b-e78e-49b2-9a46-2a7823e96b8c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 52257b30b8172b80f968df25115956b6995c1552
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59101589"
---
# <a name="iclrruntimeinfoisloadable-method"></a>ICLRRuntimeInfo::IsLoadable メソッド
このインターフェイスに関連付けられているランタイムを考慮して、現在のプロセスに読み込めるかどうかを示す、プロセスに読み込まれることが既にある他のランタイム。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT IsLoadable(  
        [out, retval] BOOL *pbLoadable);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pbLoadable`  
 [out]`true`このランタイムは、現在のプロセスに読み込まれます。 それ以外にできる場合は`false`します。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
|E_POINTER|`pbLoadable` null です。|  
  
## <a name="remarks"></a>Remarks  
 別のランタイムが既にプロセスに読み込まれていて、インプロセスでサイド バイ サイドで実行するため、このインターフェイスに関連付けられているランタイムを読み込める`pbLoadable`返します`true`します。 2 つのランタイムはサイド バイ サイドでインプロセスで実行できない場合`pbLoadable`返します`false`します。 たとえば、共通言語ランタイム (CLR) バージョン 4 では、CLR バージョン 2.0 を使用して同じプロセス内で並列してまたは CLR バージョン 1.1 を実行できます。 ただし、CLR の version 1.1 と CLR の version 2.0 では、サイド バイ サイドでプロセスを実行できません。  
  
 かどうかは、プロセスにランタイムが読み込まれません、このメソッドはその常に返します`true`します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MetaHost.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRRuntimeInfo インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [ホスト](../../../../docs/framework/unmanaged-api/hosting/index.md)
