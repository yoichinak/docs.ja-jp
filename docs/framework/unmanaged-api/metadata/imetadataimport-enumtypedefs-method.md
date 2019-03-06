---
title: IMetaDataImport::EnumTypeDefs メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeDefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeDefs
helpviewer_keywords:
- EnumTypeDefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeDefs method [.NET Framework metadata]
ms.assetid: 4e508711-da92-4381-aaf8-6803075cdaa2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9a285543571c843a982b6615fdc4b5f1325ed066
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466961"
---
# <a name="imetadataimportenumtypedefs-method"></a>IMetaDataImport::EnumTypeDefs メソッド
現在のスコープ内のすべての型を表す TypeDef トークンを列挙します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT EnumTypeDefs (  
   [out] HCORENUM   *phEnum,   
   [in]  mdTypeDef  rTypeDefs[],  
   [in]  ULONG      cMax,   
   [out] ULONG      *pcTypeDefs  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `phEnum`  
 [out]新しい列挙子へのポインター。 このメソッドの最初の呼び出しで NULL があります。  
  
 `rTypeDefs`  
 [in]TypeDef トークンを格納するために使用する配列。  
  
 `cMax`  
 [in] `rTypeDefs` 配列の最大サイズ。  
  
 `pcTypeDefs`  
 [out]TypeDef のトークンで返される数`rTypeDefs`します。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|`S_OK`|`EnumTypeDefs` 正常に返されます。|  
|`S_FALSE`|トークンを列挙することはありません。 その場合は、`pcTypeDefs`は 0 です。|  
  
## <a name="remarks"></a>Remarks  
 TypeDef トークンは、クラスやインターフェイスなどの型だけでなく、機能拡張メカニズムを使用して追加された型を表します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
