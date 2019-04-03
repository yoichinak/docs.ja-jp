---
title: 装飾の概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], about adorners
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
ms.openlocfilehash: 94075189d82e5d446b3058b944c789a4288c26ca
ms.sourcegitcommit: d938c39afb9216db377d0f0ecdaa53936a851059
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2019
ms.locfileid: "58634532"
---
# <a name="adorners-overview"></a>装飾の概要
装飾は特別な種類の<xref:System.Windows.FrameworkElement>ユーザーに視覚的な手掛かりを提供するために使用します。 装飾は、要素への機能ハンドル追加やコントロールに関する状態情報の提供など、さまざまな用途に使用できます。  
  
  
  
<a name="about_Adorners"></a>   
## <a name="about-adorners"></a>装飾について  
 <xref:System.Windows.Documents.Adorner>カスタム<xref:System.Windows.FrameworkElement>にバインドされている、<xref:System.Windows.UIElement>します。 装飾は、 <xref:System.Windows.Documents.AdornerLayer>、レンダリング サーフェイスでは、常に装飾対象の要素や装飾される要素のコレクションの上にあります。 装飾のレンダリングのレンダリングから独立して、<xref:System.Windows.UIElement>に装飾がバインドされています。 通常、装飾は、装飾対象の要素の左上に位置する標準の 2 次元座標の原点を使用して、バインド先の要素に対して相対的な位置に配置されます。  
  
 装飾の一般的な用途は、次のとおりです。  
  
-   追加の機能ハンドルを<xref:System.Windows.UIElement>をユーザーが何らかの方法 (サイズ変更、回転、位置変更など) で要素を操作できるようにします。  
  
-   視覚的なフィードバックによって、さまざまな状態を表示し、各種のイベントに応答する。  
  
-   上で視覚的装飾をオーバーレイ、<xref:System.Windows.UIElement>します。  
  
-   視覚的にマスクまたはの一部またはすべてをオーバーライドする<xref:System.Windows.UIElement>します。  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] は、視覚的要素を装飾する基本的なフレームワークを提供します。 次の表に示すのは、オブジェクトの装飾に使用する主な種類と、その用途の一覧です。 その後に、使用例をいくつか示します。  
  
|||  
|-|-|  
|<xref:System.Windows.Documents.Adorner>|具体的な装飾の実装すべての継承元になる抽象基本クラス。|  
|<xref:System.Windows.Documents.AdornerLayer>|装飾される 1 つ以上の要素に対する、装飾のレンダリング層を表すクラス。|  
|<xref:System.Windows.Documents.AdornerDecorator>|1 つの装飾層を要素のコレクションに関連付けることを可能にするクラス。|  
  
<a name="implement_custom_Adorner"></a>   
## <a name="implementing-a-custom-adorner"></a>カスタム装飾の実装  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] が提供する装飾フレームワークは、カスタム装飾の作成をサポートすることを主な目的としています。 抽象から継承するクラスを実装することで、カスタム装飾が作成された<xref:System.Windows.Documents.Adorner>クラス。  
  
> [!NOTE]
>  親を<xref:System.Windows.Documents.Adorner>は、<xref:System.Windows.Documents.AdornerLayer>をレンダリングする、 <xref:System.Windows.Documents.Adorner>、装飾される要素ではありません。  
  
 次の例では、簡単な装飾を実装するクラスを示します。 例を装飾するだけのものの角に丸みを<xref:System.Windows.UIElement>円でします。  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
 次の図に適用された simplecircleadorner です、<xref:System.Windows.Controls.TextBox>します。  
  
 ![装飾対象のテキスト ボックスを示すスクリーン ショット。](./media/adorners-overview/simplecircleadorner-textbox.png)  
  
<a name="rendering_behavior_for_Adorners"></a>   
## <a name="rendering-behavior-for-adorners"></a>装飾のレンダリング動作  
 装飾自体にはレンダリング動作が備わっていないので、装飾のレンダリングは装飾の実装側の責任で行う必要がある点に、注意が必要です。   一般的なレンダリングの動作を実装する方法は、オーバーライドする、<xref:System.Windows.UIElement.OnRender%2A>メソッドと 1 つ以上を使用して<xref:System.Windows.Media.DrawingContext>(上記の例で示す) のように、必要に応じて、装飾のビジュアルを表示するオブジェクト。  
  
> [!NOTE]
>  装飾層に配置されているすべてのものは、設定した他のすべてのスタイルの上に描画されます。 つまり、装飾は常に視覚的に最上位にあり、z オーダーを使用してオーバーライドすることはできません。  
  
<a name="adorner_events_hittest"></a>   
## <a name="events-and-hit-testing"></a>イベントおよびヒット テスト  
 装飾は、その他のように入力イベントを受信<xref:System.Windows.FrameworkElement>します。  装飾が入力イベントを受信する要素よりも高い z オーダーは、常に装飾にあるので (など<xref:System.Windows.UIElement.Drop>または<xref:System.Windows.UIElement.MouseMove>) 装飾対象の要素を基になるを想定している可能性があります。  装飾は、特定の入力イベントをリッスンし、それらのイベントを再度発生させることによって、下位にある装飾対象の要素に渡すことができます。  
  
 装飾の下の要素のヒット テストをパススルーを有効にするには、ヒット テストを設定<xref:System.Windows.UIElement.IsHitTestVisible%2A>プロパティを**false**で装飾します。  ヒット テストの詳細については、次を参照してください。  
  
 [ビジュアル層でのヒット テスト](../graphics-multimedia/hit-testing-in-the-visual-layer.md)。  
  
<a name="adorn_single_element"></a>   
## <a name="adorning-a-single-uielement"></a>単一の UIElement の装飾  
 特定の装飾をバインドする<xref:System.Windows.UIElement>、これらの手順に従います。  
  
1.  静的メソッドを呼び出す<xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>を取得する、<xref:System.Windows.Documents.AdornerLayer>オブジェクト、<xref:System.Windows.UIElement>装飾対象。 <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> 指定された、ビジュアル ツリーをウォーク<xref:System.Windows.UIElement>、し、最初に見つかった装飾層を返します。 (装飾層が見つからない場合、メソッドにより null が返されます)。  
  
2.  呼び出す、<xref:System.Windows.Documents.AdornerLayer.Add%2A>ターゲットに装飾をバインドするメソッド<xref:System.Windows.UIElement>します。  
  
 次の例では、simplecircleadorner に (上図) を参照、<xref:System.Windows.Controls.TextBox>という*myTextBox*します。  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
>  [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] を使用して、装飾を別の要素にバインドする方法は、現在サポートされていません。  
  
<a name="adorn_children_panel"></a>   
## <a name="adorning-the-children-of-a-panel"></a>パネルの子の装飾  
 子に装飾をバインドする、 <xref:System.Windows.Controls.Panel>、これらの手順に従います。  
  
1.  呼び出す、`static`メソッド<xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>子が装飾対象の要素の装飾層が見つかりません。  
  
2.  呼び出し、親要素の子を列挙、<xref:System.Windows.Documents.AdornerLayer.Add%2A>メソッドを各子要素に装飾をバインドします。  
  
 次の例は、simplecircleadorner 参照の子に (上記) を連結、<xref:System.Windows.Controls.StackPanel>という*myStackPanel*します。  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Media.AdornerHitTestResult>
- [WPF での図形と基本描画の概要](../graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
- [イメージ、描画、およびビジュアルによる塗りつぶし](../graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [Drawing オブジェクトの概要](../graphics-multimedia/drawing-objects-overview.md)
- [方法トピック](adorners-how-to-topics.md)
