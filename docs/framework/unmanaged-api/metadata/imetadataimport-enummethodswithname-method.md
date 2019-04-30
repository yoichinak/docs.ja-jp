---
title: IMetaDataImport::EnumMethodsWithName メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodsWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodsWithName
helpviewer_keywords:
- IMetaDataImport::EnumMethodsWithName method [.NET Framework metadata]
- EnumMethodsWithName method [.NET Framework metadata]
ms.assetid: a8624913-2e23-46ad-a0c1-bb8eccbbf20f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f15ee906fb20cb60272cee3deffa68dbe852f689
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62042621"
---
# <a name="imetadataimportenummethodswithname-method"></a>IMetaDataImport::EnumMethodsWithName メソッド
指定された名前を持ち、指定された TypeDef トークンによって参照される型で定義されているメソッドを列挙します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT EnumMethodsWithName (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdTypeDef       cl,  
   [in]  LPCWSTR         szName,  
   [out] mdMethodDef     rMethods[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `phEnum`  
 [入力、出力]列挙子へのポインター。 このメソッドの最初の呼び出しで NULL があります。  
  
 `cl`  
 [in]列挙するメソッドを持つ型を表す TypeDef トークンです。  
  
 `szName`  
 [in]列挙体のスコープを制限する名前です。  
  
 `rMethods`  
 [out]MethodDef トークンを格納するために使用する配列。  
  
 `cMax`  
 [in] `rMethods` 配列の最大サイズ。  
  
 `pcTokens`  
 [out]返される MethodDef トークン数`rMethods`します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、フィールドと、メソッドがないプロパティまたはイベントを列挙します。 異なり[imetadataimport::enummethods](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md)、`EnumMethodsWithName`を指定した名前を持たないすべてのメソッドのトークンを破棄します。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodsWithName` 正常に返されます。|  
|`S_FALSE`|トークンを列挙することはありません。 その場合は、`pcTokens`は 0 です。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
