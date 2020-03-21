---
title: IMetaDataEmit::DefineTypeDef メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineTypeDef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineTypeDef
helpviewer_keywords:
- IMetaDataEmit::DefineTypeDef method [.NET Framework metadata]
- DefineTypeDef method [.NET Framework metadata]
ms.assetid: dd11c485-be95-4b97-9cd8-68679a4fb432
topic_type:
- apiref
ms.openlocfilehash: 4f1c3e823b35fcf7d5935eee111e042b2291d216
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175760"
---
# <a name="imetadataemitdefinetypedef-method"></a>IMetaDataEmit::DefineTypeDef メソッド
共通言語ランタイム型の型定義を作成し、その型定義のメタデータ トークンを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DefineTypeDef (
    [in]  LPCWSTR     szTypeDef,
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[],
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `szTypeDef`  
 [in]ユニコードの型の名前。  
  
 `dwTypeDefFlags`  
 [in]`TypeDef`属性を指定します。 これは値の`CoreTypeAttr`ビットマスクです。  
  
 `tkExtends`  
 [in]基本クラスのトークン。 トークンまたはトークン`mdTypeDef`のいずれか`mdTypeRef`である必要があります。  
  
 `rtkImplements`  
 [in]このクラスまたはインターフェイスが実装するインターフェイスを指定するトークンの配列。  
  
 `ptd`  
 [アウト]割`mdTypeDef`り当てられたトークン。  
  
## <a name="remarks"></a>解説  
 フラグを指定`dwTypeDefFlags`する型は、作成する型が共通型システム参照型 (クラスまたはインターフェイス) であるか、または共通の型システム値型であるかを指定します。  
  
 指定されたパラメーターによっては、このメソッドは、副作用として、この型によって継承または実装`mdInterfaceImpl`される各インターフェイスのレコードを作成することもあります。 ただし、このメソッドは、これらの`mdInterfaceImpl`トークンを返しません。 クライアントが後でトークンを追加または変更する`mdInterfaceImpl`場合は、インターフェイスを使用`IMetaDataImport`してトークンを列挙する必要があります。 `[default]`インターフェイスの COM セマンティクスを使用する場合は、既定のインターフェイスを の最初の要素として`rtkImplements`指定する必要があります。クラスに設定されたカスタム属性は、クラスに既定のインターフェイスがあることを示します (これは常にクラスに対して`mdInterfaceImpl`宣言された最初のトークンであると想定されます)。  
  
 配列の各要素`rtkImplements`は、`mdTypeDef`または`mdTypeRef`トークンを保持します。 配列の最後の要素は`mdTokenNil`.  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MSCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
