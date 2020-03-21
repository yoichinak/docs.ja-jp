---
title: '方法 : 文字の装飾を作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [WPF], baseline
- text [WPF], decorations
- fonts [WPF], underline
- fonts [WPF], overline
- strikethrough type [WPF]
- fonts [WPF], strikethrough
- overline type [WPF]
- underline type [WPF]
- typography [WPF], text decorations
- baseline type [WPF]
ms.assetid: cf3cb4e7-782a-4be7-b2d4-e0935e21e4e0
ms.openlocfilehash: cf3b3c3bcb75153a0be4f7ced03b38134b79a930
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185924"
---
# <a name="how-to-create-a-text-decoration"></a>方法 : 文字の装飾を作成する
オブジェクト<xref:System.Windows.TextDecoration>は、テキストに追加できる視覚的な装飾です。 文字装飾には、下線、ベースライン、取り消し線、上線の 4 種類があります。 次の例は、テキストに関連する文字装飾の位置を示しています。  
  
 ![文字装飾タイプの図](./media/how-to-create-a-text-decoration/text-decoration-types.gif)  
  
 テキストに文字装飾を追加するには、オブジェクトを<xref:System.Windows.TextDecoration>作成し、そのプロパティを変更します。 <xref:System.Windows.TextDecoration.Location%2A>下線などの文字装飾の表示場所を指定するには、このプロパティを使用します。 塗りつぶし<xref:System.Windows.TextDecoration.Pen%2A>やグラデーションの色など、文字装飾の外観を指定するには、このプロパティを使用します。 <xref:System.Windows.TextDecoration.Pen%2A>プロパティの値を指定しない場合、装飾は既定でテキストと同じ色になります。 オブジェクトを<xref:System.Windows.TextDecoration>定義したら、目的のテキスト オブジェクトの<xref:System.Windows.TextDecorations>コレクションに追加します。  
  
 線形グラデーション ブラシと破線のペンでスタイル設定された文字装飾の例を次に示します。  
  
 ![線形グラデーション下線を使用したテキスト装飾](./media/how-to-create-a-text-decoration/text-decoration-gradient.png)  
  
 オブジェクト<xref:System.Windows.Documents.Hyperlink>はインラインレベルのフローコンテンツ要素で、フローコンテンツ内でハイパーリンクをホストできます。 既定では、<xref:System.Windows.Documents.Hyperlink>オブジェクトを<xref:System.Windows.TextDecoration>使用して下線を表示します。 <xref:System.Windows.TextDecoration>オブジェクトのインスタンス化に対して、特に多数<xref:System.Windows.Documents.Hyperlink>のオブジェクトがある場合は、オブジェクトのインスタンス化に多くのパフォーマンスを要する場合があります。 要素を広範囲に<xref:System.Windows.Documents.Hyperlink>使用する場合は、イベントなどのイベントをトリガするときにのみ下線を表示することを検討してください。 <xref:System.Windows.ContentElement.MouseEnter>  
  
 次の例では、[マイ MSN] リンクの下線は動的で、<xref:System.Windows.ContentElement.MouseEnter>イベントがトリガーされたときにのみ表示されます。  
  
 ![TextDecorations を表示するハイパーリンク](./media/how-to-create-a-text-decoration/text-decorations-hyperlinks.png)  

 詳細については、「[方法: ハイパーリンクに下線を引くかどうかを指定する](how-to-specify-whether-a-hyperlink-is-underlined.md)」を参照してください。  
  
## <a name="example"></a>例  
 次のコード例では、下線付きの文字装飾で既定のフォント値が使用されます。  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets1)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets1)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets1)]  
  
 次のコード例では、ペンの単色ブラシを使用して下線付きの文字装飾を作成しています。  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets2)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets2)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets2)]  
  
 次のコード例では、点線付きのペンに線形グラデーション ブラシを使用して下線付きの文字装飾を作成します。  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets3)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets3)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets3)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.TextDecoration>
- <xref:System.Windows.Documents.Hyperlink>
- [ハイパーリンクに下線を引くかどうかを指定する](how-to-specify-whether-a-hyperlink-is-underlined.md)
