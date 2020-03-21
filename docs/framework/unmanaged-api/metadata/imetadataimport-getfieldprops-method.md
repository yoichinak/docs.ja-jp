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
ms.openlocfilehash: 8c3f98a124dbbcae3b0500932a2357ed1757951f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177244"
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
 [in]関連付けられたメタデータを取得するフィールドを表す FieldDef トークン。  
  
 `pClass`  
 [アウト]フィールドが属するクラスの型を表す TypeDef トークンへのポインター。  
  
 `szField`  
 [アウト]フィールドの名前。  
  
 `cchField`  
 [in]*szField*のバッファーのワイド文字でのサイズ。  
  
 `pchField`  
 [アウト]返されるバッファーの実際のサイズ。  
  
 `pdwAttr`  
 [アウト]フィールドのメタデータに関連付けられたフラグ。  
  
 `ppvSigBlob`  
 [in]フィールドを記述するバイナリ メタデータ値へのポインター。  
  
 `pcbSigBlob`  
 [アウト]のサイズ (バイト`ppvSigBlob`単位)  
  
 `pdwCPlusTypeFlag`  
 [アウト]フィールドの値の型を指定するフラグ。  
  
 `ppValue`  
 [アウト]フィールドの定数値。  
  
 `pcchValue`  
 [アウト]の文字`ppValue`で表されるサイズ。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれる  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
