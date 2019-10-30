---
title: 装飾の概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], about adorners
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
ms.openlocfilehash: 22d9b1eddbb6db47fb15deebf94cfc5f8d37a380
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040847"
---
# <a name="adorners-overview"></a>装飾の概要

装飾は特殊な種類の <xref:System.Windows.FrameworkElement>であり、ユーザーに視覚的な手掛かりを提供するために使用されます。 装飾は、要素への機能ハンドル追加やコントロールに関する状態情報の提供など、さまざまな用途に使用できます。

## <a name="about-adorners"></a>装飾について

<xref:System.Windows.Documents.Adorner> は、<xref:System.Windows.UIElement>にバインドされているカスタム <xref:System.Windows.FrameworkElement> です。 装飾は <xref:System.Windows.Documents.AdornerLayer>でレンダリングされます。これは、常に装飾された要素または装飾要素のコレクションの上にあるレンダリングサーフェイスです。 装飾のレンダリングは、装飾がバインドされている <xref:System.Windows.UIElement> のレンダリングからは独立しています。 通常、装飾は、装飾対象の要素の左上に位置する標準の 2 次元座標の原点を使用して、バインド先の要素に対して相対的な位置に配置されます。

装飾の一般的な用途は、次のとおりです。

- ユーザーが何らかの方法 (サイズ変更、回転、位置合わせなど) で要素を操作できるようにする <xref:System.Windows.UIElement> に機能ハンドルを追加する。
- 視覚的なフィードバックによって、さまざまな状態を表示し、各種のイベントに応答する。
- <xref:System.Windows.UIElement>に視覚的な装飾をオーバーレイします。
- <xref:System.Windows.UIElement>の一部またはすべてを視覚的にマスクまたはオーバーライドします。

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] は、視覚的要素を装飾する基本的なフレームワークを提供します。 次の表に示すのは、オブジェクトの装飾に使用する主な種類と、その用途の一覧です。 いくつかの使用例を次に示します。

|||
|-|-|
|<xref:System.Windows.Documents.Adorner>|具体的な装飾の実装すべての継承元になる抽象基本クラス。|
|<xref:System.Windows.Documents.AdornerLayer>|装飾される 1 つ以上の要素に対する、装飾のレンダリング層を表すクラス。|
|<xref:System.Windows.Documents.AdornerDecorator>|1 つの装飾層を要素のコレクションに関連付けることを可能にするクラス。|

## <a name="implementing-a-custom-adorner"></a>カスタム装飾の実装

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] が提供する装飾フレームワークは、カスタム装飾の作成をサポートすることを主な目的としています。 カスタム装飾は、抽象 <xref:System.Windows.Documents.Adorner> クラスを継承するクラスを実装することによって作成されます。

> [!NOTE]
> <xref:System.Windows.Documents.Adorner> の親は、装飾される要素ではなく、<xref:System.Windows.Documents.Adorner>をレンダリングする <xref:System.Windows.Documents.AdornerLayer> です。

次の例では、簡単な装飾を実装するクラスを示します。 この装飾の例では、<xref:System.Windows.UIElement> の角を円でものます。

[!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
[!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]
  
次の図は、<xref:System.Windows.Controls.TextBox>に適用される SimpleCircleAdorner を示しています。

![装飾されたテキストボックスを示すスクリーンショット。](./media/adorners-overview/simplecircleadorner-textbox.png)

## <a name="rendering-behavior-for-adorners"></a>装飾のレンダリング動作

装飾自体にはレンダリング動作が備わっていないので、装飾のレンダリングは装飾の実装側の責任で行う必要がある点に、注意が必要です。 レンダリング動作を実装する一般的な方法として、<xref:System.Windows.UIElement.OnRender%2A> メソッドをオーバーライドし、1つまたは複数の <xref:System.Windows.Media.DrawingContext> オブジェクトを使用して、必要に応じて装飾のビジュアルをレンダリングします (上記の例を参照)。

> [!NOTE]
> 装飾層に配置されているすべてのものは、設定した他のすべてのスタイルの上に描画されます。 つまり、装飾は常に視覚的に最上位にあり、z オーダーを使用してオーバーライドすることはできません。

## <a name="events-and-hit-testing"></a>イベントおよびヒット テスト

装飾は、他の <xref:System.Windows.FrameworkElement>と同様に入力イベントを受け取ります。  装飾は常に、それがもの要素よりも高い z オーダーを持つため、装飾は、基になる装飾対象の要素を対象とする可能性がある入力イベント (<xref:System.Windows.UIElement.Drop> や <xref:System.Windows.UIElement.MouseMove>など) を受け取ります。  装飾は、特定の入力イベントをリッスンし、それらのイベントを再度発生させることによって、下位にある装飾対象の要素に渡すことができます。

装飾の下で要素のパススルーヒットテストを有効にするには、装飾でヒットテストの <xref:System.Windows.UIElement.IsHitTestVisible%2A> プロパティを**false**に設定します。  ヒットテストの詳細については、「[ビジュアル層でのヒットテスト](../graphics-multimedia/hit-testing-in-the-visual-layer.md)」を参照してください。

## <a name="adorning-a-single-uielement"></a>単一の UIElement の装飾

特定の <xref:System.Windows.UIElement>に装飾をバインドするには、次の手順を実行します。

1. 静的メソッド <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> を呼び出して、<xref:System.Windows.UIElement> に装飾する <xref:System.Windows.Documents.AdornerLayer> オブジェクトを取得します。 <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> は、指定された <xref:System.Windows.UIElement>を開始位置としてビジュアルツリーをウォークし、最初に見つかった装飾層を返します。 (装飾層が見つからない場合、メソッドにより null が返されます)。

2. <xref:System.Windows.Documents.AdornerLayer.Add%2A> メソッドを呼び出して、装飾をターゲット <xref:System.Windows.UIElement>にバインドします。

 次の例では、SimpleCircleAdorner (上の図を参照) を*myTextBox*という名前の <xref:System.Windows.Controls.TextBox> にバインドします。

 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]

> [!NOTE]
> [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] を使用して、装飾を別の要素にバインドする方法は、現在サポートされていません。

## <a name="adorning-the-children-of-a-panel"></a>パネルの子の装飾

装飾を <xref:System.Windows.Controls.Panel>の子にバインドするには、次の手順を実行します。

1. `static` メソッド <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> を呼び出して、子を装飾する要素の装飾層を検索します。

2. 親要素の子を列挙し、<xref:System.Windows.Documents.AdornerLayer.Add%2A> メソッドを呼び出して、各子要素に装飾をバインドします。

次の例では、SimpleCircleAdorner (上の図を参照) を*mystackpanel.xaml*という名前の <xref:System.Windows.Controls.StackPanel> の子にバインドします。

[!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
[!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.AdornerHitTestResult>
- [WPF での図形と基本描画の概要](../graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
- [イメージ、描画、およびビジュアルによる塗りつぶし](../graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [Drawing オブジェクトの概要](../graphics-multimedia/drawing-objects-overview.md)
- [方法トピック](adorners-how-to-topics.md)
