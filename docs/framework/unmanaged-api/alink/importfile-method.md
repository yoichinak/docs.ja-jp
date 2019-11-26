---
title: ImportFile メソッド
ms.date: 03/30/2017
api_name:
- IALink.ImportFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFile
helpviewer_keywords:
- ImportFile method
ms.assetid: bcbe321f-b83a-4e9a-9f10-8d913e244dc9
topic_type:
- apiref
ms.openlocfilehash: cda6d90865f8ad2b9d565f6a6378c35b03c65bf7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446994"
---
# <a name="importfile-method"></a>ImportFile メソッド
Imports assemblies and unbound modules.  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ImportFile(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a>パラメーター  
 `pszFilename`  
 Fully qualified name of file to be imported.  
  
 `pszTargetName`  
 Optional output file name that can be used to rename the file as it is linked into the assembly.  
  
 `fSmartImport`  
 If TRUE, ImportTypes is used, otherwise importing must be performed manually.  
  
 `pImportToken`  
 Pointer to token where a unique file ID will be stored. The file can be an assembly or a file.  
  
 `ppAssemblyScope`  
 Receives pointer to [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md). Can be NULL if the file is not an assembly.  
  
 `pdwCountOfScopes`  
 Pointer to the count of files and/or scopes that have been imported.  
  
## <a name="return-value"></a>戻り値  
 Returns S_OK if the method succeeds.  
  
## <a name="requirements"></a>［要件］  
 Requires alink.h  
  
## <a name="see-also"></a>関連項目

- [IALink インターフェイス](ialink-interface.md)
- [IALink2 インターフェイス](ialink2-interface.md)
- [ALink API](index.md)
