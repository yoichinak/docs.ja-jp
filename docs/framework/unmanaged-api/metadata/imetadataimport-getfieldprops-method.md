---
title: IMetaDataImport::GetFieldProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetFieldProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetFieldProps
helpviewer_keywords:
- IMetaDataImport::GetFieldProps method [.NET Framework metadata]
- GetFieldProps method [.NET Framework metadata]
ms.assetid: 7b0e9b10-8cef-4ba6-8432-40bf63e65ab1
topic_type:
- apiref
ms.openlocfilehash: 462512fd2c2b33905b45bb67599b23b301fc71f7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437995"
---
# <a name="imetadataimportgetfieldprops-method"></a>IMetaDataImport::GetFieldProps メソッド
指定した FieldDef トークンによって参照されるフィールドに関連付けられているメタデータを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetFieldProps (  
   [in]  mdFieldDef        mb,   
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szField,  
   [in]  ULONG             cchField,   
   [out] ULONG             *pchField,  
   [out] DWORD             *pdwAttr,  
   [in]  PCCOR_SIGNATURE   *ppvSigBlob,   
   [out] ULONG             *pcbSigBlob,   
   [out] DWORD             *pdwCPlusTypeFlag,   
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `mb`  
 [in] A FieldDef token that represents the field to get associated metadata for.  
  
 `pClass`  
 [out] A pointer to a TypeDef token that represents the type of the class that the field belongs to.  
  
 `szField`  
 [out] The name of the field.  
  
 `cchField`  
 [in] The size in wide characters of the buffer for *szField*.  
  
 `pchField`  
 [out] The actual size of the returned buffer.  
  
 `pdwAttr`  
 [out] Flags associated with the field's metadata.  
  
 `ppvSigBlob`  
 [in] A pointer to the binary metadata value that describes the field.  
  
 `pcbSigBlob`  
 [out] The size in bytes of `ppvSigBlob`.  
  
 `pdwCPlusTypeFlag`  
 [out] A flag that specifies the value type of the field.  
  
 `ppValue`  
 [out] A constant value for the field.  
  
 `pcchValue`  
 [out] The size in chars of `ppValue`, or zero if no string exists.  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **Header:** Cor.h  
  
 **Library:** Included as a resource in MsCorEE.dll  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
