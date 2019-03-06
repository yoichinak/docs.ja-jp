---
title: ForwardTranslateAccelerator 関数 (WPF のアンマネージ API リファレンス)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ForwardTranslateAccelerator
api_location:
- PresentationHost_v0400.dll
ms.assetid: fff47a86-9d9f-4176-9530-10e1876e393f
ms.openlocfilehash: 2b1914b9a0e478c7ab15fca77b7df952123153ac
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57502290"
---
# <a name="forwardtranslateaccelerator-function-wpf-unmanaged-api-reference"></a>ForwardTranslateAccelerator 関数 (WPF のアンマネージ API リファレンス)
この API は、Windows Presentation Foundation (WPF) インフラストラクチャをサポートしているし、コードから直接使用するものではありません。  
  
 Windows Presentation Foundation (WPF) インフラストラクチャによって windows の管理に使用します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ForwardTranslateAccelerator(  
   MSG* pMsg,   
   VARIANT_BOOL appUnhandled  
)  
```  
  
## <a name="parameters"></a>パラメーター  
 pMsg  
 メッセージへのポインター。  
  
 appUnhandled  
 `true` アプリが、入力メッセージを処理する機会が与えられた既にがそれを処理していません。それ以外の場合、`false`します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** 参照してください[.NET Framework システム要件](../../get-started/system-requirements.md)します。  
  
 **DLL:**  
  
 .NET framework 3.0 および 3.5。PresentationHostDLL.dll  
  
 .NET framework 4 以降では。PresentationHost_v0400.dll  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [WPF のアンマネージ API リファレンス](wpf-unmanaged-api-reference.md)
