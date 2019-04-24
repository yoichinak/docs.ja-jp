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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e8d871f2ecbd96d5bda781b2ae11b94efd409442
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59128402"
---
# <a name="imetadataimportenummembers-method"></a>IMetaDataImport::EnumMembers メソッド
指定した型のメンバーを表す MemberDef トークンを列挙します。  
  
## <a name="syntax"></a>構文  
  
```  
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
 [入力、出力]列挙子へのポインター。  
  
 `cl`  
 [in]そのメンバーが列挙型を表す TypeDef トークンです。  
  
 `rMembers`  
 [out]MemberDef トークンを保持するために使用する配列。  
  
 `cMax`  
 [in] `rMembers` 配列の最大サイズ。  
  
 `pcTokens`  
 [out]実際に返される MemberDef トークン数`rMembers`します。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|`S_OK`|`EnumMembers` 正常に返されます。|  
|`S_FALSE`|MemberDef トークンを列挙することはありません。 その場合は、`pcTokens`は 0 です。|  
  
## <a name="remarks"></a>Remarks  
 クラスのメンバーのコレクションを列挙する場合、`EnumMembers`メンバーのみを返します (フィールドおよびメソッドが**いない**プロパティまたはイベント)、クラスで直接定義されています。 クラスは、継承されたメンバーの実装を提供する場合でも、クラスが継承する任意のメンバーは返されません。 継承されたメンバーを列挙するために、呼び出し元は明示的に継承チェーンを走査する必要があります。 継承チェーンの規則は、言語や、元のメタデータを生成するコンパイラによって異なる場合がありますに注意してください。
 
 プロパティおよびイベントはによって列挙されない`EnumMembers`します。 使用して、それらを列挙する[EnumProperties](imetadataimport-enumproperties-method.md)または[EnumEvents](imetadataimport-enumevents-method.md)します。
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
