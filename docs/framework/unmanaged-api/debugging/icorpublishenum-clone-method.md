---
title: ICorPublishEnum::Clone メソッド
ms.date: 03/30/2017
api_name:
- ICorPublishEnum.Clone
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum::Clone
helpviewer_keywords:
- Clone method, ICorPublishEnum interface [.NET Framework debugging]
- ICorPublishEnum::Clone method [.NET Framework debugging]
ms.assetid: c9a26ea3-b8eb-4b8e-854f-9a2ca26b3b39
topic_type:
- apiref
ms.openlocfilehash: e9f7f1fc0f04e8cc8c69d533c1dbba380d04ebfb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140488"
---
# <a name="icorpublishenumclone-method"></a>ICorPublishEnum::Clone メソッド
この[ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)オブジェクトのコピーを作成します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Clone (  
    [out] ICorPublishEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `ppEnum`  
 入出力この `ICorPublishEnum` オブジェクトのコピーである `ICorPublishEnum` オブジェクトのアドレスへのポインター。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorPub .idl、CorPub .h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorPublishEnum インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)
