---
title: IMetaDataTables::GetGuid メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetGuid
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetGuid
helpviewer_keywords:
- GetGuid method [.NET Framework metadata]
- IMetaDataTables::GetGuid method [.NET Framework metadata]
ms.assetid: a3546316-e24d-417f-9909-e45d42c9d471
topic_type:
- apiref
ms.openlocfilehash: 57df124f15f78daad053d9634e1baa969a65cc35
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175279"
---
# <a name="imetadatatablesgetguid-method"></a>IMetaDataTables::GetGuid メソッド
指定したインデックス位置にある行から GUID を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetGuid (
    [in]  ULONG       ixGuid,  
    [out] const GUID  **ppGUID  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `ixGuid`  
 [in]GUID を取得する行のインデックス。  
  
 `ppGuid`  
 [アウト]GUID へのポインターへのポインター。  
  
## <a name="remarks"></a>解説  

  このメソッドは一貫した結果を返さないため、このメソッドを使用することはお勧めしません。 GUID テーブルの詳細については、共通言語インフラストラクチャ (CLI) のドキュメント、特に「パーティション II: メタデータの定義とセマンティクス」を参照してください。 ドキュメントはオンラインで入手できます。[「ECMA C# および共通言語インフラストラクチャ標準](../../../standard/components.md#applicable-standards)と[標準 ECMA-335 - 共通言語インフラストラクチャ (CLI)」](http://www.ecma-international.org/publications/standards/Ecma-335.htm)を参照してください。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataTables インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [IMetaDataTables2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
