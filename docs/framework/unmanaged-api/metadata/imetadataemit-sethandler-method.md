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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ada84df2a08b992aa178c2fb63c713b05a8937a2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57503217"
---
# <a name="imetadataemitsethandler-method"></a>IMetaDataEmit::SetHandler メソッド
指定したによって参照されるメソッドを設定`IUnknown`トークンを再マップの通知コールバックとしてのポインター。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetHandler (   
    [in]  IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pUnk`  
 [in]登録ハンドラー。  
  
## <a name="remarks"></a>Remarks  
 メタデータ エンジンによって提供されるメソッドを使用して通知を送信する`SetHandler`、最適化された方法でレコードを生成しないと、保存されたレコードを最適化するには、コンパイラに指示します。  
  
 を介して、コールバック メソッドが提供されていない場合`SetHandler`、最適化は実行されませんで保存さまざまなインポートを除くスコープがマージされたを使用して`IMapToken`でスコープごとにマージします。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして使用  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
