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
ms.openlocfilehash: 6825a5198976cc7ab2c04ebd6e782418dcf4a8f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177677"
---
# <a name="imetadataemitdefineimporttype-method"></a>IMetaDataEmit::DefineImportType メソッド
現在のスコープの外部で定義されている指定した型への参照を作成し、その参照のトークンを定義します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
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
 [in]ターゲット型のインポート元のアセンブリを表す[IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)インターフェイス。  
  
 `pbHashValue`  
 [in]で指定されたアセンブリのハッシュを格納する`pAssemImport`配列。  
  
 `cbHashValue`  
 [in] `pbHashValue` 配列のバイト数。  
  
 `pImport`  
 [in]ターゲット型のインポート元のメタデータ スコープを表す[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)インターフェイス。  
  
 `tdImport`  
 [in]ターゲット`mdTypeDef`の型を指定するトークン。  
  
 `pAssemEmit`  
 [in]ターゲット型のインポート先のアセンブリを表す[IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)インターフェイス。  
  
 `ptr`  
 [アウト]型`mdTypeRef`参照の現在のスコープで定義されているトークン。  
  
## <a name="remarks"></a>解説  
 [:D メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md)を呼び出す前に、`DefineImportType`メソッドを使用して、メンバーの親クラスまたは親インターフェイスの現在のスコープ内の型参照を作成できます。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MSCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
