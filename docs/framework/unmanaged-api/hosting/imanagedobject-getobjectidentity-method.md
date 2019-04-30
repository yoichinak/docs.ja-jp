---
title: IManagedObject::GetObjectIdentity メソッド
ms.date: 03/30/2017
api_name:
- IManagedObject.GetObjectIdentity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetObjectIdentity
helpviewer_keywords:
- GetObjectIdentity method [.NET Framework hosting]
- IManagedObject::GetObjectIdentity method [.NET Framework hosting]
ms.assetid: b862ff3e-e480-4cdf-84e2-e1013334a467
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6d014d2900ea790f84331ed933143513ae9e63f7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61943517"
---
# <a name="imanagedobjectgetobjectidentity-method"></a>IManagedObject::GetObjectIdentity メソッド
この管理対象のオブジェクトの id を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetObjectIdentity (  
    [out] BSTR*   pBSTRGUID,  
    [out] int*    AppDomainID,  
    [out] CCW_PTR pCCW  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pBSTRGUID`  
 [out]オブジェクトが存在するプロセスの GUID へのポインター。  
  
 `AppDomainID`  
 [out]オブジェクトのアプリケーション ドメインの ID へのポインター。  
  
 `pCCW`  
 [out]V-table という COM クラシックでのオブジェクトのインデックスへのポインター。  
  
## <a name="remarks"></a>Remarks  
 マネージ オブジェクトの id には、v-table という COM クラシックでのプロセス GUID、アプリケーション ドメイン ID、およびオブジェクトのインデックスが含まれています。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IManagedObject インターフェイス](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
