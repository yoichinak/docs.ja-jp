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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1b80833892fc1c0290e94f5de7d9b081529c6a37
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62043923"
---
# <a name="imetadataemitdefineproperty-method"></a>IMetaDataEmit::DefineProperty メソッド
指定して、指定した型のプロパティの定義を作成します。`get`と`set`メソッド アクセサー、およびそのプロパティの定義にトークンを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
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
 [in]クラスまたはインターフェイスのプロパティを定義するトークンです。  
  
 `szProperty`  
 [in]プロパティの名前。  
  
 `dwPropFlags`  
 [in]プロパティのフラグ。  
  
 `pvSig`  
 [in]プロパティ シグネチャ。  
  
 `cbSig`  
 [in]内のバイト数`pvSig`します。  
  
 `dwCPlusTypeFlag`  
 [in]プロパティの既定値の型。  
  
 `pValue`  
 [in]プロパティの既定値。  
  
 `cchValue`  
 [in] \(Unicode) の数の文字について`pValue`です。  
  
 `mdSetter`  
 [in]このメソッドは、プロパティ値を設定します。  
  
 `mdGetter`  
 [in]このメソッドは、プロパティ値を取得します。  
  
 `rmdOtherMethods[]`  
 [in]プロパティに関連付けられているその他のメソッドの配列。 終了、配列、`mdTokenNil`します。  
  
 `pmdProp`  
 [out]`mdProperty`に割り当てられたトークン。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして使用  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
