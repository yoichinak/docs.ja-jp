---
title: IMetaDataImport::EnumMembersWithName メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMembersWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMembersWithName
helpviewer_keywords:
- IMetaDataImport::EnumMembersWithName method [.NET Framework metadata]
- EnumMembersWithName method [.NET Framework metadata]
ms.assetid: 7c9e9120-3104-42f0-86ce-19a025f20dcc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 961c1e0468ab99baca387b7d6ada4733629b7ffa
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492232"
---
# <a name="imetadataimportenummemberswithname-method"></a>IMetaDataImport::EnumMembersWithName メソッド
指定した名前を持つ指定した型のメンバーを表す MemberDef トークンを列挙します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT EnumMembersWithName (  
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   cl,   
   [in]      LPCWSTR     szName,   
   [out]     mdToken     rMembers[],   
   [in]      ULONG       cMax,   
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `phEnum`  
 [入力、出力]列挙子へのポインター。  
  
 `cl`  
 [in]列挙のメンバーを持つ型を表す TypeDef トークンです。  
  
 `szName`  
 [in]列挙子のスコープを制限するメンバーの名前。  
  
 `rMembers`  
 [out]MemberDef トークンを格納するために使用する配列。  
  
 `cMax`  
 [in] `rMembers` 配列の最大サイズ。  
  
 `pcTokens`  
 [out]実際に返される MemberDef トークン数`rMembers`します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、フィールドと、メソッドがないプロパティまたはイベントを列挙します。 異なり[imetadataimport::enummembers](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md)、`EnumMembersWithName`指定した名前がないすべてのフィールドとメンバーのトークンを破棄します。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|`S_OK`|`EnumTypeDefs` 正常に返されます。|  
|`S_FALSE`|MemberDef トークンを列挙することはありません。 その場合は、`pcTokens`は 0 です。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
