---
title: ガイドの概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], about adorners
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
ms.openlocfilehash: d8e6e53edc92a2847c001377706d313cf97cced5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956105"
---
# <a name="adorners-overview"></a>ガイドの概要
装飾は特殊な型<xref:System.Windows.FrameworkElement>であり、ユーザーに視覚的な手掛かりを提供するために使用されます。 装飾は、要素への機能ハンドル追加やコントロールに関する状態情報の提供など、さまざまな用途に使用できます。  

<a name="about_Adorners"></a>   
## <a name="about-adorners"></a>装飾について  
 は、にバインド<xref:System.Windows.FrameworkElement>され<xref:System.Windows.UIElement>ているカスタムです。 <xref:System.Windows.Documents.Adorner> 装飾はで<xref:System.Windows.Documents.AdornerLayer>レンダリングされます。これは、常に装飾された要素または装飾対象の要素のコレクションの上にあるレンダリングサーフェイスです。 装飾のレンダリングは、 <xref:System.Windows.UIElement>装飾がバインドされているのレンダリングからは独立しています。 通常、装飾は、装飾対象の要素の左上に位置する標準の 2 次元座標の原点を使用して、バインド先の要素に対して相対的な位置に配置されます。  
  
 装飾の一般的な用途は、次のとおりです。  
  
- に機能ハンドルを追加<xref:System.Windows.UIElement>して、ユーザーが何らかの方法 (サイズ変更、回転、位置合わせなど) で要素を操作できるようにします。  
  
- 視覚的なフィードバックによって、さまざまな状態を表示し、各種のイベントに応答する。  
  
- に視覚的な<xref:System.Windows.UIElement>装飾をオーバーレイします。  
  
- の一部または全体を視覚的に<xref:System.Windows.UIElement>マスクまたはオーバーライドします。  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] は、視覚的要素を装飾する基本的なフレームワークを提供します。 次の表に示すのは、オブジェクトの装飾に使用する主な種類と、その用途の一覧です。 その後に、使用例をいくつか示します。  
  
|||  
|-|-|  
|<xref:System.Windows.Documents.Adorner>|具体的な装飾の実装すべての継承元になる抽象基本クラス。|  
|<xref:System.Windows.Documents.AdornerLayer>|装飾される 1 つ以上の要素に対する、装飾のレンダリング層を表すクラス。|  
|<xref:System.Windows.Documents.AdornerDecorator>|1 つの装飾層を要素のコレクションに関連付けることを可能にするクラス。|  
  
<a name="implement_custom_Adorner"></a>   
## <a name="implementing-a-custom-adorner"></a>カスタム装飾の実装  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] が提供する装飾フレームワークは、カスタム装飾の作成をサポートすることを主な目的としています。 カスタム装飾は、抽象<xref:System.Windows.Documents.Adorner>クラスを継承するクラスを実装することによって作成されます。  
  
> [!NOTE]
> の<xref:System.Windows.Documents.Adorner> <xref:System.Windows.Documents.Adorner>親<xref:System.Windows.Documents.AdornerLayer>は、装飾される要素ではなく、をレンダリングするです。  
  
 次の例では、簡単な装飾を実装するクラスを示します。 この装飾の例では、 <xref:System.Windows.UIElement>単にの角を円でものしています。  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
 次の図は、に<xref:System.Windows.Controls.TextBox>適用される SimpleCircleAdorner を示しています。  
  
 ![装飾されたテキストボックスを示すスクリーンショット。](./media/adorners-overview/simplecircleadorner-textbox.png)  
  
<a name="rendering_behavior_for_Adorners"></a>   
## <a name="rendering-behavior-for-adorners"></a>装飾のレンダリング動作  
 装飾自体にはレンダリング動作が備わっていないので、装飾のレンダリングは装飾の実装側の責任で行う必要がある点に、注意が必要です。   レンダリング動作を実装する一般的な方法は、 <xref:System.Windows.UIElement.OnRender%2A>メソッドをオーバーライドし、1つまたは複数<xref:System.Windows.Media.DrawingContext>のオブジェクトを使用して、必要に応じて装飾のビジュアルをレンダリングすることです (上の例を参照)。  
  
> [!NOTE]
> 装飾層に配置されているすべてのものは、設定した他のすべてのスタイルの上に描画されます。 つまり、装飾は常に視覚的に最上位にあり、z オーダーを使用してオーバーライドすることはできません。  
  
<a name="adorner_events_hittest"></a>   
## <a name="events-and-hit-testing"></a>イベントおよびヒット テスト  
 装飾は、他<xref:System.Windows.FrameworkElement>と同様に入力イベントを受け取ります。  装飾は常に、それがもの要素よりも高い z オーダーを持つため、装飾は、基になる<xref:System.Windows.UIElement.Drop>装飾<xref:System.Windows.UIElement.MouseMove>対象の要素を対象とする可能性がある入力イベント (やなど) を受け取ります。  装飾は、特定の入力イベントをリッスンし、それらのイベントを再度発生させることによって、下位にある装飾対象の要素に渡すことができます。  
  
 装飾の下で要素のパススルーヒットテストを有効にするには、装飾<xref:System.Windows.UIElement.IsHitTestVisible%2A>でヒットテストプロパティを**false**に設定します。  ヒット テストの詳細については、次を参照してください。  
  
 [ビジュアル層でのヒット テスト](../graphics-multimedia/hit-testing-in-the-visual-layer.md)。  
  
<a name="adorn_single_element"></a>   
## <a name="adorning-a-single-uielement"></a>単一の UIElement の装飾  
 装飾を特定<xref:System.Windows.UIElement>のにバインドするには、次の手順を実行します。  
  
1. 静的メソッド<xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>を呼び出して、 <xref:System.Windows.UIElement>装飾<xref:System.Windows.Documents.AdornerLayer>するのオブジェクトを取得します。 <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>指定したを開始位置としてビジュアル<xref:System.Windows.UIElement>ツリーを検索し、最初に見つかった装飾層を返します。 (装飾層が見つからない場合、メソッドにより null が返されます)。  
  
2. 装飾を<xref:System.Windows.Documents.AdornerLayer.Add%2A>ターゲット<xref:System.Windows.UIElement>にバインドするには、メソッドを呼び出します。  
  
 次の例では、SimpleCircleAdorner (上の図を<xref:System.Windows.Controls.TextBox>参照) を名前付きの*myTextBox*にバインドします。  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
> [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] を使用して、装飾を別の要素にバインドする方法は、現在サポートされていません。  
  
<a name="adorn_children_panel"></a>   
## <a name="adorning-the-children-of-a-panel"></a>パネルの子の装飾  
 装飾をの<xref:System.Windows.Controls.Panel>子にバインドするには、次の手順を実行します。  
  
1. 子が`static`装飾<xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>される要素の装飾層を検索するには、メソッドを呼び出します。  
  
2. 親要素の子を列挙し、 <xref:System.Windows.Documents.AdornerLayer.Add%2A>メソッドを呼び出して、各子要素に装飾をバインドします。  
  
 次の例では、上に示した SimpleCircleAdorner を、 <xref:System.Windows.Controls.StackPanel>名前付きの*mystackpanel.xaml*の子にバインドします。  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.AdornerHitTestResult>
- [WPF での図形と基本描画の概要](../graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
- [イメージ、描画、およびビジュアルによる塗りつぶし](../graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [Drawing オブジェクトの概要](../graphics-multimedia/drawing-objects-overview.md)
- [方法トピック](adorners-how-to-topics.md)
