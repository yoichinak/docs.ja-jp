---
title: '方法 : 中抜きの文字列を作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- typography [WPF], linear gradient brush
- outlined text [WPF]
- gradient brush [WPF]
- linear gradient brush [WPF]
- typography [WPF], outline effects
ms.assetid: 4aa3cf6e-1953-4f26-8230-7c1409e5f28d
ms.openlocfilehash: d0ce46b9895589fd4635b567136204368a6431ad
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186858"
---
# <a name="how-to-create-outlined-text"></a>方法 : 中抜きの文字列を作成する
ほとんどの場合、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]アプリケーションでテキスト文字列に装飾を追加する場合、テキストを使用して、個別の文字またはグリフのコレクションを使用します。 たとえば、線形グラデーション ブラシを作成し、<xref:System.Windows.Controls.Control.Foreground%2A><xref:System.Windows.Controls.TextBox>オブジェクトのプロパティに適用できます。 テキスト ボックスを表示または編集すると、テキスト文字列の現在の文字セットに線形グラデーション ブラシが自動的に適用されます。  
  
 ![線形グラデーション ブラシで表示されるテキスト](./media/how-to-create-outlined-text/text-linear-gradient.jpg)
  
 ただし、テキストをオブジェクトに<xref:System.Windows.Media.Geometry>変換して、他の種類の視覚的なリッチ テキストを作成することもできます。 たとえば、テキスト文字列のアウトラインに<xref:System.Windows.Media.Geometry>基づいてオブジェクトを作成できます。  
  
 ![線形グラデーション ブラシを使用するテキスト アウトライン](./media/how-to-create-outlined-text/text-outline-linear-gradient.jpg)  
  
 テキストを<xref:System.Windows.Media.Geometry>オブジェクトに変換すると、文字のコレクションではなく、テキスト文字列の文字を変更することはできません。 ただし、変換されたテキストのストロークおよび塗りつぶしのプロパティを変更することで、テキストの外観を変えることができます。 ストロークは、変換したテキストのアウトラインを参照します。塗りつぶしは、変換したテキストのアウトラインの内側の領域を参照します。  
  
 次の例は、変換されたテキストのストロークと塗りつぶしを変更することによって視覚効果を作成するいくつかの方法を示しています。  
  
 ![塗りつぶしとストロークに別の色を使用するテキスト](./media/how-to-create-outlined-text/fill-stroke-text-effect.jpg)  
  
 ![ストロークに適用されるイメージ ブラシを含むテキスト](./media/how-to-create-outlined-text/image-brush-application.jpg)
  
 変換されたテキストの外接ボックスの四角形またはハイライトを変更することもできます。 次の例は、変換されたテキストのストロークと強調表示を変更して視覚効果を作成する方法を示しています。  
  
 ![イメージ ブラシがストロークとハイライトに適用されたテキスト](./media/how-to-create-outlined-text/image-brush-text-application.jpg)

## <a name="example"></a>例  
 テキストを<xref:System.Windows.Media.Geometry>オブジェクトに変換するキーは、オブジェクトを<xref:System.Windows.Media.FormattedText>使用することです。 このオブジェクトを作成したら、<xref:System.Windows.Media.FormattedText.BuildGeometry%2A>メソッドと メソッド<xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A>を使用してテキストをオブジェクトに<xref:System.Windows.Media.Geometry>変換できます。 最初のメソッドは、書式設定されたテキストのジオメトリを返します。2 番目のメソッドは、書式設定されたテキストの境界ボックスのジオメトリを返します。 <xref:System.Windows.Media.FormattedText>次のコード例は、オブジェクトを作成し、書式設定されたテキストとその境界ボックスのジオメトリを取得する方法を示しています。  
  
 [!code-csharp[OutlineTextControlViewer#CreateText](~/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#createtext)]
 [!code-vb[OutlineTextControlViewer#CreateText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#createtext)]  
  
 取得した<xref:System.Windows.Media.Geometry>オブジェクトを表示するには、変換されたテキストを表示しているオブジェクト<xref:System.Windows.Media.DrawingContext>にアクセスする必要があります。 これらのコード例では、ユーザー定義のレンダリングをサポートするクラスから派生したカスタム コントロール オブジェクトを作成することによって、この処理を行います。  
  
 カスタム<xref:System.Windows.Media.Geometry>コントロール内のオブジェクトを表示するには、メソッドのオーバーライド<xref:System.Windows.UIElement.OnRender%2A>を指定します。 オーバーライドしたメソッドは、オブジェクトを<xref:System.Windows.Media.DrawingContext.DrawGeometry%2A>描画するメソッドを<xref:System.Windows.Media.Geometry>使用する必要があります。  
  
 [!code-csharp[OutlineTextControlViewer#OnRender](~/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#onrender)]
 [!code-vb[OutlineTextControlViewer#OnRender](~/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#onrender)]  
  
  カスタム ユーザー コントロール オブジェクトの例のソースについては[、「C# のOutlineTextControl.cs](https://github.com/dotnet/samples/blob/master/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs)と[Visual Basic のアウトライン テキスト コントロール.vb](https://github.com/dotnet/samples/blob/master/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb)」を参照してください。
  
## <a name="see-also"></a>関連項目

- [書式設定されたテキストの描画](drawing-formatted-text.md)
