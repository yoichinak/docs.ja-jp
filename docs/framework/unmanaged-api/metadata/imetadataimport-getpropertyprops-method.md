---
title: IMetaDataImport::GetPropertyProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPropertyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPropertyProps
helpviewer_keywords:
- GetPropertyProps method [.NET Framework metadata]
- IMetaDataImport::GetPropertyProps method [.NET Framework metadata]
ms.assetid: dc0ff3e6-7e7d-4f6c-948d-52b28f5cb78c
topic_type:
- apiref
ms.openlocfilehash: 247a2793bf3806f5ee38585d50b4535820dfcb69
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437062"
---
# <a name="imetadataimportgetpropertyprops-method"></a>IMetaDataImport::GetPropertyProps メソッド
Gets the metadata for the property represented by the specified token.  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetPropertyProps (  
   [in]  mdProperty        prop,  
   [out] mdTypeDef         *pClass,   
   [out] LPCWSTR           szProperty,   
   [in]  ULONG             cchProperty,   
   [out] ULONG             *pchProperty,   
   [out] DWORD             *pdwPropFlags,   
   [out] PCCOR_SIGNATURE   *ppvSig,   
   [out] ULONG             *pbSig,   
   [out] DWORD             *pdwCPlusTypeFlag,   
   [out] UVCP_CONSTANT     *ppDefaultValue,  
   [out] ULONG             *pcchDefaultValue,  
   [out] mdMethodDef       *pmdSetter,   
   [out] mdMethodDef       *pmdGetter,   
   [out] mdMethodDef       rmdOtherMethod[],  
   [in]  ULONG             cMax,   
   [out] ULONG             *pcOtherMethod   
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `prop`  
 [in] A token that represents the property to return metadata for.  
  
 `pClass`  
 [out] A pointer to the TypeDef token that represents the type that implements the property.  
  
 `szProperty`  
 [out] A buffer to hold the property name.  
  
 `cchProperty`  
 [in] The size in wide characters of `szProperty`.  
  
 `pchProperty`  
 [out] The number of wide characters returned in `szProperty`.  
  
 `pdwPropFlags`  
 [out] A pointer to any attribute flags applied to the property. This value is a bitmask from the [CorPropertyAttr](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md) enumeration.  
  
 `ppvSig`  
 [out] A pointer to the metadata signature of the property.  
  
 `pbSig`  
 [out] The number of bytes returned in `ppvSig`.  
  
 `pdwCPlusTypeFlag`  
 [out] A flag specifying the type of the constant that is the default value of the property. This value is from the CorElementType enumeration.  
  
 `ppDefaultValue`  
 [out] A pointer to the bytes that store the default value for this property.  
  
 `pcchDefaultValue`  
 [out] The size in wide characters of `ppDefaultValue`, if `pdwCPlusTypeFlag` is ELEMENT_TYPE_STRING; otherwise, this value is not relevant. In that case, the length of `ppDefaultValue` is inferred from the type that is specified by `pdwCPlusTypeFlag`.  
  
 `pmdSetter`  
 [out] A pointer to the MethodDef token that represents the set accessor method for the property.  
  
 `pmdGetter`  
 [out] A pointer to the MethodDef token that represents the get accessor method for the property.  
  
 `rmdOtherMethod`  
 [out] An array of MethodDef tokens that represent other methods associated with the property.  
  
 `cMax`  
 [in] `rmdOtherMethod` 配列の最大サイズ。 If you do not provide an array large enough to hold all the methods, they are skipped without warning.  
  
 `pcOtherMethod`  
 [out] The number of MethodDef tokens returned in `rmdOtherMethod`.  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **Header:** Cor.h  
  
 **Library:** Included as a resource in MsCorEE.dll  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
