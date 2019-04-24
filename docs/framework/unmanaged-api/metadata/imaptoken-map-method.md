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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a85dc586b0c08fabdd34c018e82314c9003eeded
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59171015"
---
# <a name="imaptokenmap-method"></a>IMapToken::Map メソッド
メタデータ署名を使用して、アセンブリ間のリレーションシップをマップします。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Map (  
    [in]  mdToken tkImp,   
    [in]  mdToken tkEmit  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `tkImp`  
 [in]コードをインポート オブジェクトを表すメタデータ トークンです。  
  
 `tkEmit`  
 [in]出力コード オブジェクトを表すメタデータ トークンです。  
  
## <a name="remarks"></a>Remarks  
 トークンの再マップは、マージ中が発生、インポートされた (ソース) のメタデータ スコープ内に元のトークンがスコープ設定し、出力 (ターゲット) のメタデータ スコープに新しいトークンがスコープ設定します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMapToken インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)
