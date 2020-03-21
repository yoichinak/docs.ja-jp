---
title: IMetaDataEmit::Merge メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.Merge
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::Merge
helpviewer_keywords:
- IMetaDataEmit::Merge method [.NET Framework metadata]
- Merge method [.NET Framework metadata]
ms.assetid: 7596220c-f699-4b6c-8ae7-c83220610650
topic_type:
- apiref
ms.openlocfilehash: 759358822ed865c89f6f55084d1e7f6143506e93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175708"
---
# <a name="imetadataemitmerge-method"></a>IMetaDataEmit::Merge メソッド
指定されたインポートされたスコープを、マージするスコープのリストに追加します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Merge (
    [in]  IMetaDataImport  *pImport,
    [in]  IMapToken        *pHostMapToken,
    [in]  IUnknown         *pHandler
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pImport`  
 [in]マージするインポートされたスコープを識別する[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)オブジェクトへのポインター。  
  
 `pIMap`  
 [in]トークンの再マップを指定する[IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)オブジェクトへのポインター。  
  
 `pHandler`  
 [in]エラーを指定する[IUnknown](/cpp/atl/iunknown)オブジェクトへのポインター。  
  
## <a name="remarks"></a>解説  
 呼び出し[IMetaDataEmit::MergeEnd](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md)を呼び出して、メタデータの単一のスコープへの結合をトリガーします。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MSCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
