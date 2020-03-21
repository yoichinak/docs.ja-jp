---
title: IMetaDataImport::EnumMembers メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMembers
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMembers
helpviewer_keywords:
- IMetaDataImport::EnumMembers method [.NET Framework metadata]
- EnumMembers method [.NET Framework metadata]
ms.assetid: 3fb8e178-342b-4c89-9bcf-f7f834e6cb77
topic_type:
- apiref
ms.openlocfilehash: 20c7a90f27defa18a5ef311d1f3a549b81fc5c40
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175487"
---
# <a name="imetadataimportenummembers-method"></a>IMetaDataImport::EnumMembers メソッド
指定した型のメンバーを表す MemberDef トークンを列挙します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnumMembers (
   [in, out]  HCORENUM    *phEnum,
   [in]  mdTypeDef   cl,
   [out] mdToken     rMembers[],
   [in]  ULONG       cMax,
   [out] ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `phEnum`  
 [イン、アウト]列挙子へのポインター。  
  
 `cl`  
 [in]列挙されるメンバーを持つ型を表す TypeDef トークン。  
  
 `rMembers`  
 [アウト]MemberDef トークンを保持するために使用される配列。  
  
 `cMax`  
 [in] `rMembers` 配列の最大サイズ。  
  
 `pcTokens`  
 [アウト]に返される MemberDef トークンの`rMembers`実際の数。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|`S_OK`|`EnumMembers`正常に返されました。|  
|`S_FALSE`|列挙する MemberDef トークンがありません。 その場合は、`pcTokens`ゼロです。|  
  
## <a name="remarks"></a>解説  
 クラスのメンバーのコレクションを列挙する場合、`EnumMembers`クラスに直接定義されたメンバー (フィールドとメソッド**not**ではなく、プロパティまたはイベント) のみが返されます。 クラスが継承されたメンバーの実装を提供する場合でも、クラスが継承するメンバーは返しません。 継承されたメンバーを列挙するには、呼び出し元が継承チェーンを明示的にウォークする必要があります。 継承チェーンの規則は、元のメタデータを出力した言語またはコンパイラによって異なる場合があります。

 プロパティとイベントは、 によって`EnumMembers`列挙されません。 これらのプロパティを列挙するには、[列挙プロパティ](imetadataimport-enumproperties-method.md)または[列挙イベント](imetadataimport-enumevents-method.md)を使用します。
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれる  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
