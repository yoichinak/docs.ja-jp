---
title: IMetaDataImport::FindMember メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMember
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMember
helpviewer_keywords:
- IMetaDataImport::FindMember method [.NET Framework metadata]
- FindMember method [.NET Framework metadata]
ms.assetid: ad32fb84-c2b6-41cd-888d-787ff3a90449
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 777d7bf51db3e6984f30e31c46ac115301d13faf
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478974"
---
# <a name="imetadataimportfindmember-method"></a>IMetaDataImport::FindMember メソッド
フィールドまたは囲まれたメソッドの memberdef にポインターをトークン取得を指定した<xref:System.Type>指定した名前とメタデータ シグネチャを持つとします。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT FindMember (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,   
   [in]  PCCOR_SIGNATURE   pvSigBlob,   
   [in]  ULONG             cbSigBlob,   
   [out] mdToken           *pmb  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `td`  
 [in]クラスまたはインターフェイスを検索するメンバーを囲む TypeDef トークンです。 この値が場合`mdTokenNil`、グローバル変数またはグローバル関数、検索を実行します。  
  
 `szName`  
 [in]検索するメンバーの名前。  
  
 `pvSigBlob`  
 [in]メンバーのバイナリ メタデータ シグネチャへのポインター。  
  
 `cbSigBlob`  
 [in]バイト サイズ`pvSigBlob`します。  
  
 `pmb`  
 [out]一致する MemberDef トークンへのポインター。  
  
## <a name="remarks"></a>Remarks  
 外側のクラスまたはインターフェイスを使用してメンバーを指定する (`td`)、その名前 (`szName`)、および必要に応じてその署名 (`pvSigBlob`)。 クラスまたはインターフェイスで同じ名前の複数のメンバーである可能性があります。 その場合は、一意の一致を検索するメンバーのシグネチャを渡します。  
  
 渡される署名`FindMember`生成された現在のスコープで特定のスコープにバインドされるためです。 署名は、外側のクラスまたは値の型を識別するトークンを埋め込むことができます。 トークンは、ローカルの TypeDef テーブルへのインデックスです。 現在のスコープのコンテキスト外にある実行時シグネチャを作成してを入力としてその署名を使用することはできません`FindMember`します。  
  
 `FindMember` クラスまたはインターフェイス内で直接定義されたメンバーのみを検索します継承されたメンバーは検索しません。  
  
> [!NOTE]
>  `FindMember` ヘルパー メソッドです。 呼び出す[imetadataimport::findmethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md)その呼び出しには、一致が見つからない場合は`FindMember`呼び出して[imetadataimport::findfield](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md)します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
