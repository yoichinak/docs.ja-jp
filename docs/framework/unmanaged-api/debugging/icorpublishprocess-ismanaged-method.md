---
title: ICorPublishProcess::IsManaged メソッド
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.IsManaged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::IsManaged
helpviewer_keywords:
- IsManaged method, ICorPublishProcess interface [.NET Framework debugging]
- ICorPublishProcess::IsManaged method [.NET Framework debugging]
ms.assetid: 06b1f7cc-acdf-47a6-9d53-d9dec2424152
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 404403576b7fd32362a690d470a5ea4b48489d26
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484798"
---
# <a name="icorpublishprocessismanaged-method"></a>ICorPublishProcess::IsManaged メソッド
これによって、プロセスが参照されるかどうかを示す値を取得します[ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)コード管理されていることがわかっています。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT IsManaged (  
    [out] BOOL   *pbManaged  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pbManaged`  
 [out]プロセスにマネージ コードがあるかどうかを示すブール値へのポインター。 値が`true`場合は、プロセスにマネージ コードです。 それ以外の場合、`false`します。  
  
## <a name="remarks"></a>Remarks  
 現在のバージョン以降`ICorPublishProcess`がマネージ コード、プロセスにのみアクセスできるように`IsManaged`は常に返します`true`します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorPub.idl, CorPub.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [ICorPublishProcess インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
