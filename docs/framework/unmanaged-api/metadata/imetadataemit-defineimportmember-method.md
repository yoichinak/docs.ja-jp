---
title: IMetaDataEmit::DefineImportMember メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineImportMember
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineImportMember
helpviewer_keywords:
- DefineImportMember method [.NET Framework metadata]
- IMetaDataEmit::DefineImportMember method [.NET Framework metadata]
ms.assetid: c7dd94c6-335b-46ff-9dfe-505056db5673
topic_type:
- apiref
ms.openlocfilehash: a7449ffc8a8ccf2db62ab3cff2f9cfaffd0c72a9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175864"
---
# <a name="imetadataemitdefineimportmember-method"></a>IMetaDataEmit::DefineImportMember メソッド
現在のスコープの外部で定義されている型またはモジュールの指定されたメンバーへの参照を作成し、その参照のトークンを定義します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DefineImportMember (
    [in]  IMetaDataAssemblyImport  *pAssemImport,
    [in]  const void               *pbHashValue,
    [in]  ULONG                    cbHashValue,  
    [in]  IMetaDataImport          *pImport,
    [in]  mdToken                  mbMember,
    [in]  IMetaDataAssemblyEmit    *pAssemEmit,
    [in]  mdToken                  tkParent,
    [out] mdMemberRef              *pmr
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pAssemImport`  
 [in]ターゲット メンバーのインポート元のアセンブリを表す[IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)インターフェイス。  
  
 `pbHashValue`  
 [in]で指定されたアセンブリのハッシュを格納する`pAssemImport`配列。  
  
 `cbHashValue`  
 [in] `pbHashValue` 配列のバイト数。  
  
 `pImport`  
 [in]ターゲット メンバーのインポート元のメタデータ スコープを表す[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)インターフェイス。  
  
 `mbMember`  
 [in]ターゲット メンバーを指定するメタデータ トークン。 トークンは`mdMethodDef`、(メンバー メソッドの場合)、(`mdProperty`メンバー プロパティの場合)、または`mdFieldDef`(メンバー フィールドの場合) トークンです。  
  
 `pAssemEmit`  
 [in]ターゲット メンバーのインポート先のアセンブリを表す[IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)インターフェイス。  
  
 `tkParent`  
 [in]`mdTypeRef`ターゲット メンバーを所有する型またはモジュールのトークンまたは`mdModuleRef`トークン。  
  
 `pmr`  
 [アウト]メンバー`mdMemberRef`参照の現在のスコープで定義されているトークン。  
  
## <a name="remarks"></a>解説  
 この`DefineImportMember`メソッドは、 で`mbMember`指定された別のスコープで定義されている メンバーを検索し`pImport`、そのプロパティを取得します。 この情報を使用して、現在のスコープの[IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md)メソッドを呼び出してメンバー参照を作成します。  
  
 通常、メソッドを`DefineImportMember`使用する前に、現在のスコープで、ターゲット メンバーの親クラス、インターフェイス、またはモジュールの型参照またはモジュール参照を作成する必要があります。 この参照のメタデータ トークンは`tkParent`、引数に渡されます。 後でコンパイラまたはリンカーによって解決される場合は、ターゲット メンバーの親への参照を作成する必要はありません。 まとめると次のようになります。  
  
- ターゲット メンバーがフィールドまたはメソッドの場合は[、IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md)または[IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)メソッドを使用して、メンバーの親クラスまたは親インターフェイスの型参照を現在のスコープ内に作成します。  
  
- 対象のメンバーがグローバル変数またはグローバル関数 (つまり、クラスまたはインターフェイスのメンバーではない) である場合は[、IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md)メソッドを使用して、メンバーの親モジュールの現在のスコープ内にモジュール参照を作成します。  
  
- ターゲット メンバーの親が後でコンパイラまたはリンカーによって解決される場合は、`mdTokenNil``tkParent`を渡します。 この場合、グローバル関数またはグローバル変数が .obj ファイルからインポートされ、最終的に現在のモジュールにリンクされ、メタデータがマージされる場合があります。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MSCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
