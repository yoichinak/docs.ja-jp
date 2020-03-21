---
title: 装飾の概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], about adorners
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
ms.openlocfilehash: b41c1f10f7e1b7c1799fd27270a3eeb9899ceeb6
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111180"
---
# <a name="adorners-overview"></a>装飾の概要

装飾は、ユーザーに視覚的な手掛<xref:System.Windows.FrameworkElement>かりを提供するために使用される特殊なタイプの. 装飾は、要素への機能ハンドル追加やコントロールに関する状態情報の提供など、さまざまな用途に使用できます。

## <a name="about-adorners"></a>装飾について

は<xref:System.Windows.Documents.Adorner>、 に<xref:System.Windows.FrameworkElement>バインドされるカスタムです<xref:System.Windows.UIElement>。 装飾は、装飾された要素または装飾<xref:System.Windows.Documents.AdornerLayer>された要素のコレクションの上に常に表示されるレンダリング サーフェスでレンダリングされます。 装飾のレンダリングは、装飾<xref:System.Windows.UIElement>がバインドされているレンダリングから独立しています。 装飾は通常、装飾された要素の左上にある標準の 2D 座標原点を使用して、バインド先の要素に対して相対的に配置されます。

装飾の一般的な用途は、次のとおりです。

- 機能ハンドルを追加して<xref:System.Windows.UIElement>、ユーザーが何らかの方法で要素を操作できるようにする (サイズ変更、回転、位置変更など)。
- 視覚的なフィードバックによって、さまざまな状態を表示し、各種のイベントに応答する。
- 上の視覚的な装飾を<xref:System.Windows.UIElement>オーバーレイします。
- を視覚的にマスクするか、または一部または<xref:System.Windows.UIElement>すべてをオーバーライドします。

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] は、視覚的要素を装飾する基本的なフレームワークを提供します。 次の表に示すのは、オブジェクトの装飾に使用する主な種類と、その用途の一覧です。 次に、いくつかの使用例を示します。

|||
|-|-|
|<xref:System.Windows.Documents.Adorner>|具体的な装飾の実装すべての継承元になる抽象基本クラス。|
|<xref:System.Windows.Documents.AdornerLayer>|装飾される 1 つ以上の要素に対する、装飾のレンダリング層を表すクラス。|
|<xref:System.Windows.Documents.AdornerDecorator>|1 つの装飾層を要素のコレクションに関連付けることを可能にするクラス。|

## <a name="implementing-a-custom-adorner"></a>カスタム装飾の実装

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] が提供する装飾フレームワークは、カスタム装飾の作成をサポートすることを主な目的としています。 カスタム装飾は、抽象<xref:System.Windows.Documents.Adorner>クラスから継承するクラスを実装することによって作成されます。

> [!NOTE]
> の<xref:System.Windows.Documents.Adorner>親は、装飾<xref:System.Windows.Documents.AdornerLayer>されている要素ではなく<xref:System.Windows.Documents.Adorner>、をレンダリングします。

次の例では、簡単な装飾を実装するクラスを示します。 この例では、単に円を持つ a<xref:System.Windows.UIElement>の角を飾ります。

[!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
[!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]
  
次の図は、に適用されるシンプルな円アドナー<xref:System.Windows.Controls.TextBox>を示しています。

![装飾されたテキスト ボックスを示すスクリーンショット。](./media/adorners-overview/simplecircleadorner-textbox.png)

## <a name="rendering-behavior-for-adorners"></a>装飾のレンダリング動作

装飾自体にはレンダリング動作が備わっていないので、装飾のレンダリングは装飾の実装側の責任で行う必要がある点に、注意が必要です。 レンダリング動作を実装する一般的な方法は、<xref:System.Windows.UIElement.OnRender%2A>メソッドをオーバーライドし、必要<xref:System.Windows.Media.DrawingContext>に応じて 1 つまたは複数のオブジェクトを使用して装飾のビジュアルをレンダリングすることです (上記の例を参照)。

> [!NOTE]
> 装飾層に配置されているすべてのものは、設定した他のすべてのスタイルの上に描画されます。 つまり、装飾は常に視覚的に最上位にあり、z オーダーを使用してオーバーライドすることはできません。

## <a name="events-and-hit-testing"></a>イベントおよびヒット テスト

装飾は、他<xref:System.Windows.FrameworkElement>の .  装飾は常に装飾要素よりも高い z オーダーを持つため、装飾は、基になる装飾された要素を対象とする入力イベント<xref:System.Windows.UIElement.Drop> <xref:System.Windows.UIElement.MouseMove>(または など) を受け取ります。  装飾は、特定の入力イベントをリッスンし、それらのイベントを再度発生させることによって、下位にある装飾対象の要素に渡すことができます。

装飾の下の要素のパススルー ヒット テストを有効にするには、装飾のヒット<xref:System.Windows.UIElement.IsHitTestVisible%2A>テスト プロパティを**false**に設定します。  ヒット テストの詳細については、「[ビジュアル レイヤーでのヒット テスト](../graphics-multimedia/hit-testing-in-the-visual-layer.md)」を参照してください。

## <a name="adorning-a-single-uielement"></a>単一の UIElement の装飾

装飾を特定<xref:System.Windows.UIElement>の にバインドするには、次の手順を実行します。

1. 装飾されるオブジェクトを<xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A><xref:System.Windows.Documents.AdornerLayer>取得<xref:System.Windows.UIElement>するには、static メソッドを呼び出します。 <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>指定された<xref:System.Windows.UIElement>から始めてビジュアル ツリーを上に移動し、最初に見つかった装飾レイヤを返します。 (装飾層が見つからない場合、メソッドにより null が返されます)。

2. メソッドを<xref:System.Windows.Documents.AdornerLayer.Add%2A>呼び出して、装飾をターゲットにバインド<xref:System.Windows.UIElement>します。

 次の例では、上に示す名前の*myTextBox*に<xref:System.Windows.Controls.TextBox>SimpleCircleAdorner をバインドします。

 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]

> [!NOTE]
> [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] を使用して、装飾を別の要素にバインドする方法は、現在サポートされていません。

## <a name="adorning-the-children-of-a-panel"></a>パネルの子の装飾

の子に装飾をバインドするには<xref:System.Windows.Controls.Panel>、次の手順を実行します。

1. 子が`static`装飾<xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>される要素の装飾レイヤーを検索するには、メソッドを呼び出します。

2. 親要素の子を列挙し、各子要素<xref:System.Windows.Documents.AdornerLayer.Add%2A>に装飾をバインドするメソッドを呼び出します。

次の例では、名前の付いた<xref:System.Windows.Controls.StackPanel>*myStackPanel*の子に SimpleCircleAdorner (上図) をバインドします。

[!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
[!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.AdornerHitTestResult>
- [WPF での図形と基本描画の概要](../graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
- [イメージ、描画、およびビジュアルによる塗りつぶし](../graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [Drawing オブジェクトの概要](../graphics-multimedia/drawing-objects-overview.md)
- [ハウツートピック](adorners-how-to-topics.md)
