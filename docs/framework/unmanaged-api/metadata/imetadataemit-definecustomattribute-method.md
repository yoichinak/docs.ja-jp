---
title: IMetaDataEmit::DefineCustomAttribute メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineCustomAttribute
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineCustomAttribute
helpviewer_keywords:
- DefineCustomAttribute method [.NET Framework metadata]
- IMetaDataEmit::DefineCustomAttribute method [.NET Framework metadata]
ms.assetid: 7dd14854-b756-4401-b167-88ca576dc8f0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 52190583338f1c1ee9183a98d5f4a6cd7236342d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992551"
---
# <a name="imetadataemitdefinecustomattribute-method"></a>IMetaDataEmit::DefineCustomAttribute メソッド
指定したオブジェクトに接続する、指定したメタデータ シグネチャを持つカスタム属性の定義を作成し、そのカスタム属性定義トークンを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT DefineCustomAttribute (   
    [in]  mdToken     tkObj,   
    [in]  mdToken     tkType,   
    [in]  void const  *pCustomAttribute,   
    [in]  ULONG       cbCustomAttribute,   
    [out] mdCustomAttribute *pcv   
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `tkObj`  
 [in]所有者アイテムのトークンです。  
  
 `tkType`  
 [in]カスタム属性を識別するトークンです。  
  
 `pCustomAttribute`  
 [in]カスタム属性へのポインター。  
  
 `cbCustomAttribute`  
 [in]内のバイト数`pCustomAttribute`します。  
  
 `pcv`  
 [out]`mdCustomAttribute`に割り当てられたトークン。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして使用  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
