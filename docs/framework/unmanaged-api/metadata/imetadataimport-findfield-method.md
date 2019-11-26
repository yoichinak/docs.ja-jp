---
title: IMetaDataImport::FindField メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindField
helpviewer_keywords:
- IMetaDataImport::FindField method [.NET Framework metadata]
- FindField method [.NET Framework metadata]
ms.assetid: 38cd4e16-fbb2-471c-aa73-ac51a1931ad2
topic_type:
- apiref
ms.openlocfilehash: 842d6c0deb90bc45cb59454fb30fcc3544d742f1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437941"
---
# <a name="imetadataimportfindfield-method"></a>IMetaDataImport::FindField メソッド
Gets a pointer to the FieldDef token for the field that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT FindField (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,  
   [in]  PCCOR_SIGNATURE   pvSigBlob,  
   [in]  ULONG             cbSigBlob,  
   [out] mdFieldDef        *pmb  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `td`  
 [in] The TypeDef token for the class or interface that encloses the field to search for. If this value is `mdTokenNil`, the lookup is done for a global variable.  
  
 `szName`  
 [in] The name of the field to search for.  
  
 `pvSigBlob`  
 [in] A pointer to the binary metadata signature of the field.  
  
 `cbSigBlob`  
 [in] The size in bytes of `pvSigBlob`.  
  
 `pmb`  
 [out] A pointer to the matching FieldDef token.  
  
## <a name="remarks"></a>Remarks  
 You specify the field using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).  
  
 The signature passed to `FindField` must have been generated in the current scope, because signatures are bound to a particular scope. A signature can embed a token that identifies the enclosing class or value type. (The token is an index into the local TypeDef table). You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindField`.  
  
 `FindField` finds only fields that were defined directly in the class or interface; it does not find inherited fields.  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **Header:** Cor.h  
  
 **Library:** Included as a resource in MsCorEE.dll  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
