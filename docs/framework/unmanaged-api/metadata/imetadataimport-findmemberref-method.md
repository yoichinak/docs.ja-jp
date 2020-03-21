---
title: IMetaDataImport::FindMemberRef メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMemberRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMemberRef
helpviewer_keywords:
- IMetaDataImport::FindMemberRef method [.NET Framework metadata]
- FindMemberRef method [.NET Framework metadata]
ms.assetid: 1ccda329-d752-4d89-abe8-511af3c3f4c9
topic_type:
- apiref
ms.openlocfilehash: d8b8bfd0e70e75c702f32555c10f433a1ff4ae10
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175422"
---
# <a name="imetadataimportfindmemberref-method"></a>IMetaDataImport::FindMemberRef メソッド
指定した名前とメタデータ シグネチャを持つメンバー参照の MemberRef トークン<xref:System.Type>へのポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT FindMemberRef (  
   [in]  mdTypeRef          td,  
   [in]  LPCWSTR            szName,
   [in]  PCCOR_SIGNATURE    pvSigBlob,
   [in]  ULONG              cbSigBlob,
   [out] mdMemberRef        *pmr  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `td`  
 [in]検索するメンバー参照を囲むクラスまたはインターフェイスの TypeRef トークン。 この値が`mdTokenNil`の場合、グローバル変数またはグローバル関数参照の検索が行われます。  
  
 `szName`  
 [in]検索するメンバー参照の名前。  
  
 `pvSigBlob`  
 [in]メンバー参照のバイナリ メタデータ シグネチャへのポインター。  
  
 `cbSigBlob`  
 [in]のサイズ (バイト`pvSigBlob`単位)  
  
 `pmr`  
 [アウト]一致する MemberRef トークンへのポインター。  
  
## <a name="remarks"></a>解説  
 メンバーを指定するには、外側のクラスまたはインターフェイス (`td`) 、`szName`その名前 ( )`pvSigBlob`、およびオプションでそのシグネチャ ( ) を使用します。  
  
 渡された署名は`FindMemberRef`、特定のスコープにバインドされているため、現在のスコープで生成されている必要があります。 シグネチャは、外側のクラスまたは値の型を識別するトークンを埋め込むことができます。 トークンは、ローカルの TypeDef テーブルへのインデックスです。 現在のスコープのコンテキストの外部でランタイム シグネチャを作成し、そのシグネチャを への`FindMemberRef`入力として使用することはできません。  
  
 `FindMemberRef`は、クラスまたはインターフェイスで直接定義されたメンバー参照のみを検索します。継承されたメンバ参照は見つかりません。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれる  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
