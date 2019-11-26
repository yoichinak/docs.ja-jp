---
title: IMetaDataEmit::DefineField メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineField
helpviewer_keywords:
- IMetaDataEmit::DefineField method [.NET Framework metadata]
- DefineField method, IMetaDataEmit interface [.NET Framework metadata
ms.assetid: 6b5be4fc-2e86-499c-8b09-833160bca767
topic_type:
- apiref
ms.openlocfilehash: 40f24a4ea628ce92a27ab1bfe97fc87a57dfa4f0
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432548"
---
# <a name="imetadataemitdefinefield-method"></a>IMetaDataEmit::DefineField メソッド
Creates a definition for a field with the specified metadata signature, and gets a token to that field definition.  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DefineField (   
    [in]  mdTypeDef   td,   
    [in]  LPCWSTR     szName,   
    [in]  DWORD       dwFieldFlags,   
    [in]  PCCOR_SIGNATURE pvSigBlob,   
    [in]  ULONG       cbSigBlob,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,   
    [in]  ULONG       cchValue,   
    [out] mdFieldDef  *pmd   
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `td`  
 [in] The `mdTypeDef` token for the enclosing class or interface.  
  
 `szName`  
 [in] The field name in Unicode.  
  
 `dwFieldFlags`  
 [in] The field attributes. This is a bitmask of `CorFieldAttr` values.  
  
 `pvSigBlob`  
 [in] The field signature as a BLOB.  
  
 `cbSigBlob`  
 [in] The count of bytes in `pvSigBlob`.  
  
 `dwCPlusTypeFlag`  
 [in] The `ELEMENT_TYPE_` *\** for the constant value. This is a `CorElementType` value. If not defining a constant value for the field, use `ELEMENT_TYPE_END`.  
  
 `pValue`  
 [in] The constant value for the field.  
  
 `cchValue`  
 [in] The size in (Unicode) characters of `pValue`.  
  
 `pmd`  
 [out] The `mdFieldDef` token assigned.  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **Header:** Cor.h  
  
 **Library:** Used as a resource in MSCorEE.dll  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
