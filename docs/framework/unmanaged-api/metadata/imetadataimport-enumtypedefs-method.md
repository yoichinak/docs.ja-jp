---
title: IMetaDataImport::EnumTypeDefs メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeDefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeDefs
helpviewer_keywords:
- EnumTypeDefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeDefs method [.NET Framework metadata]
ms.assetid: 4e508711-da92-4381-aaf8-6803075cdaa2
topic_type:
- apiref
ms.openlocfilehash: 3854cb4aa3d229c87466c0a35a72447ceb235624
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449995"
---
# <a name="imetadataimportenumtypedefs-method"></a>IMetaDataImport::EnumTypeDefs メソッド
現在のスコープ内のすべての型を表す TypeDef トークンを列挙します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnumTypeDefs (  
   [out] HCORENUM   *phEnum,   
   [in]  mdTypeDef  rTypeDefs[],  
   [in]  ULONG      cMax,   
   [out] ULONG      *pcTypeDefs  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `phEnum`  
 [out] A pointer to the new enumerator. This must be NULL for the first call of this method.  
  
 `rTypeDefs`  
 [in] The array used to store the TypeDef tokens.  
  
 `cMax`  
 [in] `rTypeDefs` 配列の最大サイズ。  
  
 `pcTypeDefs`  
 [out] The number of TypeDef tokens returned in `rTypeDefs`.  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|`S_OK`|`EnumTypeDefs` returned successfully.|  
|`S_FALSE`|There are no tokens to enumerate. In that case, `pcTypeDefs` is zero.|  
  
## <a name="remarks"></a>Remarks  
 The TypeDef token represents a type such as a class or an interface, as well as any type added via an extensibility mechanism.  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **Header:** Cor.h  
  
 **Library:** Included as a resource in MsCorEE.dll  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
