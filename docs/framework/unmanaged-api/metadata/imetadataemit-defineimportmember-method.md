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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 341972629e18213536919fe53bfae94613b4d6e9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777634"
---
# <a name="imetadataemitdefineimportmember-method"></a>IMetaDataEmit::DefineImportMember メソッド
型または現在のスコープ外に定義され、その参照のトークンを定義するモジュールの指定されたメンバーへの参照を作成します。  
  
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
 [in][IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)対象メンバーのインポート元となるアセンブリを表すインターフェイスです。  
  
 `pbHashValue`  
 [in]指定されたアセンブリのハッシュを格納する配列`pAssemImport`します。  
  
 `cbHashValue`  
 [in] `pbHashValue` 配列のバイト数。  
  
 `pImport`  
 [in][IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)対象メンバーのインポート元のメタデータ スコープを表すインターフェイスです。  
  
 `mbMember`  
 [in]ターゲット メンバーを指定するメタデータ トークンです。 トークンを指定できます、 `mdMethodDef` (メンバー メソッドの場合) の`mdProperty`(のメンバー プロパティの場合) または`mdFieldDef`(メンバー フィールド) のトークン。  
  
 `pAssemEmit`  
 [in][IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)対象メンバーのインポート先のアセンブリを表すインターフェイスです。  
  
 `tkParent`  
 [in]`mdTypeRef`または`mdModuleRef`型またはモジュールのトークンを所有する対象のメンバー。  
  
 `pmr`  
 [out]`mdMemberRef`メンバー参照の現在のスコープで定義されているトークンです。  
  
## <a name="remarks"></a>Remarks  
 `DefineImportMember`メソッドで指定されたメンバーを検索`mbMember`がで指定された別のスコープで定義されている`pImport`、そのプロパティを取得します。 呼び出しにこの情報を使用して、 [imetadataemit::definememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md)メンバー参照を作成する現在のスコープ内のメソッド。  
  
 使用する前に、一般に、`DefineImportMember`メソッドを作成する必要が、現在のスコープは、型参照またはターゲット メンバーの親クラス、インターフェイス、またはモジュールのモジュール参照。 この参照のメタデータ トークンが渡されたし、`tkParent`引数。 コンパイラまたはリンカーによって後で解決する場合は、ターゲット メンバーの親への参照を作成する必要はありません。 まとめ  
  
- 対象のメンバーがフィールドまたはメソッドの場合は、いずれかを使用、 [imetadataemit::definetyperefbyname](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md)または[imetadataemit::defineimporttype](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)の現在のスコープ内の型参照を作成する方法、メンバーの親クラスまたはインターフェイスの親。  
  
- グローバル変数またはグローバル関数 (つまり、いないメンバー クラスまたはインターフェイスの) の場合は、対象のメンバーを使用して、 [imetadataemit::definemoduleref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md)メソッド メンバーの親の現在のスコープ内のモジュール参照を作成するにはモジュール。  
  
- ターゲット メンバーの親はコンパイラまたはリンカーで後で解決される、その渡す`mdTokenNil`で`tkParent`します。 これが適用される唯一のシナリオは、グローバル関数またはグローバル変数が最終的には、現在のモジュールにリンクされる .obj ファイルからインポートされると、メタデータのマージします。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして使用  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
