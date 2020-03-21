---
title: IMetaDataAssemblyImport::EnumExportedTypes メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumExportedTypes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumExportedTypes
helpviewer_keywords:
- EnumExportedTypes method [.NET Framework metadata]
- IMetaDataAssemblyImport::EnumExportedTypes method [.NET Framework metadata]
ms.assetid: e5912ed8-e4ce-438b-8ea3-d9e4c288d109
topic_type:
- apiref
ms.openlocfilehash: f00fe5bce2f808265add228406dfaa2ccc267545
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176007"
---
# <a name="imetadataassemblyimportenumexportedtypes-method"></a>IMetaDataAssemblyImport::EnumExportedTypes メソッド
現在のメタデータ スコープ内のアセンブリ マニフェストで参照されるエクスポートされた型を列挙します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnumExportedTypes (  
    [in, out] HCORENUM     *phEnum,
    [out] mdExportedType   rExportedTypes[],
    [in]  ULONG            cMax,
    [out] ULONG            *pcTokens  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `phEnum`  
 [イン、アウト]列挙子へのポインター。 メソッドが初めて呼び出されたとき`EnumExportedTypes`は、この値は NULL 値である必要があります。  
  
 `rExportedTypes`  
 [アウト]メタデータ トークン`mdExportedType`の列挙体。  
  
 `cMax`  
 [in]配列に配置できる`mdExportedType`トークンの最大数。 `rExportedTypes`  
  
 `pcTokens`  
 [アウト]に実際に`mdExportedType`配置されたトークンの`rExportedTypes`数。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|`S_OK`|`EnumExportedTypes`正常に返されました。|  
|`S_FALSE`|列挙するトークンがありません。 この場合、`pcTokens`ゼロに設定されます。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[「システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataAssemblyImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
