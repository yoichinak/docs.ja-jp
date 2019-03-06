---
title: IGCHost::GetStats メソッド
ms.date: 03/30/2017
api_name:
- IGCHost.GetStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetStats
helpviewer_keywords:
- GetStats method, IGCHost interface [.NET Framework hosting]
- IGCHost::GetStats method [.NET Framework hosting]
ms.assetid: c4ae022c-46ac-4f19-9ddd-09b955f19412
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1b8af1de3daf08a8389a5b0e6ebb278646345f9b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57482614"
---
# <a name="igchostgetstats-method"></a>IGCHost::GetStats メソッド
ガベージ コレクション システムの現在の状態の統計情報を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pStats`  
 [入力、出力]ポインターを[COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)ガベージ コレクション システムの現在の状態の統計情報を含む構造体。  
  
## <a name="remarks"></a>Remarks  
 統計情報は、スマート配賦システムによってガベージ コレクション システムの動作を使用できます。 たとえば、配賦システム可能性があります決定をより多くのメモリを追加またはコレクションを強制する必要がある統計情報を確認した後します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** GCHost.idl、GCHost.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [IGCHost インターフェイス](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
