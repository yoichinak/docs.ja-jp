---
title: IMetaDataImport::FindMemberRef メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMemberRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMemberRef
helpviewer_keywords:
- IMetaDataImport::FindMemberRef method [.NET Framework metadata]
- FindMemberRef method [.NET Framework metadata]
ms.assetid: 1ccda329-d752-4d89-abe8-511af3c3f4c9
topic_type:
- apiref
ms.openlocfilehash: 59512cc1c1b280d7fe6deb2f9d721ad53547e356
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437959"
---
# <a name="imetadataimportfindmemberref-method"></a>IMetaDataImport::FindMemberRef メソッド
Gets a pointer to the MemberRef token for the member reference that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT FindMemberRef (  
   [in]  mdTypeRef          td,  
   [in]  LPCWSTR            szName,   
   [in]  PCCOR_SIGNATURE    pvSigBlob,   
   [in]  ULONG              cbSigBlob,   
   [out] mdMemberRef        *pmr  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `td`  
 [in] The TypeRef token for the class or interface that encloses the member reference to search for. If this value is `mdTokenNil`, the lookup is done for a global variable or a global-function reference.  
  
 `szName`  
 [in] The name of the member reference to search for.  
  
 `pvSigBlob`  
 [in] A pointer to the binary metadata signature of the member reference.  
  
 `cbSigBlob`  
 [in] The size in bytes of `pvSigBlob`.  
  
 `pmr`  
 [out] A pointer to the matching MemberRef token.  
  
## <a name="remarks"></a>Remarks  
 You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).  
  
 The signature passed to `FindMemberRef` must have been generated in the current scope, because signatures are bound to a particular scope. A signature can embed a token that identifies the enclosing class or value type. The token is an index into the local TypeDef table. You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindMemberRef`.  
  
 `FindMemberRef` finds only member references that were defined directly in the class or interface; it does not find inherited member references.  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **Header:** Cor.h  
  
 **Library:** Included as a resource in MsCorEE.dll  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
