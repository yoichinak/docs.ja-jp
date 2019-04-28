---
title: IMetaDataImport::GetNameFromToken メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetNameFromToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetNameFromToken
helpviewer_keywords:
- GetNameFromToken method [.NET Framework metadata]
- IMetaDataImport::GetNameFromToken method [.NET Framework metadata]
ms.assetid: 32114ecf-8916-4ab2-a201-179c017344f1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1d77891478c9136a18dc4c9c44beed805244dd1a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777599"
---
# <a name="imetadataimportgetnamefromtoken-method"></a>IMetaDataImport::GetNameFromToken メソッド
指定したメタデータ トークンによって参照されるオブジェクトの UTF-8 名を取得します。 このメソッドは、互換性のために残されています。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetNameFromToken (  
   [in] mdToken      tk,  
   [out] MDUTF8CSTR  *pszUtf8NamePtr  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `tk`  
 [in]名前を取得するオブジェクトを表すトークンです。  
  
 `pszUtf8NamePtr`  
 [out]ヒープで utf-8 オブジェクト名へのポインター。  
  
## <a name="remarks"></a>Remarks  
 `GetNameFromToken` は互換性のために残されています。 代わりに、トークンを必要に応じてなどの特定の型のプロパティを取得するメソッドを呼び出す`GetFieldProps`フィールドまたは`GetMethodProps`メソッド。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll でリソースとして含まれます  
  
 **.NET framework のバージョン:** 1  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
