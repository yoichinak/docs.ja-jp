---
title: IMetaDataAssemblyEmit::DefineExportedType メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineExportedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineExportedType
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineExportedType method [.NET Framework metadata]
- DefineExportedType method [.NET Framework metadata]
ms.assetid: fad01d7a-3178-4c8c-9f0a-4641e3701c9b
topic_type:
- apiref
ms.openlocfilehash: 44f97ef498eb8e64c55fc86b9f290b9e088293f6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432072"
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a>IMetaDataAssemblyEmit::DefineExportedType メソッド
指定してエクスポートした型のメタデータが含まれる `ExportedType` 構造体を作成し、関連付けられたメタデータ トークンを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DefineExportedType (  
    [in]  LPCWSTR             szName,  
    [in]  mdToken             tkImplementation,   
    [in]  mdTypeDef           tkTypeDef,  
    [in]  DWORD               dwExportedTypeFlags,  
    [out] mdExportedType      *pmdct  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `szName`  
 [in] The name of type to be exported. For version 1.1 of the common language runtime, the name of the exported type must exactly match the name given in the `TypeDef` for the type.  
  
 `tkImplementation`  
 [in] A token specifying where the exported type is implemented. The valid values and their associated meanings are:  
  
- `mdFile` The type is implemented in a different file within this assembly.  
  
- `mdAssemblyRef` The type is implemented in a different assembly.  
  
- `mdExportedTYpe` The type is nested within some other type.  
  
- `mdFileNil` The type is in the same file as the manifest and is not a nested type.  
  
 `tkTypeDef`  
 [in] A token to the metadata that specifies the type to be exported. This value is entered in the `TypeDef` table in the file that implements the type and is relevant only if that file is in this assembly.  
  
 `dwExportedTypeFlags`  
 [in] A bitwise combination of [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) enumeration values that define the property settings for the exported type.  
  
 `pmdct`  
 [out] A pointer to the returned metadata token that indicates the exported type.  
  
## <a name="remarks"></a>Remarks  
 An `ExportedType` metadata structure must be defined for each type that is exposed by this assembly and that is implemented in a module other than the one containing the manifest.  
  
## <a name="requirements"></a>［要件］  
 **Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** Cor.h  
  
 **Library:** Used as a resource in MsCorEE.dll  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataAssemblyEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
