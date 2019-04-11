---
title: IMetaDataEmit::DefineImportType メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineImportType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineImportType
helpviewer_keywords:
- DefineImportType method [.NET Framework metadata]
- IMetaDataEmit::DefineImportType method [.NET Framework metadata]
ms.assetid: 37fd27af-8062-4904-ace4-51bb78ec600a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c9debf041a26af128dea3cde214630f5a95eac71
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59090661"
---
# <a name="imetadataemitdefineimporttype-method"></a>IMetaDataEmit::DefineImportType メソッド
現在のスコープ外に定義され、その参照のトークンを定義する指定した型への参照を作成します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT DefineImportType (   
    [in]  IMetaDataAssemblyImport  *pAssemImport,   
    [in]  const void               *pbHashValue,   
    [in]  ULONG                    cbHashValue,    
    [in]  IMetaDataImport          *pImport,   
    [in]  mdTypeDef                tdImport,   
    [in]  IMetaDataAssemblyEmit    *pAssemEmit,   
    [out] mdTypeRef                *ptr  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pAssemImport`  
 [in][IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)ターゲットの種類のインポート元となるアセンブリを表すインターフェイスです。  
  
 `pbHashValue`  
 [in]指定されたアセンブリのハッシュを格納する配列`pAssemImport`します。  
  
 `cbHashValue`  
 [in] `pbHashValue` 配列のバイト数。  
  
 `pImport`  
 [in][IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)ターゲットの種類のインポート元のメタデータ スコープを表すインターフェイスです。  
  
 `tdImport`  
 [in]`mdTypeDef`対象の型を示すトークン。  
  
 `pAssemEmit`  
 [in][IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)ターゲットの種類のインポート先のアセンブリを表すインターフェイスです。  
  
 `ptr`  
 [out]`mdTypeRef`型参照の現在のスコープで定義されているトークンです。  
  
## <a name="remarks"></a>Remarks  
 呼び出しの前に、 [imetadataemit::defineimportmember](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md)メソッドが使用できる、`DefineImportType`メンバーの親クラスまたは親インターフェイスの現在のスコープ内の型の参照を作成します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして使用  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
