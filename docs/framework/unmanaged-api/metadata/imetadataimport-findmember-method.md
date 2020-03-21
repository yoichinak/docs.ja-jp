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
ms.openlocfilehash: dab155b82d87609b3d3f390133e6490502a43518
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177279"
---
# <a name="imetadataimportfindmember-method"></a>IMetaDataImport::FindMember メソッド
指定した名前とメタデータ シグネチャを持つフィールドまたはメソッドの MemberDef<xref:System.Type>トークンへのポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
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
 [in]検索するメンバーを囲むクラスまたはインターフェイスの TypeDef トークン。 この値が`mdTokenNil`の場合、グローバル変数またはグローバル関数の検索が行われます。  
  
 `szName`  
 [in]検索するメンバーの名前。  
  
 `pvSigBlob`  
 [in]メンバーのバイナリ メタデータ シグネチャへのポインター。  
  
 `cbSigBlob`  
 [in]のサイズ (バイト`pvSigBlob`単位)  
  
 `pmb`  
 [アウト]一致する MemberDef トークンへのポインター。  
  
## <a name="remarks"></a>解説  
 メンバーを指定するには、外側のクラスまたはインターフェイス (`td`) 、`szName`その名前 ( )`pvSigBlob`、およびオプションでそのシグネチャ ( ) を使用します。 クラスまたはインターフェイス内に同じ名前のメンバーが複数存在する場合があります。 その場合は、メンバーの署名を渡して一意の一致を見つけます。  
  
 渡された署名は`FindMember`、特定のスコープにバインドされているため、現在のスコープで生成されている必要があります。 シグネチャは、外側のクラスまたは値の型を識別するトークンを埋め込むことができます。 トークンは、ローカルの TypeDef テーブルへのインデックスです。 現在のスコープのコンテキストの外部でランタイム シグネチャを作成し、そのシグネチャを`FindMember`入力として使用することはできません。  
  
 `FindMember`は、クラスまたはインターフェイスで直接定義されたメンバーのみを検索します。継承されたメンバーは見つかりません。  
  
> [!NOTE]
> `FindMember`はヘルパー メソッドです。 を呼[び](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md)出します。その呼び出しが一致を`FindMember`見つけられない場合は[、IMetaDataImport::FindField](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md)を呼び出します。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれる  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
