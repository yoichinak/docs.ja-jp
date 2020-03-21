---
title: 関数を転送する - WPF アンマネージ API リファレンス
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ForwardTranslateAccelerator
api_location:
- PresentationHost_v0400.dll
ms.assetid: fff47a86-9d9f-4176-9530-10e1876e393f
ms.openlocfilehash: a0a01be3000dc53df7855cb74015ba1164206838
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186631"
---
# <a name="forwardtranslateaccelerator-function-wpf-unmanaged-api-reference"></a>フォワードトランスレートアクセラレータ関数 (WPF アンマネージ API リファレンス)
この API は、Windows プレゼンテーション基盤 (WPF) インフラストラクチャをサポートし、コードから直接使用することを意図していません。  
  
 Windows プレゼンテーション ファウンデーション (WPF) インフラストラクチャによってウィンドウ管理に使用されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ForwardTranslateAccelerator(  
   MSG* pMsg,
   VARIANT_BOOL appUnhandled  
)  
```  
  
## <a name="parameters"></a>パラメーター  
 Pmsg  
 メッセージへのポインター。  
  
 アプリ未処理  
 `true`アプリが入力メッセージを処理する機会が既に与えられているが、それを処理していない場合。それ以外`false`の場合は、 .  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[NET Framework のシステム要件](../../get-started/system-requirements.md)を参照してください。  
  
 **Dll：**  
  
 NET フレームワーク 3.0 および 3.5: プレゼンテーションホストDLL.dll  
  
 NET フレームワーク 4 以降の場合: PresentationHost_v0400.dll  
  
 **.NET フレームワーク のバージョン:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [WPF のアンマネージ API リファレンス](wpf-unmanaged-api-reference.md)
