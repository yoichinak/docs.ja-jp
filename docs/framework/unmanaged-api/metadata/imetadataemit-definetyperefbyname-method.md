---
title: IMetaDataEmit::DefineTypeRefByName メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineTypeRefByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineTypeRefByName
helpviewer_keywords:
- DefineTypeRefByName method [.NET Framework metadata]
- IMetaDataEmit::DefineTypeRefByName method [.NET Framework metadata]
ms.assetid: c30a4ce3-2d3e-411a-98df-e62ac4a5dd50
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d93c55cec3d35fd4208a4a8a7c9b235dd10fb9ca
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59156170"
---
# <a name="imetadataemitdefinetyperefbyname-method"></a>IMetaDataEmit::DefineTypeRefByName メソッド
現在のスコープ外には、指定したスコープで定義されている型のメタデータ トークンを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT DefineTypeRefByName (   
    [in]  mdToken     tkResolutionScope,   
    [in]  LPCWSTR     szName,   
    [out] mdTypeRef   *ptr   
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `tkResolutionScope`  
 [in]解決スコープを指定するトークンです。 次のトークン型は有効です。  
  
-   `mdModuleRef`、呼び出し元が定義されている同じアセンブリで型が定義されている場合。  
  
-   `mdAssemblyRef`、呼び出し元が定義されているもの以外のアセンブリで型が定義されている場合。  
  
-   `mdTypeRef`、型が入れ子にされた型の場合。  
  
-   `mdModule`、、型が、呼び出し元が定義されている同じモジュールで定義されている場合。  
  
-   型がグローバルに定義されている場合は null です。  
  
 `szName`  
 [in]Unicode で対象の型の名前。  
  
 `ptr`  
 [out]ポインター、`mdTypeRef`型に割り当てられているトークンです。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして使用  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
