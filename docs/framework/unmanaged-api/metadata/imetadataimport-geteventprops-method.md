---
title: IMetaDataImport::GetEventProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetEventProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetEventProps
helpviewer_keywords:
- IMetaDataImport::GetEventProps method [.NET Framework metadata]
- GetEventProps method [.NET Framework metadata]
ms.assetid: 5eaf3b4a-92b7-4d5b-97e0-1e83721e0052
topic_type:
- apiref
ms.openlocfilehash: 18fe0c834506d0ac4cd15fd7af4c4f15904b0f81
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437576"
---
# <a name="imetadataimportgeteventprops-method"></a>IMetaDataImport::GetEventProps メソッド
Gets metadata information for the event represented by the specified event token, including the declaring type, the add and remove methods for delegates, and any flags and other associated data.  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetEventProps (  
   [in]  mdEvent       ev,  
   [out] mdTypeDef     *pClass,   
   [out] LPCWSTR       szEvent,   
   [in]  ULONG         cchEvent,   
   [out] ULONG         *pchEvent,   
   [out] DWORD         *pdwEventFlags,  
   [out] mdToken       *ptkEventType,  
   [out] mdMethodDef   *pmdAddOn,   
   [out] mdMethodDef   *pmdRemoveOn,   
   [out] mdMethodDef   *pmdFire,   
   [out] mdMethodDef   rmdOtherMethod[],   
   [in]  ULONG         cMax,  
   [out] ULONG         *pcOtherMethod  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `ev`  
 [in] The event metadata token representing the event to get metadata for.  
  
 `pClass`  
 [out] A pointer to the TypeDef token representing the class that declares the event.  
  
 `szEvent`  
 [out] The name of the event referenced by `ev`.  
  
 `pchEvent`  
 [in] The requested length in wide characters of `szEvent`.  
  
 `pdwEventFlags`  
 [out] The returned length in wide characters of `szEvent`.  
  
 `ptkEventType`  
 [out] A pointer to a TypeRef or TypeDef metadata token representing the <xref:System.Delegate> type of the event.  
  
 `pmdAddOn`  
 [out] A pointer to the metadata token representing the method that adds handlers for the event.  
  
 `pmdRemoveOn`  
 [out] A pointer to the metadata token representing the method that removes handlers for the event.  
  
 `pmdFire`  
 [out] A pointer to the metadata token representing the method that raises the event.  
  
 `rmdOtherMethod`  
 [out] An array of token pointers to other methods associated with the event.  
  
 `cMax`  
 [in] `rmdOtherMethod` 配列の最大サイズ。  
  
 `pcOtherMethod`  
 [out] The number of tokens returned in `rmdOtherMethod`.  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **Header:** Cor.h  
  
 **Library:** Included as a resource in MsCorEE.dll  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
