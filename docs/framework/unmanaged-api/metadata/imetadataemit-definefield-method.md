---
title: IMetaDataEmit::DefineField メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineField
helpviewer_keywords:
- IMetaDataEmit::DefineField method [.NET Framework metadata]
- DefineField method, IMetaDataEmit interface [.NET Framework metadata
ms.assetid: 6b5be4fc-2e86-499c-8b09-833160bca767
topic_type:
- apiref
ms.openlocfilehash: 8ca5ab70f60de4d783800fb18612a8f04cb9cee1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177715"
---
# <a name="imetadataemitdefinefield-method"></a>IMetaDataEmit::DefineField メソッド
指定したメタデータ シグネチャを持つフィールドの定義を作成し、そのフィールド定義へのトークンを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DefineField (
    [in]  mdTypeDef   td,
    [in]  LPCWSTR     szName,
    [in]  DWORD       dwFieldFlags,
    [in]  PCCOR_SIGNATURE pvSigBlob,
    [in]  ULONG       cbSigBlob,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,
    [in]  ULONG       cchValue,
    [out] mdFieldDef  *pmd
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `td`  
 [in]外側`mdTypeDef`のクラスまたはインターフェイスのトークン。  
  
 `szName`  
 [in]ユニコードのフィールド名。  
  
 `dwFieldFlags`  
 [in]フィールド属性。 これは値の`CorFieldAttr`ビットマスクです。  
  
 `pvSigBlob`  
 [in]BLOB としてのフィールド シグネチャ。  
  
 `cbSigBlob`  
 [in]のバイト数`pvSigBlob`。  
  
 `dwCPlusTypeFlag`  
 [in]`ELEMENT_TYPE_`*\** 定数値の場合。 これは値です`CorElementType`。 フィールドの定数値を定義しない場合は、 を`ELEMENT_TYPE_END`使用します。  
  
 `pValue`  
 [in]フィールドの定数値。  
  
 `cchValue`  
 [in]のサイズ (Unicode) 文字`pValue`  
  
 `pmd`  
 [アウト]割`mdFieldDef`り当てられたトークン。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MSCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
