---
title: IMetaDataAssemblyImport::FindAssembliesByName メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindAssembliesByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindAssembliesByName
helpviewer_keywords:
- FindAssembliesByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindAssembliesByName method [.NET Framework metadata]
ms.assetid: 4db97cf9-e4c1-4233-8efa-cbdc0e14a8e4
topic_type:
- apiref
ms.openlocfilehash: c12d3a7a7d1e52529435361aa12e22e4edeecf03
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448295"
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a>IMetaDataAssemblyImport::FindAssembliesByName メソッド
Gets an array of assemblies with the specified `szAssemblyName` parameter, using the standard rules employed by the common language runtime (CLR) for resolving references.  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT FindAssembliesByName (  
    [in]  LPCWSTR     szAppBase,   
    [in]  LPCWSTR     szPrivateBin,   
    [in]  LPCWSTR     szAssemblyName,   
    [out] IUnknown    *ppIUnk[],   
    [in]  ULONG       cMax,   
    [out] ULONG       *pcAssemblies  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `szAppBase`  
 [in] The root directory in which to search for the given assembly. If this value is set to `null`, `FindAssembliesByName` will look only in the global assembly cache for the assembly.  
  
 `szPrivateBin`  
 [in] A list of semicolon-delimited subdirectories (for example, "bin;bin2"), under the root directory, in which to search for the assembly. These directories are probed in addition to those specified in the default probing rules.  
  
 `szAssemblyName`  
 [in] The name of the assembly to find. The format of this string is defined in the class reference page for <xref:System.Reflection.AssemblyName>.  
  
 `ppIUnk`  
 [in] An array of type [IUnknown](/cpp/atl/iunknown) in which to put the `IMetadataAssemblyImport` interface pointers.  
  
 `cMax`  
 [out] The maximum number of interface pointers that can be placed in `ppIUnk`.  
  
 `pcAssemblies`  
 [out] The number of interface pointers returned. That is, the number of interface pointers actually placed in `ppIUnk`.  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|`S_OK`|`FindAssembliesByName` returned successfully.|  
|`S_FALSE`|There are no assemblies.|  
  
## <a name="remarks"></a>Remarks  
 Given an assembly name, the `FindAssembliesByName` method finds the assembly by following the standard rules for resolving assembly references. (For more information, see [How the Runtime Locates Assemblies](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` allows the caller to configure various aspects of the assembly resolver context, such as application base and private search path.  
  
 The `FindAssembliesByName` method requires the CLR to be initialized in the process in order to invoke the assembly resolution logic. Therefore, you must call [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (passing COINITEE_DEFAULT) before calling `FindAssembliesByName`, and then follow with a call to [CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).  
  
 `FindAssembliesByName` returns an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) pointer to the file containing the assembly manifest for the assembly name that is passed in. If the given assembly name is not fully specified (for example, if it does not include a version), multiple assemblies might be returned.  
  
 `FindAssembliesByName` is commonly used by a compiler that attempts to find a referenced assembly at compile time.  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **Header:** Cor.h  
  
 **Library:** Used as a resource in MsCorEE.dll  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ランタイムがアセンブリを検索する方法](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [IMetaDataAssemblyImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
