---
title: IMetaDataAssemblyEmit::SetAssemblyRefProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetAssemblyRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetAssemblyRefProps
helpviewer_keywords:
- SetAssemblyRefProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 70a32bf3-9051-4f96-ae87-11356d06a073
topic_type:
- apiref
ms.openlocfilehash: 5434aa2d12bd9a29a8c2fc784421442469ceb1ce
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440555"
---
# <a name="imetadataassemblyemitsetassemblyrefprops-method"></a>IMetaDataAssemblyEmit::SetAssemblyRefProps メソッド
指定された `AssemblyRef` メタデータ構造体を変更します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetAssemblyRefProps (  
    [in] mdAssemblyRef              ar,  
    [in] const void                 *pbPublicKeyOrToken,  
    [in] ULONG                      cbPublicKeyOrToken,  
    [in] LPCWSTR                    szName,   
    [in] const ASSEMBLYMETADATA     *pMetaData,   
    [in] const void                 *pbHashValue,  
    [in] ULONG                      cbHashValue,  
    [in] DWORD                      dwAssemblyRefFlags  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `ar`  
 [in] The metadata token that specifies the `AssemblyRef` metadata structure to be modified.  
  
 `pbPublicKeyOrToken`  
 [in] The public key of the publisher of the referenced assembly.  
  
 `cbPublicKeyOrToken`  
 [in] The size in bytes of `pbPublicKeyOrToken`.  
  
 `szName`  
 [in] The human-readable text name of the assembly.  
  
 `pMetaData`  
 [in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.  
  
 `pbHashValue`  
 [in] A pointer to the hash data associated with the assembly.  
  
 `cbHashValue`  
 [in] The size in bytes of `pbHashValue`.  
  
 `dwAssemblyRefFlags`  
 [in] A bitwise combination of [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) values that specify attributes of the referenced assembly.  
  
## <a name="remarks"></a>Remarks  
 To create an `AssemblyRef` metadata structure, use the [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md) method.  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **Header:** Cor.h  
  
 **Library:** Used as a resource in MsCorEE.dll  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataAssemblyEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
