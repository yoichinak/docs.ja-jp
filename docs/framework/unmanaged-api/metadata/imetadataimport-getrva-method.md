---
title: IMetaDataImport::GetRVA メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetRVA
helpviewer_keywords:
- GetRVA method [.NET Framework metadata]
- IMetaDataImport::GetRVA method [.NET Framework metadata]
ms.assetid: ea422217-988b-4acd-b2db-c55357938275
topic_type:
- apiref
ms.openlocfilehash: a3a5cadc1b5a9df7967aae271ff10296843121dd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436963"
---
# <a name="imetadataimportgetrva-method"></a>IMetaDataImport::GetRVA メソッド
Gets the relative virtual address (RVA) and the implementation flags of the method or field represented by the specified token.  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetRVA (  
   [in]  mdToken     tk,   
   [out] ULONG       *pulCodeRVA,   
   [out]  DWORD      *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `tk`  
 [in] A MethodDef or FieldDef metadata token that represents the code object to return the RVA for. If the token is a FieldDef, the field must be a global variable.  
  
 `pulCodeRVA`  
 [out] A pointer to the relative virtual address of the code object represented by the token.  
  
 `pdwImplFlags`  
 [out] A pointer to the implementation flags for the method. This value is a bitmask from the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration. The value of `pdwImplFlags` is valid only if `tk` is a MethodDef token.  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **Header:** Cor.h  
  
 **Library:** Included as a resource in MsCorEE.dll  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
