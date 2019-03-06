---
title: '方法: テキスト選択を取得する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [WPF], retrieving
- TextBox control [WPF], retrieving text
- retrieving text [WPF]
ms.assetid: d5793172-1e11-4a39-9be0-73f336ed858d
ms.openlocfilehash: fdd0e3974964e141c4b65e1c8851f3c371a4d501
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357613"
---
# <a name="how-to-retrieve-a-text-selection"></a>方法: テキスト選択を取得する
この例を使用する 1 つの方法を示しています、<xref:System.Windows.Controls.TextBox.SelectedText%2A>で、ユーザーが選択したテキストを取得するプロパティを<xref:System.Windows.Controls.TextBox>コントロール。  
  
## <a name="example"></a>例  
 次[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]の定義の例を<xref:System.Windows.Controls.TextBox>を選択するには、いくつかテキストを格納しているコントロールと<xref:System.Windows.Controls.Button>と指定したコントロール<xref:System.Windows.Controls.Button.OnClick%2A>メソッド。  
  
 この例では、関連付けられているボタンで<xref:System.Windows.Controls.Primitives.ButtonBase.Click>テキスト選択範囲を取得するイベント ハンドラーを使用します。 ユーザーは、ボタンをクリックしたときに、<xref:System.Windows.Controls.Button.OnClick%2A>メソッドは、テキスト ボックスで、選択したテキストを文字列にコピーします。 特定の状況では、これによって、テキスト選択の取得 (ボタンをクリックすると、) もその選択した場合 (文字列へのテキスト選択範囲をコピー)、実行されるアクションは、さまざまなシナリオに対応するために簡単に変更できます。  
  
 [!code-xaml[TextBox_MiscCode#_TextBoxSelectTextXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxselecttextxaml)]  
  
## <a name="example"></a>例  
 次C#の例に示す、<xref:System.Windows.Controls.Button.OnClick%2A>で定義されているボタンのイベント ハンドラー、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]この例です。  
  
 [!code-csharp[TextBox_MiscCode#_SelectText](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_selecttext)]
 [!code-vb[TextBox_MiscCode#_SelectText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_selecttext)]  
  
## <a name="see-also"></a>関連項目
- [TextBox の概要](textbox-overview.md)
- [RichTextBox の概要](richtextbox-overview.md)
