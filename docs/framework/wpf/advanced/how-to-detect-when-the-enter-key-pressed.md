---
title: '方法: ときに検出、押されたキーを入力します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Enter key [WPF], detecting
- keys [WPF], Enter
ms.assetid: a66f39d2-ef4a-43a5-b454-a4ea0fe88655
ms.openlocfilehash: 1796127d33087a3fd4504d03f175f8afe5323630
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57351863"
---
# <a name="how-to-detect-when-the-enter-key-pressed"></a>方法: ときに検出、押されたキーを入力します。
この例では、ときに検出、<xref:System.Windows.Input.Key.Enter>キーボードのキーが押されました。  
  
 この例は、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ファイルと分離コード ファイル。  
  
## <a name="example"></a>例  
 押されたとき、<xref:System.Windows.Input.Key.Enter>キー、<xref:System.Windows.Controls.TextBox>の別の領域で、テキスト ボックスに入力が表示されます、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]します。  
  
 次[!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)]で構成されるユーザー インターフェイスを作成、 <xref:System.Windows.Controls.StackPanel>、 <xref:System.Windows.Controls.TextBlock>、および<xref:System.Windows.Controls.TextBox>。  
  
 [!code-xaml[keydown#KeyDownUI](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml#keydownui)]  
  
 次のコードを作成、<xref:System.Windows.UIElement.KeyDown>イベント ハンドラー。  押されたキーがある場合、<xref:System.Windows.Input.Key.Enter>でメッセージを表示、キー、<xref:System.Windows.Controls.TextBlock>します。  
  
 [!code-csharp[keydown#KeyDownSample](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml.cs#keydownsample)]
 [!code-vb[keydown#KeyDownSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyDown/VisualBasic/Window1.xaml.vb#keydownsample)]  
  
## <a name="see-also"></a>関連項目
- [入力の概要](input-overview.md)
- [ルーティング イベントの概要](routed-events-overview.md)
