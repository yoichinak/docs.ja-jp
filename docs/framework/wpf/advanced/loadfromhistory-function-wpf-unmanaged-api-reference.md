---
title: 読み込み履歴関数 - WPF アンマネージ API リファレンス
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- LoadFromHistory
api_location:
- PresentationHost_v0400.dll
ms.assetid: d037c062-a911-4949-b251-ccd3e48b1d17
ms.openlocfilehash: be9b8658614e678b4370044a753554859d230fed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141576"
---
# <a name="loadfromhistory-function-wpf-unmanaged-api-reference"></a>読み込み履歴関数 (WPF アンマネージ API リファレンス)
この API は、Windows プレゼンテーション基盤 (WPF) インフラストラクチャをサポートし、コードから直接使用することを意図していません。  
  
 Windows プレゼンテーション ファウンデーション (WPF) インフラストラクチャによってウィンドウ管理に使用されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT LoadFromHistory_export(  
        IStream* pHistoryStream,
        IBindCtx* pBindCtx  
)  
```  
  
## <a name="parameters"></a>パラメーター  
 をクリックします。  
 履歴情報のストリームへのポインター。  
  
 をクリックします。  
 バインド コンテキストへのポインター。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[NET Framework のシステム要件](../../get-started/system-requirements.md)を参照してください。  
  
 **Dll：**  
  
 NET フレームワーク 3.0 および 3.5: プレゼンテーションホストDLL.dll  
  
 NET フレームワーク 4 以降の場合: PresentationHost_v0400.dll  
  
 **.NET フレームワーク のバージョン:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [WPF のアンマネージ API リファレンス](wpf-unmanaged-api-reference.md)
