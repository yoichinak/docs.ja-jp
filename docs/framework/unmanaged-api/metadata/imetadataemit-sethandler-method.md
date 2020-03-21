---
title: IMetaDataEmit::SetHandler メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetHandler
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetHandler
helpviewer_keywords:
- IMetaDataEmit::SetHandler method [.NET Framework metadata]
- SetHandler method [.NET Framework metadata]
ms.assetid: c6c1aaaf-e2cd-407c-b73e-fbe6ffd83bb3
topic_type:
- apiref
ms.openlocfilehash: 375c4b2cece0bdfd763ae383c5412c9e25614baf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177541"
---
# <a name="imetadataemitsethandler-method"></a>IMetaDataEmit::SetHandler メソッド
トークンの再マップの通知コールバックとして`IUnknown`、指定したポインターによって参照されるメソッドを設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetHandler (
    [in]  IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pUnk`  
 [in]登録するハンドラー。  
  
## <a name="remarks"></a>解説  
 メタデータ エンジンは、 によって`SetHandler`提供されるメソッドを使用して、最適化された方法でレコードを生成せず、保存されたレコードを最適化するコンパイラに通知を送信します。  
  
 コールバック メソッドが を通じて`SetHandler`提供されない場合、各スコープのマージ時に複数のインポート スコープがマージされている`IMapToken`場合を除き、save で最適化は実行されません。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MSCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
