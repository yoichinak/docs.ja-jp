---
title: IMetaDataImport2::EnumMethodSpecs メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumMethodSpecs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumMethodSpecs
helpviewer_keywords:
- IMetaDataImport2::EnumMethodSpecs method [.NET Framework metadata]
- EnumMethodSpecs method [.NET Framework metadata]
ms.assetid: b3fc1e6c-bcb6-4915-baf8-7dc0a31b8724
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a3641fcda33a497293dbf87b419c8606847dc296
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049844"
---
# <a name="imetadataimport2enummethodspecs-method"></a>IMetaDataImport2::EnumMethodSpecs メソッド
トークンに関連付けられた、指定した MethodDef または MemberRef MethodSpec トークンの配列の列挙子を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT EnumMethodSpecs (  
    [in, out] HCORENUM      *phEnum,   
    [in]      mdToken       tk,  
    [out]     mdMethodSpec  rMethodSpecs[],  
    [in]      ULONG         cMax,  
    [out]     ULONG         *pcMethodSpecs  
);   
```  
  
## <a name="parameters"></a>パラメーター  
 `phEnum`  
 [入力、出力]列挙子へのポインター`rMethodSpecs`します。  
  
 `tk`  
 [in]MethodSpec トークンが列挙メソッドを表す MemberRef または MethodDef トークンです。 場合の値`tk`0 (ゼロ) には、スコープ内のすべての MethodSpec トークンが列挙されます。  
  
 `rMethodSpecs`  
 [out]列挙する MethodSpec トークンの配列。  
  
 `cMax`  
 [in]配置するトークンの要求の最大数`rMethodSpecs`します。  
  
 `pcMethodSpecs`  
 [out]返されたトークンの数に配置`rMethodSpecs`します。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodSpecs` 正常に返されます。|  
|`S_FALSE`|`phEnum` メンバーの要素がありません。 この場合、 `pcMethodSpecs` 0 (ゼロ) に設定されます。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
