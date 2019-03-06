---
title: '方法: 中抜きの文字列を作成する'
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
ms.openlocfilehash: 409981e9c751144d26151210977a45b5e1eccf0a
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368152"
---
# <a name="how-to-create-outlined-text"></a>方法: 中抜きの文字列を作成する
ほとんどの場合、テキスト文字列内に装飾を追加するときに、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]アプリケーションでは、一連の個別の文字とグリフの観点からテキストを使用しています。 たとえば、線状グラデーション ブラシを作成してに適用、<xref:System.Windows.Controls.Control.Foreground%2A>のプロパティを<xref:System.Windows.Controls.TextBox>オブジェクト。 表示またはテキスト ボックスを編集すると、線状グラデーション ブラシがテキスト文字列内の文字の現在のセットに自動的に適用します。  
  
 ![線状グラデーション ブラシで表示されるテキスト](./media/outlinedtext01.jpg "OutlinedText01")  
テキスト ボックスに適用される線形グラデーション ブラシの例  
  
 ただし、テキストに変換も<xref:System.Windows.Media.Geometry>オブジェクトを視覚的にリッチ テキストの他の種類を作成することができます。 たとえば、作成する、<xref:System.Windows.Media.Geometry>のテキスト文字列のアウトラインに基づいてオブジェクト。  
  
 ![線形グラデーション ブラシを使用するテキスト アウトライン](./media/outlinedtext02.jpg "OutlinedText02")  
テキストのアウトラインのジオメトリに適用される線形グラデーション ブラシの例  
  
 テキストを変換するときに、<xref:System.Windows.Media.Geometry>文字のコレクションでは不要になったオブジェクト-テキスト文字列内の文字を変更することはできません。 ただし、変換されたテキストのストロークおよび塗りつぶしのプロパティを変更することで、テキストの外観を変えることができます。 ストロークは、変換したテキストのアウトラインを参照します。塗りつぶしは、変換したテキストのアウトラインの内側の領域を参照します。  
  
 次の例では、変換されたテキストの塗りつぶし、ストロークを変更して視覚効果を作成するいくつかの方法を示します。  
  
 ![塗りつぶしとストロークに別の色とテキスト](./media/outlinedtext03.jpg "OutlinedText03")  
ストロークと塗りつぶしを別々の色に設定した例  
  
 ![ストロークに適用されるイメージ ブラシを含むテキスト](./media/outlinedtext04.jpg "OutlinedText04")  
ストロークに適用したイメージ ブラシの例  
  
 境界ボックスの四角形、または変換後のテキストの強調表示を変更することもできます。 次の例では、ストロークと変換されたテキストの強調表示を変更することで視覚効果を作成する方法を示しています。  
  
 ![ストロークに適用されるイメージ ブラシを含むテキスト](./media/outlinedtext05.jpg "OutlinedText05")  
ストロークと強調表示に適用したイメージ ブラシの例  
  
## <a name="example"></a>例  
 テキストを変換するキー、<xref:System.Windows.Media.Geometry>オブジェクトは、使用する、<xref:System.Windows.Media.FormattedText>オブジェクト。 使用することがこのオブジェクトを作成すると、<xref:System.Windows.Media.FormattedText.BuildGeometry%2A>と<xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A>にテキストを変換するメソッドを<xref:System.Windows.Media.Geometry>オブジェクト。 最初のメソッドが書式設定されたテキストのジオメトリを返します2 番目のメソッドの境界ボックスの書式設定されたテキストのジオメトリを返します。 次のコード例を作成する方法を示しています、<xref:System.Windows.Media.FormattedText>オブジェクトと書式設定されたテキストとその境界ボックスのジオメトリを取得します。  
  
 [!code-csharp[OutlineTextControlViewer#CreateText](~/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#createtext)]
 [!code-vb[OutlineTextControlViewer#CreateText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#createtext)]  
  
 取得して、表示するために、<xref:System.Windows.Media.Geometry>オブジェクトにアクセスする必要がある、<xref:System.Windows.Media.DrawingContext>の変換後のテキストが表示されているオブジェクト。 これらのコード例では、ユーザー定義のレンダリングをサポートするクラスから派生したカスタム コントロール オブジェクトを作成してこれは、します。  
  
 表示する<xref:System.Windows.Media.Geometry>、カスタム コントロール内のオブジェクトのオーバーライドを提供する、<xref:System.Windows.UIElement.OnRender%2A>メソッド。 オーバーライドされたメソッドを使用する必要があります、<xref:System.Windows.Media.DrawingContext.DrawGeometry%2A>を描画するメソッド、<xref:System.Windows.Media.Geometry>オブジェクト。  
  
 [!code-csharp[OutlineTextControlViewer#OnRender](~/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#onrender)]
 [!code-vb[OutlineTextControlViewer#OnRender](~/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#onrender)]  
  
  カスタム ユーザー コントロール オブジェクトの例のソースを参照してください。[の OutlineTextControl.cs C# ](https://github.com/dotnet/samples/blob/master/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs)と[Visual basic の OutlineTextControl.vb](https://github.com/dotnet/samples/blob/master/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb)します。 
  
## <a name="see-also"></a>関連項目
- [書式設定されたテキストの描画](drawing-formatted-text.md)
