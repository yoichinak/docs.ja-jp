---
title: IMetaDataImport2::EnumGenericParams メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumGenericParams
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumGenericParams
helpviewer_keywords:
- EnumGenericParams method [.NET Framework metadata]
- IMetaDataImport2::EnumGenericParams method [.NET Framework metadata]
ms.assetid: b50488a5-3cf0-483c-82dc-2892a3ec61ac
topic_type:
- apiref
ms.openlocfilehash: 55709e79cd8bdb36fe1e32ee8a699fccb1b1bbc8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175305"
---
# <a name="imetadataimport2enumgenericparams-method"></a>IMetaDataImport2::EnumGenericParams メソッド
指定した TypeDef トークンまたは MethodDef トークンに関連付けられているジェネリック パラメーター トークンの配列の列挙子を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT EnumGenericParams (  
   [in, out] HCORENUM     *phEnum,
   [in]  mdToken          tk,  
   [out] mdGenericParam   rGenericParams[],
   [in]  ULONG            cMax,
   [out] ULONG            *pcGenericParams  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `phEnum`  
 [イン、アウト]列挙子へのポインター。  
  
 `tk`  
 [in]ジェネリック パラメーターを列挙する TypeDef トークンまたは MethodDef トークン。  
  
 `rGenericParams`  
 [アウト]列挙するジェネリック パラメーターの配列。  
  
 `cMax`  
 [in]に配置するトークンの要求最大数`rGenericParams`。  
  
 `pcGenericParams`  
 [アウト]に格納されたトークンの数が`rGenericParams`返されます。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|`S_OK`|`EnumGenericParams`正常に返されました。|  
|`S_FALSE`|`phEnum`メンバー要素がありません。 この場合、0(`pcGenericParams`ゼロ)に設定されます。|  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
