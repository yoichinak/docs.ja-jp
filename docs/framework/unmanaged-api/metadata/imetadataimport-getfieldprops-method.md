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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d7f8cccf8d583645982eb37f6afcb553914679ad
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59075675"
---
# <a name="imetadataimportgetfieldprops-method"></a>IMetaDataImport::GetFieldProps メソッド
指定した FieldDef トークンによって参照されるフィールドに関連付けられているメタデータを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
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
 [in]関連付けられているメタデータを取得するフィールドを表す FieldDef トークンです。  
  
 `pClass`  
 [out]フィールドが属するクラスの型を表す TypeDef トークンへのポインター。  
  
 `szField`  
 [out]フィールドの名前。  
  
 `cchField`  
 [in]サイズのバッファーのワイド文字単位*szField*します。  
  
 `pchField`  
 [out]返されたバッファーの実際のサイズ。  
  
 `pdwAttr`  
 [out]フィールドのメタデータに関連付けられたフラグ。  
  
 `ppvSigBlob`  
 [in]フィールドを説明するメタデータのバイナリ値へのポインター。  
  
 `pcbSigBlob`  
 [out]バイト サイズ`ppvSigBlob`します。  
  
 `pdwCPlusTypeFlag`  
 [out]フィールドの値の型を指定するフラグ。  
  
 `ppValue`  
 [out]フィールドの定数値。  
  
 `pcchValue`  
 [out]サイズの文字で`ppValue`、または 0 の文字列が存在しない場合。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
