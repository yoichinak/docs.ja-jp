---
title: ICorPublishProcess::EnumAppDomains メソッド
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.EnumAppDomains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::EnumAppDomains
helpviewer_keywords:
- EnumAppDomains method [.NET Framework debugging]
- ICorPublishProcess::EnumAppDomains method [.NET Framework debugging]
ms.assetid: 7da621fc-e7d0-4c00-9439-5c93619d7414
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c938adb518fe8c2bd7ac59fe47d7cd2a4f6df886
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492765"
---
# <a name="icorpublishprocessenumappdomains-method"></a>ICorPublishProcess::EnumAppDomains メソッド
これによって参照されているプロセスでアプリケーション ドメインの列挙子を取得します。 [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT EnumAppDomains (  
    [out] ICorPublishAppDomainEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `ppEnum`  
 [out]アドレスへのポインター、 [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)このプロセスでのアプリケーション ドメインのコレクションを反復処理できるインスタンス。  
  
## <a name="remarks"></a>Remarks  
 アプリケーション ドメインの一覧が存在するアプリケーション ドメインのスナップショットに基づいたとき、`EnumAppDomains`メソッドが呼び出されます。 このメソッドは、最新の一覧を作成する 2 回以上呼び出すことがあります。 このメソッドの後続の呼び出しは既存のリストを受けません。  
  
 プロセスが終了している場合`EnumAppDomains`CORDBG_E_PROCESS_TERMINATED の HRESULT 値を持つは失敗します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorPub.idl, CorPub.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [ICorPublishProcess インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
