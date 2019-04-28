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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: abbd35fe390cc09951b762a5fd671d2d34a57c6c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777885"
---
# <a name="imetadataimportfindmemberref-method"></a>IMetaDataImport::FindMemberRef メソッド
メンバーの MemberRef トークンへのポインターの参照を取得しますが、指定したで囲まれた<xref:System.Type>指定した名前とメタデータ シグネチャを持つとします。  
  
## <a name="syntax"></a>構文  
  
```  
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
 [in]クラスまたはインターフェイスを検索するメンバーの参照を囲むの TypeRef トークンです。 この値が場合`mdTokenNil`、グローバル変数またはグローバル関数の参照、検索を実行します。  
  
 `szName`  
 [in]検索するメンバーの参照の名前。  
  
 `pvSigBlob`  
 [in]メンバーの参照のバイナリ メタデータ シグネチャへのポインター。  
  
 `cbSigBlob`  
 [in]バイト サイズ`pvSigBlob`します。  
  
 `pmr`  
 [out]一致する MemberRef トークンへのポインター。  
  
## <a name="remarks"></a>Remarks  
 外側のクラスまたはインターフェイスを使用してメンバーを指定する (`td`)、その名前 (`szName`)、および必要に応じてその署名 (`pvSigBlob`)。  
  
 渡される署名`FindMemberRef`生成された現在のスコープで特定のスコープにバインドされるためです。 署名は、外側のクラスまたは値の型を識別するトークンを埋め込むことができます。 トークンは、ローカルの TypeDef テーブルへのインデックスです。 現在のスコープのコンテキスト外にあるランタイムのシグネチャを作成してへの入力としてその署名を使用することはできません`FindMemberRef`します。  
  
 `FindMemberRef` クラスまたはインターフェイス内で直接定義されたメンバーの参照のみを検索します。継承されたメンバーの参照が見つかりません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
