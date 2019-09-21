---
title: ImportFileEx2 メソッド
ms.date: 03/30/2017
api_name:
- IALink2.ImportFileEx2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFileEx2
helpviewer_keywords:
- ImportFileEx2 method
ms.assetid: 02c789fd-16fc-48c6-9619-56e87e2a37ca
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a1c950e9a6e53e04cc0f2e52a140612562b32ff1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776983"
---
# <a name="importfileex2-method"></a>ImportFileEx2 メソッド
アセンブリとバインドされていないモジュールをインポートします。 このメソッドは[Importfile メソッド](importfile-method.md)に似ていますが、インポートされるファイルがディスク上に存在しない場合でも機能します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ImportFileEx2(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    IMetaDataAssemblyImport* pAssemblyScopeIn,  
    BOOL fSmartImport,  
    DWORD dwOpenFlags,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a>パラメーター  
 `pszFilename`  
 インポートするファイルの名前。  
  
 `pszTargetName`  
 ターゲットファイルの名前 (省略可能)。  
  
 `pAssemblyScopeIn`  
 省略可能なインポートスコープ[IMetaDataAssemblyImport インターフェイス](../metadata/imetadataassemblyimport-interface.md)インターフェイス。  
  
 `fSmartImport`  
 TRUE の場合、ImportTypes が使用されます。それ以外の場合は、インポートを手動で実行する必要があります。  
  
 `dwOpenFlags`  
 [Openscope メソッド](../metadata/imetadatadispenser-openscope-method.md)に渡されるフラグ。  
  
 `pImportToken`  
 アセンブリまたはファイルの一意の ID を受け取ります。  
  
 `ppAssemblyScope`  
 アセンブリインポートスコープ[IMetaDataAssemblyImport インターフェイス](../metadata/imetadataassemblyimport-interface.md)インターフェイスを受け取ります。 ファイルがアセンブリでない場合は NULL を指定できます。  
  
 `pdwCountOfScopes`  
 インポートされたファイルまたはスコープの数を受け取ります。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合、S_OK を返します。  
  
## <a name="requirements"></a>必要条件  
 Alink. h が必要です。  
  
## <a name="see-also"></a>関連項目

- [IALink2 インターフェイス](ialink2-interface.md)
- [IALink インターフェイス](ialink-interface.md)
- [ALink API](index.md)
