---
title: IEnumRAWINPUTDEVICE
ms.date: 03/30/2017
helpviewer_keywords:
- IEnumRAWINPUTDEVICE interface [WPF]
ms.assetid: 88c8b389-a48b-46b9-b895-8ed7b1e26fea
ms.openlocfilehash: 04caca0c580d26fde7fc9a3e3a11b7a8fed26d65
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59225522"
---
# <a name="ienumrawinputdevice"></a>IEnumRAWINPUTDEVICE
このインターフェイスは、未加工入力デバイスを列挙し、 PresentationHost.exe でのみ使用されます。  
  
> [!NOTE]
>  この API は、ローカル クライアント コンピューターでの使用のみを目的とし、サポートされています。  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|[IEnumRAWINPUTDEVIC:Next](ienumrawinputdevic-next.md)|次の `celt` 要素 (つまり RAWINPUTDEVICE 構造体) を、列挙子の一覧で列挙するとともに、それを `rgelt` で列挙された要素の実際の数とともに `pceltFetched` で返します。|  
|[IEnumRAWINPUTDEVIC:Skip](ienumrawinputdevic-skip.md)|列挙子は、[次へ] をスキップするように指示します`celt`列挙体の要素に、[次へ] を呼び出せるように[IEnumRAWINPUTDEVIC:Next](ienumrawinputdevic-next.md)それらの要素は返されません。|  
|[IEnumRAWINPUTDEVIC:Reset](ienumrawinputdevic-reset.md)|列挙のシーケンスを最初にリセットします。|  
|[IEnumRAWINPUTDEVIC:Clone](ienumrawinputdevic-clone.md)|同じリストを反復処理するため、現在の列挙子と同じ状態の別の未加工入力デバイスの列挙子を作成します。|  
  
## <a name="see-also"></a>関連項目

- [未加工入力について](/windows/desktop/inputdev/about-raw-input)
