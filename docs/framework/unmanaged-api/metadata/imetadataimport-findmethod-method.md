---
title: IMetaDataImport::FindMethod メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMethod
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMethod
helpviewer_keywords:
- FindMethod method [.NET Framework metadata]
- IMetaDataImport::FindMethod method [.NET Framework metadata]
ms.assetid: 0f9bde1d-e306-438d-941b-d0925b322304
topic_type:
- apiref
ms.openlocfilehash: 470b6511366cef1680eaf97f9ab376736add55c4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437898"
---
# <a name="imetadataimportfindmethod-method"></a>IMetaDataImport::FindMethod メソッド
Gets a pointer to the MethodDef token for the method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT FindMethod (  
   [in]  mdTypeDef          td,  
   [in]  LPCWSTR            szName,   
   [in]  PCCOR_SIGNATURE    pvSigBlob,   
   [in]  ULONG              cbSigBlob,   
   [out] mdMethodDef        *pmb  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `td`  
 [in] The `mdTypeDef` token for the type (a class or interface) that encloses the member to search for. If this value is `mdTokenNil`, then the lookup is done for a global function.  
  
 `szName`  
 [in] The name of the method to search for.  
  
 `pvSigBlob`  
 [in] A pointer to the binary metadata signature of the method.  
  
 `cbSigBlob`  
 [in] The size in bytes of `pvSigBlob`.  
  
 `pmb`  
 [out] A pointer to the matching MethodDef token.  
  
## <a name="remarks"></a>Remarks  
 You specify the method using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`). There might be multiple methods with the same name in a class or interface. In that case, pass the method's signature to find the unique match.  
  
 The signature passed to `FindMethod` must have been generated in the current scope, because signatures are bound to a particular scope. A signature can embed a token that identifies the enclosing class or value type. The token is an index into the local TypeDef table. You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMethod`.  
  
 `FindMethod` finds only methods that were defined directly in the class or interface; it does not find inherited methods.  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **Header:** Cor.h  
  
 **Library:** Included as a resource in MsCorEE.dll  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Reflection.MethodInfo>
- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
