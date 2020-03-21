---
title: IMetaDataEmit::SetPropertyProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPropertyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPropertyProps
helpviewer_keywords:
- SetPropertyProps method [.NET Framework metadata]
- IMetaDataEmit::SetPropertyProps method [.NET Framework metadata]
ms.assetid: e2501fc8-b2bc-4dcc-9205-e3acd5a53ffe
topic_type:
- apiref
ms.openlocfilehash: dc6375f3e2cff1a744a8ff2e6a6adab27bbf8af3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177473"
---
# <a name="imetadataemitsetpropertyprops-method"></a>IMetaDataEmit::SetPropertyProps メソッド
[DefineProperty メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md)の前の呼び出しによって定義されたプロパティのメタデータに格納されているフィーチャを設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetPropertyProps (
    [in]  mdProperty      pr,
    [in]  DWORD           dwPropFlags,
    [in]  DWORD           dwCPlusTypeFlag,
    [in]  void const      *pValue,
    [in]  ULONG           cchValue,
    [in]  mdMethodDef     mdSetter,
    [in]  mdMethodDef     mdGetter,
    [in]  mdMethodDef     rmdOtherMethods[]
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pr`  
 [in]変更するプロパティのトークン  
  
 `dwPropFlags`  
 [in]プロパティ フラグ。  
  
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
 [in]プロパティに関連付けられている他のメソッドの配列。 この配列をトークンで`mdTokenNil`終了します。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MSCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
