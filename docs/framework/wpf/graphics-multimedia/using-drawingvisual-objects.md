---
title: DrawingVisual オブジェクトの使用
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- visual layer [WPF], DrawingVisual objects
- DrawingVisual objects in visual layer [WPF]
ms.assetid: 0b4e711d-e640-40cb-81c3-8f5c59909b7d
ms.openlocfilehash: 9d67fbc0d9716c9df3935232c6c7e579b50d55bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148323"
---
# <a name="using-drawingvisual-objects"></a>DrawingVisual オブジェクトの使用
このトピックでは、ビジュアル レイヤーでオブジェクト<xref:System.Windows.Media.DrawingVisual>を使用する[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]方法の概要を説明します。  
  
<a name="drawingvisual_object"></a>
## <a name="drawingvisual-object"></a>DrawingVisual オブジェクト  
 <xref:System.Windows.Media.DrawingVisual>は、図形、イメージ、またはテキストのレンダリングに使用される軽量の描画クラスです。 このクラスが軽量と見なされる理由は、レイアウトやイベントの処理を行わないことで、パフォーマンスが向上するからです。 そのため、背景やクリップ アートの描画に適しています。  
  
<a name="drawingvisual_host_container"></a>
## <a name="drawingvisual-host-container"></a>DrawingVisual ホスト コンテナー  
 オブジェクトを使用<xref:System.Windows.Media.DrawingVisual>するには、オブジェクトのホストコンテナを作成する必要があります。 ホスト コンテナー オブジェクトは<xref:System.Windows.FrameworkElement>、クラスから派生する<xref:System.Windows.Media.DrawingVisual>必要があります。 ホスト コンテナー オブジェクトの主な目的は子オブジェクトを格納することなので、ホスト コンテナー オブジェクトでは可視プロパティは表示されません。 ただし、ホスト<xref:System.Windows.UIElement.Visibility%2A>コンテナーのプロパティは に<xref:System.Windows.Visibility.Visible>設定する必要があります。それ以外の場合、子要素は表示されません。  
  
 ビジュアル オブジェクトのホスト コンテナー オブジェクトを作成する場合は、ビジュアル オブジェクト参照を<xref:System.Windows.Media.VisualCollection>に格納する必要があります。 このメソッド<xref:System.Windows.Media.VisualCollection.Add%2A>を使用して、ホスト コンテナーにビジュアル オブジェクトを追加します。 次の例では、ホスト コンテナー オブジェクトが作成され、3 つのビジュアル オブジェクト<xref:System.Windows.Media.VisualCollection>がに追加されます。  
  
 [!code-csharp[DrawingVisualSample#100](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[DrawingVisualSample#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#100)]  
  
> [!NOTE]
> 上記のコードの抽出元となった完全なコード サンプルについては、「[DrawingVisual を使用したヒット テストのサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Visual%20Layer/DrawingVisual)」を参照してください。  
  
<a name="creating_drawingvisual_objects"></a>
## <a name="creating-drawingvisual-objects"></a>Creating DrawingVisual オブジェクトの作成  
 オブジェクトを<xref:System.Windows.Media.DrawingVisual>作成する場合、オブジェクトには描画コンテンツがありません。 オブジェクト<xref:System.Windows.Media.DrawingContext>を取得して描画することにより、テキスト、グラフィックス、またはイメージコンテンツを追加できます。 A<xref:System.Windows.Media.DrawingContext>は<xref:System.Windows.Media.DrawingVisual>、オブジェクトの<xref:System.Windows.Media.DrawingVisual.RenderOpen%2A>メソッドを呼び出すことによって返されます。  
  
 に四角形を描画するには<xref:System.Windows.Media.DrawingContext>、オブジェクトの<xref:System.Windows.Media.DrawingContext.DrawRectangle%2A>メソッドを<xref:System.Windows.Media.DrawingContext>使用します。 他の種類のコンテンツを描画するための同様のメソッドもあります。 コンテンツの描画が完了したら<xref:System.Windows.Media.DrawingContext>、 メソッドを<xref:System.Windows.Media.DrawingContext.Close%2A>呼び出して、<xref:System.Windows.Media.DrawingContext>を閉じてコンテンツを保持します。  
  
 次の例では、<xref:System.Windows.Media.DrawingVisual>オブジェクトが作成され、四角形がオブジェクトに<xref:System.Windows.Media.DrawingContext>描画されます。  
  
 [!code-csharp[DrawingVisualSample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[DrawingVisualSample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
<a name="creating_overrides"></a>
## <a name="creating-overrides-for-frameworkelement-members"></a>FrameworkElement メンバーのオーバーライドの作成  
 ホスト コンテナー オブジェクトは、ビジュアル オブジェクトのコレクションを管理します。 そのためには、ホスト コンテナーが派生<xref:System.Windows.FrameworkElement>クラスのメンバーオーバーライドを実装する必要があります。  
  
 オーバーライドする必要がある 2 つのメンバーを次に示します。  
  
- <xref:System.Windows.FrameworkElement.GetVisualChild%2A>: 子要素のコレクションから、指定したインデックス位置にある子を返します。  
  
- <xref:System.Windows.FrameworkElement.VisualChildrenCount%2A>: この要素内のビジュアル子要素の数を取得します。  
  
 次の例では、2 つの<xref:System.Windows.FrameworkElement>メンバーのオーバーライドが実装されています。  
  
 [!code-csharp[DrawingVisualSample#102](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#102)]
 [!code-vb[DrawingVisualSample#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#102)]  
  
<a name="providing_hit_testing_support"></a>
## <a name="providing-hit-testing-support"></a>ヒット テストのサポート  
 ホスト コンテナ オブジェクトは、表示されるプロパティを表示しない場合でもイベント処理を<xref:System.Windows.UIElement.Visibility%2A><xref:System.Windows.Visibility.Visible>提供できますが、プロパティは に設定する必要があります。 これにより、マウス イベント (マウスの左ボタンのリリースなど) をトラップできる、ホスト コンテナーのイベント処理ルーチンを作成できます。 イベント処理ルーチンは、メソッドを呼び出すことによってヒット テスト<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>を実装できます。 メソッドの<xref:System.Windows.Media.HitTestResultCallback>パラメーターは、ヒット テストの結果のアクションを決定するために使用できるユーザー定義のプロシージャを参照します。  
  
 次の例では、ホスト コンテナー オブジェクトとその子に対してヒット テストのサポートを実装しています。  
  
 [!code-csharp[DrawingVisualSample#103](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#103)]
 [!code-vb[DrawingVisualSample#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#103)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.DrawingVisual>
- <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>
- [WPF グラフィックス レンダリングの概要](wpf-graphics-rendering-overview.md)
- [ビジュアル層でのヒット テスト](hit-testing-in-the-visual-layer.md)
