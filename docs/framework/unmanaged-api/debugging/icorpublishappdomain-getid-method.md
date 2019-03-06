---
title: ICorPublishAppDomain::GetID メソッド
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomain.GetID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomain::GetID
helpviewer_keywords:
- GetID method, ICorPublishAppDomain interface [.NET Framework debugging]
- ICorPublishAppDomain::GetID method [.NET Framework debugging]
ms.assetid: 229437e3-1465-4bd8-8846-9804b2488133
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a7541a2093fe877fb84a8a05237f18c4da43c44
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57465986"
---
# <a name="icorpublishappdomaingetid-method"></a>ICorPublishAppDomain::GetID メソッド
この一意識別子を取得します。 [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetID (  
    [out] ULONG32   *puId  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `puId`  
 [out]アプリケーション ドメインの識別子へのポインター。  
  
## <a name="remarks"></a>Remarks  
 識別子は、格納しているプロセスのスコープ内でのみ一意です。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorPub.idl, CorPub.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [ICorPublishAppDomain インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)
