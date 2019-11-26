---
title: IMetaDataImport::ResolveTypeRef メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.ResolveTypeRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::ResolveTypeRef
helpviewer_keywords:
- ResolveTypeRef method [.NET Framework metadata]
- IMetaDataImport::ResolveTypeRef method [.NET Framework metadata]
ms.assetid: 556bccfb-61bc-4761-b1d5-de4b1c18a38f
topic_type:
- apiref
ms.openlocfilehash: 800b15bb75e74898cee9d838900ea14b60620940
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431475"
---
# <a name="imetadataimportresolvetyperef-method"></a>IMetaDataImport::ResolveTypeRef メソッド
Resolves a <xref:System.Type> reference represented by the specified TypeRef token.  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ResolveTypeRef (  
   [in]  mdTypeRef       tr,  
   [in]  REFIID          riid,  
   [out] IUnknown        **ppIScope,  
   [out] mdTypeDef       *ptd  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `tr`  
 [in] The TypeRef metadata token to return the referenced type information for.  
  
 `riid`  
 [in] The IID of the interface to return in `ppIScope`. Typically, this would be IID_IMetaDataImport.  
  
 `ppIScope`  
 [out] An interface to the module scope in which the referenced type is defined.  
  
 `ptd`  
 [out] A pointer to a TypeDef token that represents the referenced type.  
  
## <a name="remarks"></a>Remarks  
  
> [!IMPORTANT]
> Do not use this method if multiple application domains are loaded. The method does not respect application domain boundaries. If multiple versions of an assembly are loaded, and they contain the same type with the same namespace, the method returns the module scope of the first type it finds.  
  
 The `ResolveTypeRef` method searches for the type definition in other modules. If the type definition is found, `ResolveTypeRef` returns an interface to that module scope as well as the TypeDef token for the type.  
  
 If the type reference to be resolved has a resolution scope of AssemblyRef, the `ResolveTypeRef` method searches for a match only in the metadata scopes that have already been opened with calls to either the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method or the [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) method. This is because `ResolveTypeRef` cannot determine from only the AssemblyRef scope where on disk or in the global assembly cache the assembly is stored.  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **Header:** Cor.h  
  
 **Library:** Included as a resource in MsCorEE.dll  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
