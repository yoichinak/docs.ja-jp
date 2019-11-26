---
title: IMetaDataImport::GetMethodProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMethodProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMethodProps
helpviewer_keywords:
- GetMethodProps method [.NET Framework metadata]
- IMetaDataImport::GetMethodProps method [.NET Framework metadata]
ms.assetid: e0667ef7-1d31-4c89-a2d3-d426f023f8d2
topic_type:
- apiref
ms.openlocfilehash: 4a258ce9121a287929ca5bc39c480f1ca2596e78
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437464"
---
# <a name="imetadataimportgetmethodprops-method"></a>IMetaDataImport::GetMethodProps メソッド
指定した MethodDef トークンによって参照されるメソッドに関連付けられているメタデータを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetMethodProps (  
    [in]  mdMethodDef         mb,  
    [out] mdTypeDef           *pClass,  
    [out] LPWSTR              szMethod,  
    [in]  ULONG               cchMethod,  
    [out] ULONG               *pchMethod,  
    [out] DWORD               *pdwAttr,  
    [out] PCCOR_SIGNATURE     *ppvSigBlob,  
    [out] ULONG               *pcbSigBlob,  
    [out] ULONG               *pulCodeRVA,  
    [out] DWORD               *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `mb`  
 [in] The MethodDef token that represents the method to return metadata for.  
  
 `pClass`  
 [out] A Pointer to a TypeDef token that represents the type that implements the method.  
  
 `szMethod`  
 [out] A Pointer to a buffer that has the method's name.  
  
 `cchMethod`  
 [in] The requested size of `szMethod`.  
  
 `pchMethod`  
 [out] A Pointer to the size in wide characters of `szMethod`, or in the case of truncation, the actual number of wide characters in the method name.  
  
 `pdwAttr`  
 [out] A pointer to any flags associated with the method.  
  
 `ppvSigBlob`  
 [out] A pointer to the binary metadata signature of the method.  
  
 `pcbSigBlob`  
 [out] A Pointer to the size in bytes of `ppvSigBlob`.  
  
 `pulCodeRVA`  
 [out] A pointer to the relative virtual address of the method.  
  
 `pdwImplFlags`  
 [out] A pointer to any implementation flags for the method.  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **Header:** Cor.h  
  
 **Library:** Included as a resource in MsCorEE.dll  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
