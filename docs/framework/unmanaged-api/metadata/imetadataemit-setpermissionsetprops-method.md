---
title: IMetaDataEmit::SetPermissionSetProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPermissionSetProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPermissionSetProps
helpviewer_keywords:
- SetPermissionSetProps method [.NET Framework metadata]
- IMetaDataEmit::SetPermissionSetProps method [.NET Framework metadata]
ms.assetid: 8eaee971-40bf-45e2-a3d8-6e57674213b6
topic_type:
- apiref
ms.openlocfilehash: de4cfdf2a9353eebdebaf4df9e481d06d776ff04
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177485"
---
# <a name="imetadataemitsetpermissionsetprops-method"></a>IMetaDataEmit::SetPermissionSetProps メソッド
以前の呼び出しで定義されたアクセス許可セットのメタデータ シグネチャ[:Dの](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md)機能を設定または更新します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetPermissionSetProps (
    [in]  mdToken         tk,
    [in]  DWORD           dwAction,
    [in]  void const      *pvPermission,
    [in]  ULONG           cbPermission,
    [out] mdPermission    *ppm
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `tk`  
 [in]装飾されるオブジェクトを表すメタデータ トークン。  
  
 `dwAction`  
 [in]使用する宣言セキュリティの種類を指定する[CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md)値。  
  
 `pvPermission`  
 [in]アクセス許可 BLOB。  
  
 `cbPermission`  
 [in]のサイズ (バイト単位)`pvPermission`です。  
  
 `ppm`  
 [アウト]更新`mdPermission`されたアクセス許可を表すメタデータ トークン。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MSCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
