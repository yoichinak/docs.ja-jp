---
title: IMetaDataEmit::DefineEvent メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineEvent
helpviewer_keywords:
- IMetaDataEmit::DefineEvent method [.NET Framework metadata]
- DefineEvent method [.NET Framework metadata]
ms.assetid: cf064bac-9a9f-41c5-9e1d-108ff7af3afe
topic_type:
- apiref
ms.openlocfilehash: 6966d0ad2fefd8401b19d8e8dcf7776799a066b2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432565"
---
# <a name="imetadataemitdefineevent-method"></a>IMetaDataEmit::DefineEvent メソッド
Creates a definition for an event with the specified metadata signature, and gets a token to that event definition.  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DefineEvent (   
    [in]  mdTypeDef    td,   
    [in]  LPCWSTR      szEvent,   
    [in]  DWORD        dwEventFlags,   
    [in]  mdToken      tkEventType,   
    [in]  mdMethodDef  mdAddOn,   
    [in]  mdMethodDef  mdRemoveOn,   
    [in]  mdMethodDef  mdFire,   
    [in]  mdMethodDef  rmdOtherMethods[],   
    [out] mdEvent      *pmdEvent   
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `td`  
 [in] The token for the target class or interface. This is either a `mdTypeDef` or `mdTypeDefNil` token.  
  
 `szEvent`  
 [in] The name of the event.  
  
 `dwEventFlags`  
 [in] Event flags.  
  
 `tkEventType`  
 [in] The token for the event class. This is a `mdTypeDef`, a `mdTypeRef`, or a `mdTokenNil` token.  
  
 `mdAddOn`  
 [in] The method used to subscribe to the event, or null.  
  
 `mdRemoveOn`  
 [in] The method used to unsubscribe to the event, or null.  
  
 `mdFire`  
 [in] The method used (by a derived class) to raise the event.  
  
 `rmdOtherMethods[]`  
 [in] An array of tokens for other methods associated with the event. The array is terminated with a `mdMethodDefNil` token.  
  
 `pmdEvent`  
 [out] The metadata token assigned to the event.  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **Header:** Cor.h  
  
 **Library:** Used as a resource in MSCorEE.dll  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
