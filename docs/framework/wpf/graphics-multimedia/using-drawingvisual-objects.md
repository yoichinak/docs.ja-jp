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
ms.openlocfilehash: 4e6fc89b64f7b0acc1a0077708d567eb97e2868e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962830"
---
# <a name="using-drawingvisual-objects"></a>DrawingVisual オブジェクトの使用
このトピックでは、 <xref:System.Windows.Media.DrawingVisual> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ビジュアル層でオブジェクトを使用する方法の概要について説明します。  
  
<a name="drawingvisual_object"></a>   
## <a name="drawingvisual-object"></a>DrawingVisual オブジェクト  
 は、図形、画像、またはテキストを表示するために使用される軽量の描画クラスです。<xref:System.Windows.Media.DrawingVisual> このクラスが軽量と見なされる理由は、レイアウトやイベントの処理を行わないことで、パフォーマンスが向上するからです。 そのため、背景やクリップ アートの描画に適しています。  
  
<a name="drawingvisual_host_container"></a>   
## <a name="drawingvisual-host-container"></a>DrawingVisual ホスト コンテナー  
 オブジェクトを使用<xref:System.Windows.Media.DrawingVisual>するには、オブジェクトのホストコンテナーを作成する必要があります。 ホストコンテナーオブジェクトは<xref:System.Windows.FrameworkElement>クラスから派生する必要があります。これにより、クラスには<xref:System.Windows.Media.DrawingVisual>欠けているレイアウトとイベント処理のサポートが提供されます。 ホスト コンテナー オブジェクトの主な目的は子オブジェクトを格納することなので、ホスト コンテナー オブジェクトでは可視プロパティは表示されません。 ただし、 <xref:System.Windows.UIElement.Visibility%2A>ホストコンテナーのプロパティはに<xref:System.Windows.Visibility.Visible>設定する必要があります。それ以外の場合、子要素は表示されません。  
  
 ビジュアルオブジェクトのホストコンテナーオブジェクトを作成する場合は、ビジュアルオブジェクト参照<xref:System.Windows.Media.VisualCollection>をに格納する必要があります。 <xref:System.Windows.Media.VisualCollection.Add%2A>メソッドを使用して、ホストコンテナーにビジュアルオブジェクトを追加します。 次の例では、ホストコンテナーオブジェクトが作成され、3つのビジュアルオブジェクトが<xref:System.Windows.Media.VisualCollection>に追加されます。  
  
 [!code-csharp[DrawingVisualSample#100](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[DrawingVisualSample#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#100)]  
  
> [!NOTE]
> 上記のコードの抽出元となった完全なコード サンプルについては、「[DrawingVisual を使用したヒット テストのサンプル](https://go.microsoft.com/fwlink/?LinkID=159994)」を参照してください。  
  
<a name="creating_drawingvisual_objects"></a>   
## <a name="creating-drawingvisual-objects"></a>Creating DrawingVisual オブジェクトの作成  
 オブジェクトを<xref:System.Windows.Media.DrawingVisual>作成するときに、描画コンテンツはありません。 テキスト、グラフィックス、または画像のコンテンツを追加するには、 <xref:System.Windows.Media.DrawingContext>オブジェクトのを取得して描画します。 は<xref:System.Windows.Media.DrawingContext> <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> 、オブジェクト<xref:System.Windows.Media.DrawingVisual>のメソッドを呼び出すことによって返されます。  
  
 に四角形<xref:System.Windows.Media.DrawingContext>を描画するには、 <xref:System.Windows.Media.DrawingContext>オブジェクト<xref:System.Windows.Media.DrawingContext.DrawRectangle%2A>のメソッドを使用します。 他の種類のコンテンツを描画するための同様のメソッドもあります。 に<xref:System.Windows.Media.DrawingContext>コンテンツの描画が完了したら、 <xref:System.Windows.Media.DrawingContext.Close%2A>メソッドを呼び出してを閉じ<xref:System.Windows.Media.DrawingContext> 、コンテンツを永続化します。  
  
 次の例<xref:System.Windows.Media.DrawingVisual>では、オブジェクトが作成され、その<xref:System.Windows.Media.DrawingContext>に四角形が描画されます。  
  
 [!code-csharp[DrawingVisualSample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[DrawingVisualSample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
<a name="creating_overrides"></a>   
## <a name="creating-overrides-for-frameworkelement-members"></a>FrameworkElement メンバーのオーバーライドの作成  
 ホスト コンテナー オブジェクトは、ビジュアル オブジェクトのコレクションを管理します。 そのためには、ホストコンテナーが派生<xref:System.Windows.FrameworkElement>クラスのメンバーオーバーライドを実装する必要があります。  
  
 オーバーライドする必要がある 2 つのメンバーを次に示します。  
  
- <xref:System.Windows.FrameworkElement.GetVisualChild%2A>:子要素のコレクションから、指定したインデックス位置にある子を返します。  
  
- <xref:System.Windows.FrameworkElement.VisualChildrenCount%2A> :この要素内でビジュアル子要素の数を取得します。  
  
 次の例では、2つ<xref:System.Windows.FrameworkElement>のメンバーのオーバーライドが実装されています。  
  
 [!code-csharp[DrawingVisualSample#102](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#102)]
 [!code-vb[DrawingVisualSample#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#102)]  
  
<a name="providing_hit_testing_support"></a>   
## <a name="providing-hit-testing-support"></a>ヒット テストのサポート  
 ホストコンテナーオブジェクトは、表示されるプロパティが表示されない場合でもイベント処理を提供<xref:System.Windows.UIElement.Visibility%2A>できます。ただし、 <xref:System.Windows.Visibility.Visible>プロパティをに設定する必要があります。 これにより、マウス イベント (マウスの左ボタンのリリースなど) をトラップできる、ホスト コンテナーのイベント処理ルーチンを作成できます。 イベント処理ルーチンは、メソッドを<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>呼び出すことによってヒットテストを実装できます。 メソッドの<xref:System.Windows.Media.HitTestResultCallback>パラメーターは、ヒットテストの結果のアクションを決定するために使用できるユーザー定義プロシージャを参照します。  
  
 次の例では、ホスト コンテナー オブジェクトとその子に対してヒット テストのサポートを実装しています。  
  
 [!code-csharp[DrawingVisualSample#103](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#103)]
 [!code-vb[DrawingVisualSample#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#103)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.DrawingVisual>
- <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>
- [WPF グラフィックス レンダリングの概要](wpf-graphics-rendering-overview.md)
- [ビジュアル層でのヒット テスト](hit-testing-in-the-visual-layer.md)
