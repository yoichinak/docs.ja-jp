---
title: IMetaDataEmit::DefineTypeRefByName メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineTypeRefByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineTypeRefByName
helpviewer_keywords:
- DefineTypeRefByName method [.NET Framework metadata]
- IMetaDataEmit::DefineTypeRefByName method [.NET Framework metadata]
ms.assetid: c30a4ce3-2d3e-411a-98df-e62ac4a5dd50
topic_type:
- apiref
ms.openlocfilehash: 3dfdd473b01bfe83def52f957c52e0f4d11375ad
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434386"
---
# <a name="imetadataemitdefinetyperefbyname-method"></a>IMetaDataEmit::DefineTypeRefByName メソッド
Gets a metadata token for a type that is defined in the specified scope, which is outside the current scope.  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DefineTypeRefByName (   
    [in]  mdToken     tkResolutionScope,   
    [in]  LPCWSTR     szName,   
    [out] mdTypeRef   *ptr   
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `tkResolutionScope`  
 [in] The token specifying the resolution scope. The following token types are valid:  
  
- `mdModuleRef`, if the type is defined in the same assembly in which the caller is defined.  
  
- `mdAssemblyRef`, if the type is defined in an assembly other than the one in which the caller is defined.  
  
- `mdTypeRef`, if the type is a nested type.  
  
- `mdModule`, if the type is defined in the same module in which the caller is defined.  
  
- Null, if the type is defined globally.  
  
 `szName`  
 [in] The name of the target type in Unicode.  
  
 `ptr`  
 [out] A pointer to the `mdTypeRef` token that is assigned to the type.  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **Header:** Cor.h  
  
 **Library:** Used as a resource in MSCorEE.dll  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
