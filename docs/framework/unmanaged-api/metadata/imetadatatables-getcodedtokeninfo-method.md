---
title: IMetaDataTables::GetCodedTokenInfo メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetCodedTokenInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetCodedTokenInfo
helpviewer_keywords:
- GetCodedTokenInfo method [.NET Framework metadata]
- IMetaDataTables::GetCodedTokenInfo method [.NET Framework metadata]
ms.assetid: 31214d3a-715e-49af-92b3-0fd11e4f218a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 153aa7d6b8c35129638de3d47ffa6aff72f550c9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946787"
---
# <a name="imetadatatablesgetcodedtokeninfo-method"></a>IMetaDataTables::GetCodedTokenInfo メソッド
指定した行のインデックスに関連付けられているトークンの配列へのポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetCodedTokenInfo (   
    [in]  ULONG       ixCdTkn,  
    [out] ULONG       *pcTokens,  
    [out] ULONG       **ppTokens,  
    [out] const char  **ppName  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `ixCdTkn`  
 [in]コード化されたトークンの種類。  
  
 `pcTokens`  
 [out]長さへのポインター`ppTokens`します。  
  
 `ppTokens`  
 [out]返されたトークンの一覧を格納している配列へのポインターへのポインター。  
  
 `ppName`  
 [out]トークンの名前へのポインターへのポインター`ixCdTkn`します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataTables インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [IMetaDataTables2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
