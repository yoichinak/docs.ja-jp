---
title: IMetaDataEmit::DefineProperty メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineProperty
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineProperty
helpviewer_keywords:
- IMetaDataEmit::DefineProperty method [.NET Framework metadata]
- DefineProperty method [.NET Framework metadata]
ms.assetid: 5c4c1dc2-d40d-4173-bbe6-7058fb21c98f
topic_type:
- apiref
ms.openlocfilehash: eb3ecbf39376e7126b5ec93a26badcbf5076d1db
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175786"
---
# <a name="imetadataemitdefineproperty-method"></a>IMetaDataEmit::DefineProperty メソッド
指定した型のプロパティ定義を、指定`get`したメソッド アクセサ`set`ーとメソッド アクセサーで作成し、そのプロパティ定義へのトークンを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DefineProperty (
    [in]  mdTypeDef          td,
    [in]  LPCWSTR            szProperty,
    [in]  DWORD              dwPropFlags,
    [in]  PCCOR_SIGNATURE    pvSig,
    [in]  ULONG              cbSig,
    [in]  DWORD              dwCPlusTypeFlag,
    [in]  void const         *pValue,
    [in]  ULONG              cchValue,
    [in]  mdMethodDef        mdSetter,
    [in]  mdMethodDef        mdGetter,
    [in]  mdMethodDef        rmdOtherMethods[],
    [out] mdProperty         *pmdProp
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `td`  
 [in]プロパティが定義されているクラスまたはインターフェイスのトークン。  
  
 `szProperty`  
 [in]プロパティの名前。  
  
 `dwPropFlags`  
 [in]プロパティフラグ。  
  
 `pvSig`  
 [in]プロパティのシグネチャ。  
  
 `cbSig`  
 [in]のバイト数`pvSig`。  
  
 `dwCPlusTypeFlag`  
 [in]プロパティの既定値の型。  
  
 `pValue`  
 [in]プロパティの既定値。  
  
 `cchValue`  
 [in]の (Unicode) 文字の`pValue`数。  
  
 `mdSetter`  
 [in]プロパティ値を設定するメソッド。  
  
 `mdGetter`  
 [in]プロパティ値を取得するメソッド。  
  
 `rmdOtherMethods[]`  
 [in]プロパティに関連付けられている他のメソッドの配列。 配列を で終了`mdTokenNil`します。  
  
 `pmdProp`  
 [アウト]割`mdProperty`り当てられたトークン。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MSCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
