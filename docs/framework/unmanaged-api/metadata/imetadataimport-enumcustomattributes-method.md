---
title: IMetaDataImport::EnumCustomAttributes メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumCustomAttributes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumCustomAttributes
helpviewer_keywords:
- EnumCustomAttributes method [.NET Framework metadata]
- IMetaDataImport::EnumCustomAttributes method [.NET Framework metadata]
ms.assetid: 798513a0-68b1-4d04-bc5b-782a4445ea68
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b80bb7b62d3a4ffee61cc6756b7d7d02f2b074bc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049948"
---
# <a name="imetadataimportenumcustomattributes-method"></a>IMetaDataImport::EnumCustomAttributes メソッド
指定した型またはメンバーに関連付けられたカスタム属性定義トークンを列挙します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT EnumCustomAttributes (   
   [in, out] HCORENUM      *phEnum,  
   [in]  mdToken            tk,   
   [in]  mdToken            tkType,   
   [out] mdCustomAttribute  rCustomAttributes[],   
   [in]  ULONG              cMax,  
   [out, optional] ULONG   *pcCustomAttributes  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `phEnum`  
 [入力、出力]返された列挙子へのポインター。  
  
 `tk`  
 [in]列挙体、またはすべてのカスタム属性に 0 のスコープのトークンです。  
  
 `tkType`  
 [in]列挙するには、属性の型のコンス トラクターのトークンまたは`null`すべての種類。  
  
 `rCustomAttributes`  
 [out]トークンのカスタム属性の配列。  
  
 `cMax`  
 [in] `rCustomAttributes` 配列の最大サイズ。  
  
 `pcCustomAttributes`  
 [out] 省略可能実際に返されるトークンの値数`rCustomAttributes`します。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|`S_OK`|`EnumCustomAttributes` 正常に返されます。|  
|`S_FALSE`|カスタム属性を列挙することはありません。 その場合は、`pcCustomAttributes`は 0 です。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
