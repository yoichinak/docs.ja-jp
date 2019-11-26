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
ms.openlocfilehash: acb772a64c8f13405f2836bb5f4f308986dce414
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447657"
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
 [in, out] A pointer to the enumerator.  
  
 `cl`  
 [in] A TypeDef token representing the type whose members are to be enumerated.  
  
 `rMembers`  
 [out] The array used to hold the MemberDef tokens.  
  
 `cMax`  
 [in] `rMembers` 配列の最大サイズ。  
  
 `pcTokens`  
 [out] The actual number of MemberDef tokens returned in `rMembers`.  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|`S_OK`|`EnumMembers` returned successfully.|  
|`S_FALSE`|There are no MemberDef tokens to enumerate. In that case, `pcTokens` is zero.|  
  
## <a name="remarks"></a>Remarks  
 When enumerating collections of members for a class, `EnumMembers` returns only members (fields and methods, but **not** properties or events) defined directly on the class. It does not return any members that the class inherits, even if the class provides an implementation for those inherited members. To enumerate inherited members, the caller must explicitly walk the inheritance chain. Note that the rules for the inheritance chain may vary depending on the language or compiler that emitted the original metadata.
 
 Properties and events are not enumerated by `EnumMembers`. To enumerate those, use [EnumProperties](imetadataimport-enumproperties-method.md) or [EnumEvents](imetadataimport-enumevents-method.md).
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **Header:** Cor.h  
  
 **Library:** Included as a resource in MsCorEE.dll  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
