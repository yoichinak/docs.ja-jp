---
title: IMetaDataTables::GetRow メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetRow
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetRow
helpviewer_keywords:
- IMetaDataTables::GetRow method [.NET Framework metadata]
- GetRow method [.NET Framework metadata]
ms.assetid: a7408d51-0bce-45a2-b58f-da4660bbc039
topic_type:
- apiref
ms.openlocfilehash: 71f6c496816fec1a7537f5ccdfdc1b47d17da871
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177116"
---
# <a name="imetadatatablesgetrow-method"></a>IMetaDataTables::GetRow メソッド
指定したテーブル インデックスのテーブル内の指定した行インデックスの行を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetRow (
    [in]  ULONG   ixTbl,  
    [in]  ULONG   rid,  
    [out] void    **ppRow  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `ixTbl`  
 [in]行の取得元となるテーブルのインデックス。  
  
 `rid`  
 [in]取得する行のインデックス。  
  
 `ppRow`  
 [アウト]行へのポインターへのポインター。  
  
## <a name="remarks"></a>解説  

  このメソッドは一貫した結果を返さないため、このメソッドを使用することはお勧めしません。 GUID テーブルの詳細については、共通言語インフラストラクチャ (CLI) のドキュメント、特に「パーティション II: メタデータの定義とセマンティクス」を参照してください。 ドキュメントはオンラインで入手できます。[「ECMA C# および共通言語インフラストラクチャ標準](../../../standard/components.md#applicable-standards)と[標準 ECMA-335 - 共通言語インフラストラクチャ (CLI)」](http://www.ecma-international.org/publications/standards/Ecma-335.htm)を参照してください。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET フレームワークのバージョン**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataTables インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [IMetaDataTables2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
