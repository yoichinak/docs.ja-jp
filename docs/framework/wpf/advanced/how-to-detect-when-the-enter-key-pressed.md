---
title: '方法: Enter キーが押されたことを検出する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Enter key [WPF], detecting
- keys [WPF], Enter
ms.assetid: a66f39d2-ef4a-43a5-b454-a4ea0fe88655
ms.openlocfilehash: e2337826077c836696937f91541d6d261f1270aa
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004825"
---
# <a name="how-to-detect-when-the-enter-key-pressed"></a>方法: Enter キーが押されたことを検出する
この例では、<xref:System.Windows.Input.Key.Enter> キーがキーボードで押されたことを検出する方法を示します。  
  
 この例は、@no__t 0 ファイルと分離コードファイルで構成されています。  
  
## <a name="example"></a>例  
 ユーザーが <xref:System.Windows.Controls.TextBox> の @no__t 0 キーを押すと、テキストボックスの入力が @no__t の別の領域に表示されます。  
  
 次の XAML は、@no__t 0、<xref:System.Windows.Controls.TextBlock>、<xref:System.Windows.Controls.TextBox> で構成されるユーザーインターフェイスを作成します。  
  
 [!code-xaml[keydown#KeyDownUI](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml#keydownui)]  
  
 次のコードでは、<xref:System.Windows.UIElement.KeyDown> イベントハンドラーを作成します。  押されたキーが @no__t 0 キーの場合、<xref:System.Windows.Controls.TextBlock> にメッセージが表示されます。  
  
 [!code-csharp[keydown#KeyDownSample](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml.cs#keydownsample)]
 [!code-vb[keydown#KeyDownSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyDown/VisualBasic/Window1.xaml.vb#keydownsample)]  
  
## <a name="see-also"></a>関連項目

- [入力の概要](input-overview.md)
- [ルーティング イベントの概要](routed-events-overview.md)
