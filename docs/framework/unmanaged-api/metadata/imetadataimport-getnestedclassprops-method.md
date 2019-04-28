---
title: IMetaDataImport::GetNestedClassProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetNestedClassProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetNestedClassProps
helpviewer_keywords:
- GetNestedClassProps method [.NET Framework metadata]
- IMetaDataImport::GetNestedClassProps method [.NET Framework metadata]
ms.assetid: 704d19f1-bdef-4745-af8c-6476eb246fb3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eb5820087001a207af0c2552f91b4c17f5f78ff7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777658"
---
# <a name="imetadataimportgetnestedclassprops-method"></a>IMetaDataImport::GetNestedClassProps メソッド
親の TypeDef トークンを取得<xref:System.Type>入れ子にされた型を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetNestedClassProps (  
   [in]   mdTypeDef      tdNestedClass,  
   [out]  mdTypeDef      *ptdEnclosingClass  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `tdNestedClass`  
 [in]TypeDef トークンを表す、<xref:System.Type>親クラスを返すためにトークン。  
  
 `ptdEnclosingClass`  
 [out]TypeDef トークンへのポインター、<xref:System.Type>を`tdNestedClass`で入れ子になっています。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
