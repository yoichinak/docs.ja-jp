---
title: IMetaDataImport::GetCustomAttributeProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetCustomAttributeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetCustomAttributeProps
helpviewer_keywords:
- GetCustomAttributeProps method [.NET Framework metadata]
- IMetaDataImport::GetCustomAttributeProps method [.NET Framework metadata]
ms.assetid: 6eefb243-a281-41c1-bcdc-7e17513bc446
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 422ff5d5a2924bf66fee9dad99d57fed9477d0f1
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484434"
---
# <a name="imetadataimportgetcustomattributeprops-method"></a>IMetaDataImport::GetCustomAttributeProps メソッド
指定したメタデータ トークンのカスタム属性の値を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetCustomAttributeProps (  
   [in]            mdCustomAttribute   cv,  
   [out, optional] mdToken             *ptkObj,  
   [out, optional] mdToken             *ptkType,  
   [out, optional] void const          **ppBlob,  
   [out, optional] ULONG               *pcbSize  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `cv`  
 [in] 取得するカスタム属性を表すメタデータ トークン。  
  
 `ptkObj`  
 [out]\(省略可能) カスタム属性が変更されるオブジェクトを表すメタデータ トークン。 この値には、`mdCustomAttribute` を除く任意の種類のトークンを指定できます。  
  
 `ptkType`  
 [out]\(省略可能) 返されるカスタム属性の <xref:System.Type> を表す `mdMethodDef` または `mdMemberRef` メタデータ トークン。  
  
 `ppBlob`  
 [out]\(省略可能) カスタム属性の値であるデータの配列へのポインター。  
  
 `pcbSize`  
 [out]\(省略可能) *`ppBlob` に返されたデータのサイズ (バイト単位)。  
  
## <a name="remarks"></a>Remarks  
 カスタム属性はデータの配列として格納され、その形式はメタデータ エンジンによって解釈されます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
