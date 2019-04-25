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
ms.openlocfilehash: 01e10a4b0f0bf4959850caf3951ad4ea915edb4e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59121720"
---
# <a name="using-drawingvisual-objects"></a>DrawingVisual オブジェクトの使用
このトピックでは、使用する方法の概要を示します<xref:System.Windows.Media.DrawingVisual>内のオブジェクト、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ビジュアル層。  
  
<a name="drawingvisual_object"></a>   
## <a name="drawingvisual-object"></a>DrawingVisual オブジェクト  
 <xref:System.Windows.Media.DrawingVisual>は軽量の描画図形、画像、またはテキストを表示するために使用されるクラス。 このクラスが軽量と見なされる理由は、レイアウトやイベントの処理を行わないことで、パフォーマンスが向上するからです。 そのため、背景やクリップ アートの描画に適しています。  
  
<a name="drawingvisual_host_container"></a>   
## <a name="drawingvisual-host-container"></a>DrawingVisual ホスト コンテナー  
 使用するには<xref:System.Windows.Media.DrawingVisual>オブジェクト、オブジェクトのホスト コンテナーを作成する必要があります。 ホスト コンテナー オブジェクトはから派生する必要があります、<xref:System.Windows.FrameworkElement>レイアウトやイベント処理サポートを提供するクラス、<xref:System.Windows.Media.DrawingVisual>クラスがありません。 ホスト コンテナー オブジェクトの主な目的は子オブジェクトを格納することなので、ホスト コンテナー オブジェクトでは可視プロパティは表示されません。 ただし、<xref:System.Windows.UIElement.Visibility%2A>にホスト コンテナーのプロパティを設定する必要があります<xref:System.Windows.Visibility.Visible>。 そうしないと、その子要素のいずれもが表示されます。  
  
 ビジュアル オブジェクトのホスト コンテナー オブジェクトを作成するときにビジュアル オブジェクト参照を保存する必要があります、<xref:System.Windows.Media.VisualCollection>します。 使用して、<xref:System.Windows.Media.VisualCollection.Add%2A>ホスト コンテナーにビジュアル オブジェクトを追加します。 次の例では、ホスト コンテナー オブジェクトが作成、および 3 つのビジュアル オブジェクトに追加されます、<xref:System.Windows.Media.VisualCollection>します。  
  
 [!code-csharp[DrawingVisualSample#100](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[DrawingVisualSample#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#100)]  
  
> [!NOTE]
>  上記のコードの抽出元となった完全なコード サンプルについては、「[DrawingVisual を使用したヒット テストのサンプル](https://go.microsoft.com/fwlink/?LinkID=159994)」を参照してください。  
  
<a name="creating_drawingvisual_objects"></a>   
## <a name="creating-drawingvisual-objects"></a>Creating DrawingVisual オブジェクトの作成  
 作成するときに、<xref:System.Windows.Media.DrawingVisual>オブジェクトの描画コンテンツを持ちません。 テキスト、グラフィックス、またはイメージのコンテンツを追加するには、オブジェクトの取得することによって<xref:System.Windows.Media.DrawingContext>とそこに描画します。 A<xref:System.Windows.Media.DrawingContext>呼び出しによって返される、<xref:System.Windows.Media.DrawingVisual.RenderOpen%2A>のメソッドを<xref:System.Windows.Media.DrawingVisual>オブジェクト。  
  
 四角形を描画するために、<xref:System.Windows.Media.DrawingContext>を使用して、<xref:System.Windows.Media.DrawingContext.DrawRectangle%2A>のメソッド、<xref:System.Windows.Media.DrawingContext>オブジェクト。 他の種類のコンテンツを描画するための同様のメソッドもあります。 描画コンテンツを終了したら、 <xref:System.Windows.Media.DrawingContext>、呼び出し、<xref:System.Windows.Media.DrawingContext.Close%2A>を終了するメソッド、<xref:System.Windows.Media.DrawingContext>内容を保持します。  
  
 次の例では、<xref:System.Windows.Media.DrawingVisual>オブジェクトが作成され、四角形の描画にその<xref:System.Windows.Media.DrawingContext>します。  
  
 [!code-csharp[DrawingVisualSample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[DrawingVisualSample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
<a name="creating_overrides"></a>   
## <a name="creating-overrides-for-frameworkelement-members"></a>FrameworkElement メンバーのオーバーライドの作成  
 ホスト コンテナー オブジェクトは、ビジュアル オブジェクトのコレクションを管理します。 ホスト コンテナーが派生クラスのメンバー オーバーライドを実装する必要があります<xref:System.Windows.FrameworkElement>クラス。  
  
 オーバーライドする必要がある 2 つのメンバーを次に示します。  
  
-   <xref:System.Windows.FrameworkElement.GetVisualChild%2A>:子要素のコレクションから指定したインデックス位置にある子を返します。  
  
-   <xref:System.Windows.FrameworkElement.VisualChildrenCount%2A>:この要素内でビジュアル子要素の数を取得します。  
  
 次の例では、2 つのオーバーライド<xref:System.Windows.FrameworkElement>メンバーを実装します。  
  
 [!code-csharp[DrawingVisualSample#102](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#102)]
 [!code-vb[DrawingVisualSample#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#102)]  
  
<a name="providing_hit_testing_support"></a>   
## <a name="providing-hit-testing-support"></a>ヒット テストのサポート  
 ホスト コンテナー オブジェクトがすべて表示するプロパティが表示されない場合でもイベント処理を提供することができます-ただし、その<xref:System.Windows.UIElement.Visibility%2A>にプロパティを設定する必要があります<xref:System.Windows.Visibility.Visible>します。 これにより、マウス イベント (マウスの左ボタンのリリースなど) をトラップできる、ホスト コンテナーのイベント処理ルーチンを作成できます。 イベント処理ルーチンでは呼び出すことによって、ヒット テストを実装できますし、<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>メソッド。 メソッドの<xref:System.Windows.Media.HitTestResultCallback>パラメーターは、ヒット テストの結果として得られるアクションを決定するために使用できるユーザー定義のプロシージャを表します。  
  
 次の例では、ホスト コンテナー オブジェクトとその子に対してヒット テストのサポートを実装しています。  
  
 [!code-csharp[DrawingVisualSample#103](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#103)]
 [!code-vb[DrawingVisualSample#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#103)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.DrawingVisual>
- <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>
- [WPF グラフィックス レンダリングの概要](wpf-graphics-rendering-overview.md)
- [ビジュアル層でのヒット テスト](hit-testing-in-the-visual-layer.md)
