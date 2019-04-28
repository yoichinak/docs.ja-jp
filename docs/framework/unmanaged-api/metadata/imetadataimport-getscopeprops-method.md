---
title: IMetaDataImport::GetScopeProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetScopeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetScopeProps
helpviewer_keywords:
- IMetaDataImport::GetScopeProps method [.NET Framework metadata]
- GetScopeProps method [.NET Framework metadata]
ms.assetid: c8ba42d2-d9fa-43cb-bbc0-f33e1e592cb6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 17568a46c8e946989af0e401366d7eaa885886da
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777573"
---
# <a name="imetadataimportgetscopeprops-method"></a>IMetaDataImport::GetScopeProps メソッド
現在のメタデータ スコープにあるアセンブリまたはモジュールの名前、およびオプションでバージョン ID を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetScopeProps (  
   [out] LPWSTR           szName,  
   [in]  ULONG            cchName,  
   [out] ULONG            *pchName,  
   [out, optional] GUID   *pmvid  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `szName`  
 [out]アセンブリまたはモジュール名のバッファー。  
  
 `cchName`  
 [in]ワイド文字単位サイズ`szName`します。  
  
 `pchName`  
 [out]返されるワイド文字数`szName`します。  
  
 `pmvid`  
 [out] 省略可能アセンブリまたはモジュールのバージョンを一意に識別する GUID へのポインター。  
  
## <a name="remarks"></a>Remarks  
 [Imetadataemit::setmoduleprops](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md)メソッドを使用して、これらのプロパティを設定します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
