---
title: '方法: 複数行の TextBox コントロールを作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [WPF], multiple lines of text
ms.assetid: 05914a93-d0ea-4a9a-b693-09df7d4e2ac2
ms.openlocfilehash: 75bbee806b2b7039656d6c8e7c9a64359e77d16f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352348"
---
# <a name="how-to-create-a-multiline-textbox-control"></a>方法: 複数行の TextBox コントロールを作成する
この例は、使用する方法を示します[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]を定義する、<xref:System.Windows.Controls.TextBox>複数行のテキストに合わせて自動的に拡張するコントロール。  
  
## <a name="example"></a>例  
 設定、<xref:System.Windows.Controls.TextBox.TextWrapping%2A>属性を**ラップ**により、入力したテキストを新しいをラップするときに行の端、<xref:System.Windows.Controls.TextBox>コントロールに達すると、自動的に拡大、<xref:System.Windows.Controls.TextBox>場合、新しい行に含まれるコントロールいる。  
  
 設定、<xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A>属性を**true**が再び自動的に拡大、戻り値のキーが押されたときに挿入する改行を発生させる、<xref:System.Windows.Controls.TextBox>に必要な場合に、新しい行を含めます。  
  
 <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A>属性によってスクロール バーを表示、追加、<xref:System.Windows.Controls.TextBox>いるための内容、<xref:System.Windows.Controls.TextBox>場合をスクロール、<xref:System.Windows.Controls.TextBox>フレームまたはこれを囲むウィンドウのサイズします。  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.TextWrapping>
- [TextBox の概要](textbox-overview.md)
- [RichTextBox の概要](richtextbox-overview.md)
