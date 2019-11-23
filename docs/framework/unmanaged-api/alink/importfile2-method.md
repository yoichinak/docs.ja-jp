---
title: ImportFile2 メソッド
ms.date: 03/30/2017
api_name:
- IALink.ImportFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFile2
helpviewer_keywords:
- ImportFile2 method
ms.assetid: 9a6be861-c260-4a35-acea-3372ea515a0f
topic_type:
- apiref
ms.openlocfilehash: 17f158167d4075783d1aa594fb61cc9e28d30dd7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446984"
---
# <a name="importfile2-method"></a>ImportFile2 メソッド
Imports assemblies and unbound modules. This method is like [ImportFile Method](importfile-method.md), but works even if the file being imported does not exist on disk.  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ImportFile2(  
    LPCWSTR         pszFilename,  
    LPCWSTR         pszTargetName,  
    IMetaDataAssemblyImport* pAssemblyScopeIn,  
    BOOL            fSmartImport,  
    mdToken*        pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD*          pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a>パラメーター  
 `pszFilename`  
 Name of file to be imported.  
  
 `pszTargetName`  
 Optional output file name that can be used to rename the file as it is linked into the assembly.  
  
 `pAssemblyScopeIn`  
 Optional scope [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.  
  
 `fSmartImport`  
 If TRUE, ImportTypes is used, otherwise importing must be performed manually.  
  
 `pImportToken`  
 Receives the ID for the file or assembly.  
  
 `ppAssemblyScope`  
 Receives the [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface. NULL if the file is not an assembly.  
  
 `pdwCountOfScopes`  
 Receives the found of files and/or scopes imported.  
  
## <a name="return-value"></a>戻り値  
 Returns S_OK if the method succeeds.  
  
## <a name="requirements"></a>［要件］  
 Requires alink.h.  
  
## <a name="see-also"></a>関連項目

- [IALink インターフェイス](ialink-interface.md)
- [IALink2 インターフェイス](ialink2-interface.md)
- [ALink API](index.md)
