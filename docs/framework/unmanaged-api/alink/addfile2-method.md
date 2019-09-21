---
title: AddFile2 メソッド
ms.date: 03/30/2017
api_name:
- AddFile2
- IALink2.AddFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddFile2
helpviewer_keywords:
- AddFile2 method
ms.assetid: 03bc49bf-a89b-4fb6-a88d-97482e061195
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c3a6892dbed172c0be3b036014d393657dbc8593
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777521"
---
# <a name="addfile2-method"></a>AddFile2 メソッド
アセンブリにファイルを追加します。 は、バインドされていないモジュールを作成するためにも使用できます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT AddFile2(  
    mdAssembly AssemblyID,  
    LPCWSTR pszFilename,  
    DWORD dwFlags,  
    IMetaDataEmit2* pEmitter,  
    mdFile* pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a>パラメーター  
 `AssemblyID`  
 ファイルが追加されるアセンブリの ID。  
  
 `pszFilename`  
 追加するファイルの名前。  
  
 `dwFlags`  
 Com `FileDef` + フラグ ( `ffContainsNoMetaData`や`ffWriteable`など)。 `dwFlags`は、[メソッド](../metadata/imetadataassemblyemit-definefile-method.md)に渡されます。  
  
 `pEmitter`  
 [IMetaDataEmit2 インターフェイス](../metadata/imetadataemit2-interface.md)インターフェイスへのインターフェイス。  
  
 `pFileToken`  
 追加するファイルの ID を受け取ります。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合、S_OK を返します。  
  
## <a name="requirements"></a>必要条件  
 Alink. h が必要です。  
  
## <a name="see-also"></a>関連項目

- [IALink2 インターフェイス](ialink2-interface.md)
- [IALink インターフェイス](ialink-interface.md)
- [ALink API](index.md)
