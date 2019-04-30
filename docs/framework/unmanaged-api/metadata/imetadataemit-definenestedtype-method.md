---
title: IMetaDataEmit::DefineNestedType メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineNestedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineNestedType
helpviewer_keywords:
- IMetaDataEmit::DefineNestedType method [.NET Framework metadata]
- DefineNestedType method [.NET Framework metadata]
ms.assetid: 1e994de6-4628-459c-b967-b34be1e9fe4f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4ebd4e9beca315ef8284c915800afec6bdb78c78
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62044006"
---
# <a name="imetadataemitdefinenestedtype-method"></a>IMetaDataEmit::DefineNestedType メソッド
型定義のメタデータ署名を作成し、返します、 `mdTypeDef` 、その型のトークンし、定義された型によって参照される型のメンバーであることを指定します、`tdEncloser`パラメーター。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT DefineNestedType (   
    [in]  LPCWSTR     szTypeDef,  
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[],   
    [in]  mdTypeDef   tdEncloser,   
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `szTypeDef`  
 [in]Unicode での型の名前。  
  
 `dwTypeDefFlags`  
 [in]`TypeDef`属性。 これは、ビットマスクの`CorTypeAttr`値。  
  
 `tkExtends`  
 [in]基底クラスのトークンです。 いずれかになります、`mdTypeDef`または`mdTypeRef`トークンです。  
  
 `rtkImplements`[]  
 [in]このクラスまたはインターフェイスを実装するインターフェイスを指定するトークンの配列。  
  
 `tdEncloser`  
 [in]それを囲む型のトークンです。 配列の最後の要素である必要があります`mdTokenNil`します。  
  
 `ptd`  
 [out]`mdTypeDef`に割り当てられたトークン。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして使用  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
