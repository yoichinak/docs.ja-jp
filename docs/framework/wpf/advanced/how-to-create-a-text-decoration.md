---
title: '方法: 文字の装飾を作成する'
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
ms.openlocfilehash: 22ff91770786e39e019de307167007548396ab33
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2019
ms.locfileid: "58411331"
---
# <a name="how-to-create-a-text-decoration"></a>方法: 文字の装飾を作成する
A<xref:System.Windows.TextDecoration>オブジェクトがビジュアルの装飾をテキストに追加することができます。 文字装飾の 4 つの種類があります。 ベースライン、下線、取り消し線、および上線。 次の例では、テキストに対する文字装飾の位置を示します。  
  
 ![文字装飾の種類の図](./media/how-to-create-a-text-decoration/text-decoration-types.gif)  
  
 テキストには、文字装飾を追加するには、作成、<xref:System.Windows.TextDecoration>オブジェクトし、そのプロパティを変更します。 使用して、<xref:System.Windows.TextDecoration.Location%2A>下線などの文字装飾を表示場所を指定するプロパティ。 使用して、<xref:System.Windows.TextDecoration.Pen%2A>塗りつぶしの純色のグラデーションなどの装飾の外観を指定するプロパティ。 値を指定しない場合、<xref:System.Windows.TextDecoration.Pen%2A>プロパティ、文字装飾の既定値は、テキストと同じ色。 定義した後、<xref:System.Windows.TextDecoration>オブジェクトに追加してください。、<xref:System.Windows.TextDecorations>目的のテキスト オブジェクトのコレクション。  
  
 次の例では、線状グラデーション ブラシと破線のペンによってスタイルが設定されている文字装飾を示します。  
  
 ![線形グラデーション下線を使用したテキスト装飾](./media/how-to-create-a-text-decoration/text-decoration-gradient.png)  
  
 <xref:System.Windows.Documents.Hyperlink>オブジェクトがインライン レベル フロー コンテンツ要素、フロー コンテンツ内のハイパーリンクをホストすることができます。 既定では、<xref:System.Windows.Documents.Hyperlink>を使用して、<xref:System.Windows.TextDecoration>下線を表示するオブジェクト。 <xref:System.Windows.TextDecoration> 多数ある場合は特に、オブジェクトは処理を要するインスタンスを作成すると、パフォーマンスにできる<xref:System.Windows.Documents.Hyperlink>オブジェクト。 広範に使用する場合<xref:System.Windows.Documents.Hyperlink>要素などのイベントをトリガーするときにのみ下線を表示するのにすることがあります、<xref:System.Windows.ContentElement.MouseEnter>イベント。  
  
 次の例では、"マイ MSN"リンクの下線が動的-にのみ表示されるときに、<xref:System.Windows.ContentElement.MouseEnter>イベントがトリガーされます。  
  
 ![TextDecorations を表示するハイパーリンク](./media/how-to-create-a-text-decoration/text-decorations-hyperlinks.png)  
   
 詳細については、「[方法: ハイパーリンクに下線を引くかどうかを指定する](how-to-specify-whether-a-hyperlink-is-underlined.md)」を参照してください。  
  
## <a name="example"></a>例  
 次のコード例では、下線文字の装飾は、既定のフォント値を使用します。  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets1)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets1)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets1)]  
  
 次のコード例では、ペンの純色ブラシを使用して下線の文字装飾が作成されます。  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets2)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets2)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets2)]  
  
 次のコード例では、下線文字の装飾は破線のペンの線状グラデーション ブラシで作成されます。  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets3)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets3)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets3)]  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.TextDecoration>
- <xref:System.Windows.Documents.Hyperlink>
- [ハイパーリンクに下線を引くかどうかを指定する](how-to-specify-whether-a-hyperlink-is-underlined.md)
