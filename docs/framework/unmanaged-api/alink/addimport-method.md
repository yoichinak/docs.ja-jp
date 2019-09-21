---
title: AddImport メソッド
ms.date: 03/30/2017
api_name:
- AddImport
- IALink.AddImport
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddImport
helpviewer_keywords:
- AddImport method
ms.assetid: 4fedf8a0-08c8-43d0-aa00-20f2a521c991
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aed70a78e2513f4d63fbf8ca8868f26efbac9ae8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787655"
---
# <a name="addimport-method"></a>AddImport メソッド
アセンブリにインポートを追加します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT AddImport(  
    mdAssembly      AssemblyID,  
    mdToken         ImportToken,  
    DWORD           dwFlags,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a>パラメーター  
 `AssemblyID`  
 補強するアセンブリの一意の ID。  
  
 `ImportToken`  
 インポートするファイルの[Importfile メソッド](importfile-method.md)から取得された一意の ID。  
  
 `dwFlags`  
 `ffContainsNoMetaData` や`ffWriteable`などの com + filedef フラグ。 `dwFlags`は、[メソッド](../metadata/imetadataassemblyemit-definefile-method.md)に渡されます。  
  
 `pFileToken`  
 結果ファイルの ID を受け取るトークンへのポインター。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合、S_OK を返します。  
  
## <a name="requirements"></a>必要条件  
 Alink. h が必要です。  
  
## <a name="see-also"></a>関連項目

- [IALink インターフェイス](ialink-interface.md)
- [IALink2 インターフェイス](ialink2-interface.md)
- [ALink API](index.md)
