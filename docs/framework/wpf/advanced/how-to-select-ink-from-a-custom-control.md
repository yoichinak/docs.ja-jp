---
title: '方法: カスタム コントロールからインクを選択する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], ink selection
- ink [WPF], selecting from custom control
- custom controls [WPF], ink selection
ms.assetid: 5f3a45c6-6d40-4017-9b47-933f134ceba3
ms.openlocfilehash: 8517041fd9a1864abfb32851314a2926ddab5a3e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57363778"
---
# <a name="how-to-select-ink-from-a-custom-control"></a>方法: カスタム コントロールからインクを選択する
追加することで、 <xref:System.Windows.Ink.IncrementalLassoHitTester> 、カスタム コントロールを有効に、コントロールと同様に、なげなわのツールを使用してインクをユーザーが選択できるように、<xref:System.Windows.Controls.InkCanvas>なげなわを使用してインクを選択します。  
  
 この例では、インク対応のカスタム コントロールの作成に慣れてを前提としています。  インク入力を受け入れるカスタム コントロールを作成するを参照してください。[インク入力コントロールの作成](creating-an-ink-input-control.md)です。  
  
## <a name="example"></a>例  
 ユーザーが、なげなわ選択を描画するとき、<xref:System.Windows.Ink.IncrementalLassoHitTester>予測するストロークは、ユーザーに、なげなわが完了したら、なげなわのパスの境界内になります。  なげなわのパスの境界内に決定されるストロークは、選択されていると考えることができます。  選択されたストロークは選択されていないもなります。  たとえば、ユーザーに、なげなわの描画中に方向が反転、<xref:System.Windows.Ink.IncrementalLassoHitTester>のストロークに選択を解除します。  
  
 <xref:System.Windows.Ink.IncrementalLassoHitTester>発生させる、<xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged>イベントで、ユーザーは、描画中に応答するカスタム コントロールを使用します。  たとえば、ユーザーを選択し、それらの選択を解除すると、ストロークの外観を変更できます。  
  
## <a name="managing-the-ink-mode"></a>インク モードの管理  
 なげなわがコントロール上のインクが異なって表示される場合、ユーザーに便利です。 これを実現するには、カスタム コントロールする必要がありますの追跡、ユーザーが作成またはインクを選択するかどうか。 これを行う最も簡単な方法が 2 つの値を持つ列挙型を宣言するには: インクと、ユーザーがインクを選択することを示す 1 つに、ユーザーを作成することを示す 1 つ。  
  
 [!code-csharp[HowToSelectInk#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#2)]
 [!code-vb[HowToSelectInk#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#2)]  
  
 次に、2 つ追加<xref:System.Windows.Ink.DrawingAttributes>クラス: ユーザーがインクは、ユーザーがインクを選択したときに使用する 1 つを記述するときに使用する 1 つ。  コンス トラクターの初期化、<xref:System.Windows.Ink.DrawingAttributes>両方添付して<xref:System.Windows.Ink.DrawingAttributes.AttributeChanged>同じイベント ハンドラーにイベント。 設定し、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A>のプロパティ、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>インク<xref:System.Windows.Ink.DrawingAttributes>します。  
  
 [!code-csharp[HowToSelectInk#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#3)]
 [!code-vb[HowToSelectInk#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#3)]  
[!code-csharp[HowToSelectInk#4](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#4)]
[!code-vb[HowToSelectInk#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#4)]  
  
 選択モードを公開するプロパティを追加します。 選択モードを変更するときは、設定、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A>のプロパティ、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>を適切な<xref:System.Windows.Ink.DrawingAttributes>オブジェクトを再アタッチし、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A>プロパティを<xref:System.Windows.Controls.InkPresenter>します。  
  
 [!code-csharp[HowToSelectInk#5](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#5)]
 [!code-vb[HowToSelectInk#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#5)]  
  
 公開、<xref:System.Windows.Ink.DrawingAttributes>としてプロパティのアプリケーションは、インク ストロークと選択範囲のストロークの外観を判断できるようにします。  
  
 [!code-csharp[HowToSelectInk#6](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#6)]
 [!code-vb[HowToSelectInk#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#6)]  
  
 場合のプロパティを<xref:System.Windows.Ink.DrawingAttributes>オブジェクトの変更を<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A>に再アタッチする必要があります、<xref:System.Windows.Controls.InkPresenter>します。  イベント ハンドラーで、<xref:System.Windows.Ink.DrawingAttributes.AttributeChanged>イベントを再アタッチ、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A>を<xref:System.Windows.Controls.InkPresenter>します。  
  
 [!code-csharp[HowToSelectInk#7](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#7)]
 [!code-vb[HowToSelectInk#7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#7)]  
  
## <a name="using-the-incrementallassohittester"></a>IncrementalLassoHitTester を使用します。  
 作成し、初期化、<xref:System.Windows.Ink.StrokeCollection>選択されたストロークを格納しています。  
  
 [!code-csharp[HowToSelectInk#8](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#8)]
 [!code-vb[HowToSelectInk#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#8)]  
  
 ユーザーがストロークを描画するために起動するときにインクまたはなげなわ選択したストローク選択解除します。 次に、なげなわ選択を描画して、ユーザー場合に作成、<xref:System.Windows.Ink.IncrementalLassoHitTester>呼び出して<xref:System.Windows.Ink.StrokeCollection.GetIncrementalLassoHitTester%2A>、購読、<xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged>イベント、および呼び出し<xref:System.Windows.Ink.IncrementalHitTester.AddPoints%2A>。 このコードは、別のメソッドとから呼び出される、<xref:System.Windows.UIElement.OnStylusDown%2A>と<xref:System.Windows.UIElement.OnMouseDown%2A>メソッド。  
  
 [!code-csharp[HowToSelectInk#9](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#9)]
 [!code-vb[HowToSelectInk#9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#9)]  
  
 スタイラス ポイントを追加、<xref:System.Windows.Ink.IncrementalLassoHitTester>中に、ユーザーになげなわを描画します。  次のメソッドを呼び出し、 <xref:System.Windows.UIElement.OnStylusMove%2A>、 <xref:System.Windows.UIElement.OnStylusUp%2A>、 <xref:System.Windows.UIElement.OnMouseMove%2A>、および<xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A>メソッド。  
  
 [!code-csharp[HowToSelectInk#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#10)]
 [!code-vb[HowToSelectInk#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#10)]  
  
 処理、<xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged?displayProperty=nameWithType>イベント、ユーザーを選択し、ストロークの選択を解除するときに応答します。  <xref:System.Windows.Ink.LassoSelectionChangedEventArgs>クラスには、<xref:System.Windows.Ink.LassoSelectionChangedEventArgs.SelectedStrokes%2A>と<xref:System.Windows.Ink.LassoSelectionChangedEventArgs.DeselectedStrokes%2A>ストロークを取得するプロパティが選択され、オフの場合、それぞれします。  
  
 [!code-csharp[HowToSelectInk#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#11)]
 [!code-vb[HowToSelectInk#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#11)]  
  
 ユーザーは、描画が完了したら、サブスクリプションの解除、<xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged>イベントと呼び出し<xref:System.Windows.Ink.IncrementalHitTester.EndHitTesting%2A>します。  
  
 [!code-csharp[HowToSelectInk#12](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#12)]
 [!code-vb[HowToSelectInk#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#12)]  
  
## <a name="putting-it-all-together"></a>すべてまとめて配置することです。  
 次の例では、ユーザーがなげなわを使用してインクを選択できるカスタム コントロールです。  
  
 [!code-csharp[HowToSelectInk#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#1)]
 [!code-vb[HowToSelectInk#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#1)]  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Ink.IncrementalLassoHitTester>
- <xref:System.Windows.Ink.StrokeCollection>
- <xref:System.Windows.Input.StylusPointCollection>
- [インク入力コントロールの作成](creating-an-ink-input-control.md)
