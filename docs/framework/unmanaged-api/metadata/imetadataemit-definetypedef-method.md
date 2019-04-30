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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9b6f5881f289bed258191baf4f43264ea6ba35db
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992590"
---
# <a name="imetadataemitdefinetypedef-method"></a>IMetaDataEmit::DefineTypeDef メソッド
共通言語ランタイム型では、型定義を作成し、その種類の定義のメタデータ トークンを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
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
 [in]Unicode での型の名前。  
  
 `dwTypeDefFlags`  
 [in]`TypeDef`属性。 これは、ビットマスクの`CoreTypeAttr`値。  
  
 `tkExtends`  
 [in]基底クラスのトークンです。 いずれかする必要があります、`mdTypeDef`または`mdTypeRef`トークンです。  
  
 `rtkImplements`  
 [in]このクラスまたはインターフェイスを実装するインターフェイスを指定するトークンの配列。  
  
 `ptd`  
 [out]`mdTypeDef`に割り当てられたトークン。  
  
## <a name="remarks"></a>Remarks  
 フラグ`dwTypeDefFlags`作成される型が共通型システム参照型 (クラスまたはインターフェイス) または共通型システム値型があるかどうかを指定します。  
  
 によって指定されたパラメーター、このメソッドは、副作用として可能性がありますも作成、`mdInterfaceImpl`継承またはこの型によって実装されるインターフェイスごとに記録します。 ただし、このメソッドが返さないいずれ`mdInterfaceImpl`トークンです。 クライアントが後で追加または変更する場合、`mdInterfaceImpl`トークンを使用してがあります、`IMetaDataImport`それらを列挙するインターフェイス。 COM のセマンティクスを使用する場合、`[default]`インターフェイスの最初の要素として、既定のインターフェイスを指定する必要があります`rtkImplements`; クラスに既定のインターフェイスをクラスに設定するカスタム属性が示されます (常にあると見なされますが、まず`mdInterfaceImpl`クラスの宣言されたトークン)。  
  
 各要素、`rtkImplements`配列を保持する`mdTypeDef`または`mdTypeRef`トークンです。 配列内の最後の要素である必要があります`mdTokenNil`します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして使用  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
