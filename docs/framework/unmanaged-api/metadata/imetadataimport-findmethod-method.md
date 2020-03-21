---
title: IMetaDataImport::FindMethod メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMethod
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMethod
helpviewer_keywords:
- FindMethod method [.NET Framework metadata]
- IMetaDataImport::FindMethod method [.NET Framework metadata]
ms.assetid: 0f9bde1d-e306-438d-941b-d0925b322304
topic_type:
- apiref
ms.openlocfilehash: 53b3d94e8b1e273fcbc041d25a5bf586a12735c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177252"
---
# <a name="imetadataimportfindmethod-method"></a>IMetaDataImport::FindMethod メソッド
指定した名前とメタデータ シグネチャを持つメソッドの MethodDef トークン<xref:System.Type>へのポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT FindMethod (  
   [in]  mdTypeDef          td,  
   [in]  LPCWSTR            szName,
   [in]  PCCOR_SIGNATURE    pvSigBlob,
   [in]  ULONG              cbSigBlob,
   [out] mdMethodDef        *pmb  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `td`  
 [in]検索`mdTypeDef`するメンバーを囲む型 (クラスまたはインターフェイス) のトークン。 この値が`mdTokenNil`の場合、グローバル関数の検索が行われます。  
  
 `szName`  
 [in]検索するメソッドの名前。  
  
 `pvSigBlob`  
 [in]メソッドのバイナリ メタデータ シグネチャへのポインター。  
  
 `cbSigBlob`  
 [in]のサイズ (バイト`pvSigBlob`単位)  
  
 `pmb`  
 [アウト]一致する MethodDef トークンへのポインター。  
  
## <a name="remarks"></a>解説  
 メソッドは、外側のクラスまたはインターフェイス (`td`) を使用して`szName`指定し、その名前 (`pvSigBlob`) 、およびオプションでそのシグネチャ ( ) を使用して指定します。 クラスまたはインターフェイス内に同じ名前のメソッドが複数存在する場合があります。 その場合は、メソッドのシグネチャを渡して一意の一致を見つけます。  
  
 渡された署名は`FindMethod`、特定のスコープにバインドされているため、現在のスコープで生成されている必要があります。 シグネチャは、外側のクラスまたは値の型を識別するトークンを埋め込むことができます。 トークンは、ローカルの TypeDef テーブルへのインデックスです。 現在のスコープのコンテキストの外部でランタイム シグネチャを作成し、そのシグネチャを`FindMethod`入力として使用することはできません。  
  
 `FindMethod`は、クラスまたはインターフェイスで直接定義されたメソッドのみを検索します。継承されたメソッドは見つかりません。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれる  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Reflection.MethodInfo>
- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
