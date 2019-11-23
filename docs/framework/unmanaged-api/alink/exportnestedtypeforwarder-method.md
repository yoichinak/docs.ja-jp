---
title: ExportNestedTypeForwarder メソッド
ms.date: 03/30/2017
api_name:
- IALink.ExportNestedTypeForwarder
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportNestedTypeForwarder
helpviewer_keywords:
- ExportNestedTypeForwarder method
ms.assetid: 886ea6c5-6b26-4b88-8bf6-448d6d191950
topic_type:
- apiref
ms.openlocfilehash: cc81ccd1c754e3d34c54737f4560b4f81d5cc916
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438417"
---
# <a name="exportnestedtypeforwarder-method"></a>ExportNestedTypeForwarder メソッド
Adds a type forwarder for a nested type to the type table of the given assembly.  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ExportNestedTypeForwarder(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    mdExportedType  ParentType,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a>パラメーター  
 `AssemblyID`  
 ID of the assembly to export from.  
  
 `FileToken`  
 File token or assembly ID of file that defines the type.  
  
 `TypeToken`  
 Token for the type.  
  
 `ParentType`  
 Token of parent type.  
  
 `pszTypename`  
 Fully qualified type name to export.  
  
 `dwFlags`  
 `ComType` flags such as `tdPublic` or `tdNested`.  
  
 `pType`  
 Receives token of export type. This is necessary only for emitting nested types.  
  
## <a name="return-value"></a>戻り値  
 Returns S_OK if the method succeeds.  
  
## <a name="requirements"></a>［要件］  
 Requires alink.h  
  
## <a name="see-also"></a>関連項目

- [IALink インターフェイス](ialink-interface.md)
- [IALink2 インターフェイス](ialink2-interface.md)
- [ALink API](index.md)
