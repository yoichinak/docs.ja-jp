---
title: IMapToken::Map メソッド
ms.date: 03/30/2017
api_name:
- IMapToken.Map
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMapToken::Map
helpviewer_keywords:
- IMapToken::Map method [.NET Framework metadata]
- Map method [.NET Framework metadata]
ms.assetid: b9b4bf2f-1098-43d6-9619-a99b4bda1940
topic_type:
- apiref
ms.openlocfilehash: 428b022ed560648f59798154d5987d382938c280
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176072"
---
# <a name="imaptokenmap-method"></a>IMapToken::Map メソッド
メタデータ シグネチャを使用してアセンブリ間のリレーションシップをマップします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Map (  
    [in]  mdToken tkImp,
    [in]  mdToken tkEmit  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `tkImp`  
 [in]インポートされたコード オブジェクトを表すメタデータ トークン。  
  
 `tkEmit`  
 [in]出力されたコード オブジェクトを表すメタデータ トークン。  
  
## <a name="remarks"></a>解説  
 マージ中にトークンの再マップが発生すると、元のトークンはインポートされた (ソース) メタデータ スコープでスコープが設定され、新しいトークンは出力される (ターゲット) メタデータ スコープ内でスコープが設定されます。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMapToken インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)
