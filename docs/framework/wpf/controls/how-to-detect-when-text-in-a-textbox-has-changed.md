---
title: '方法: TextBox のテキストがいつ変更されたかを検出する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TextBox control [WPF], detecting text change
- text change [WPF], detecting
- detecting text change [WPF]
ms.assetid: 1c39ee14-e37f-49fb-a0d1-a9824ca13584
ms.openlocfilehash: 1adadb0f071815930d34f40ddf244ffc8c19131b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091149"
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a>方法: TextBox のテキストがいつ変更されたかを検出する
この例を使用する 1 つの方法を示しています、<xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged>イベント メソッドを実行するたびに内のテキストを<xref:System.Windows.Controls.TextBox>コントロールが変更されました。  
  
 分離コード クラスで、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を格納している、<xref:System.Windows.Controls.TextBox>変更については、監視するコントロールに挿入されるたびに呼び出すメソッドを<xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged>イベントが発生します。  このメソッドのシグネチャが一致で予期される必要があります、<xref:System.Windows.Controls.TextChangedEventHandler>を委任します。  
  
 イベント ハンドラーが呼び出されますたびの内容、<xref:System.Windows.Controls.TextBox>ユーザー、またはプログラムでコントロールを変更します。  
  
 **注:** このイベントを発生させるときに、<xref:System.Windows.Controls.TextBox>コントロールが作成し、最初にテキストを格納します。  
  
## <a name="example"></a>例  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]を定義する、<xref:System.Windows.Controls.TextBox>コントロールを指定、<xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged>イベント ハンドラー メソッドの名前に一致する値を持つ属性です。  
  
 [!code-xaml[TextBox_MiscCode#_TextChangedXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]  
  
## <a name="example"></a>例  
 分離コード クラスで、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を格納している、<xref:System.Windows.Controls.TextBox>変更については、監視するコントロールに挿入されるたびに呼び出すメソッドを<xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged>イベントが発生します。  このメソッドのシグネチャが一致で予期される必要があります、<xref:System.Windows.Controls.TextChangedEventHandler>を委任します。  
  
 [!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
 [!code-vb[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]  
  
 イベント ハンドラーが呼び出されますたびの内容、<xref:System.Windows.Controls.TextBox>ユーザー、またはプログラムでコントロールを変更します。  
  
 **注:** このイベントを発生させるときに、<xref:System.Windows.Controls.TextBox>コントロールが作成し、最初にテキストを格納します。  
  
 コメント  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.TextChangedEventArgs>
- [TextBox の概要](textbox-overview.md)
- [RichTextBox の概要](richtextbox-overview.md)
