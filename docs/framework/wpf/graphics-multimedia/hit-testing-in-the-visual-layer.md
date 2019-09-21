---
title: ビジュアル層でのヒット テスト
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit testing functionality [WPF]
- visual layer [WPF], hit testing functionality
ms.assetid: b1a64b61-14be-4d75-b89a-5c67bebb2c7b
ms.openlocfilehash: 92b7e8ffab001af4dba6c571fd06c64f2865b1e3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962118"
---
# <a name="hit-testing-in-the-visual-layer"></a>ビジュアル層でのヒット テスト
ここでは、ビジュアル層で提供されるヒット テスト機能の概要について説明します。 ヒットテストの<xref:System.Windows.Media.Visual>サポートにより、ジオメトリ値またはポイント値がのレンダリングされたコンテンツ内に収まるかどうかを判断できます。これにより、複数のオブジェクトを選択するための選択四角形などのユーザーインターフェイスの動作を実装できます。  

<a name="hit_testing_scenarios"></a>   
## <a name="hit-testing-scenarios"></a>ヒット テストのシナリオ  
 クラス<xref:System.Windows.UIElement>にはメソッド<xref:System.Windows.UIElement.InputHitTest%2A>が用意されています。これにより、特定の座標値を使用して、要素に対してヒットテストを行うことができます。 多くの場合、メソッド<xref:System.Windows.UIElement.InputHitTest%2A>は、要素のヒットテストを実装するために必要な機能を提供します。 ただし、ビジュアル層でのヒット テストを実装する必要があるシナリオもいくつか存在します。  
  
- 以外の<xref:System.Windows.UIElement>オブジェクトに対するヒットテスト:これは、<xref:System.Windows.UIElement>オブジェクト<xref:System.Windows.Media.DrawingVisual>やグラフィックスオブジェクトなど、オブジェクト以外のテストにヒットした場合に適用されます。  
  
- ジオメトリを使用したヒットテスト:これは、点の座標値ではなく、geometry オブジェクトを使用してヒットテストを行う必要がある場合に適用されます。  
  
- 複数のオブジェクトに対するヒットテスト:これは、重複するオブジェクトなど、複数のオブジェクトに対してヒットテストを行う必要がある場合に適用されます。 最初のビジュアルだけでなく、ジオメトリまたはポイントと交差するすべてのビジュアルの結果を取得できます。  
  
- ヒット<xref:System.Windows.UIElement>テストポリシーを無視します:これは、 <xref:System.Windows.UIElement>ヒットテストポリシーを無視する必要がある場合に適用されます。これは、要素が無効になっているかどうかなどの要因を考慮します。  
  
> [!NOTE]
> ビジュアル層でのテスト ヒットを示すコード サンプル全体については、「[DrawingVisuals を使用したヒット テストのサンプル](https://go.microsoft.com/fwlink/?LinkID=159994)」と「[Win32 相互運用によるヒット テストのサンプル](https://go.microsoft.com/fwlink/?LinkID=159995)」を参照してください。  
  
<a name="hit_testing_support"></a>   
## <a name="hit-testing-support"></a>ヒット テストのサポート  
 <xref:System.Windows.Media.VisualTreeHelper>クラスの<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>メソッドの目的は、geometry または point 座標の値が、コントロールやグラフィック要素など、特定のオブジェクトの描画されたコンテンツ内にあるかどうかを判断することです。 たとえば、ヒット テストを使用することで、オブジェクトの外接する四角形内でのマウス クリックが、円のジオメトリ内にあるかどうかを確認できます。 また、ヒット テストの既定の実装をオーバーライドして、独自のカスタム ヒット テスト計算を実行することもできます。  
  
 四角形以外のオブジェクトの領域と外接する四角形の関係を次の図に示します。  
  
 ![有効なヒットテスト領域の図](./media/wcpsdk-mmgraphics-visuals-hittest-1.png "wcpsdk_mmgraphics_visuals_hittest_1")  
有効なヒット テスト領域のダイアグラム  
  
<a name="hit_testing_and_z-order"></a>   
## <a name="hit-testing-and-z-order"></a>ヒット テストと z オーダー  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] のビジュアル層は、最上位のオブジェクトだけでなく、ポイントまたはジオメトリの下にあるすべてのオブジェクトに対するヒット テストをサポートします。 結果は z オーダーで返されます。 ただし、 <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>メソッドにパラメーターとして渡すビジュアルオブジェクトによって、ヒットテストの対象となるビジュアルツリーの部分が決まります。 ヒット テストは、ビジュアル ツリー全体またはその一部に対して実行できます。  
  
 次の図では、四角形と三角形の両方のオブジェクト上に円オブジェクトがあります。 Z オーダーの値が一番上にあるビジュアルオブジェクトのヒットテストのみを目的としている場合は、ビジュアルヒットテストの列挙体<xref:System.Windows.Media.HitTestResultBehavior.Stop>を設定して、 <xref:System.Windows.Media.HitTestResultCallback>最初の項目の後のヒットテストの走査を停止することができます。  
  
 ![ビジュアルツリーの z&#45;オーダーの図](./media/wcpsdk-mmgraphics-visuals-hittest-2.png "wcpsdk_mmgraphics_visuals_hittest_2")  
ビジュアル ツリーの z オーダーのダイアグラム  
  
 特定のポイントまたはジオメトリの下にあるすべてのビジュアルオブジェクトを列挙<xref:System.Windows.Media.HitTestResultBehavior.Continue>する場合<xref:System.Windows.Media.HitTestResultCallback>は、からを返します。 つまり、完全に隠されているものも含めて、他のオブジェクトの下にあるすべてのビジュアル オブジェクトに対してヒット テストを行うことができます。 詳細については、「ヒット テスト結果のコールバックの使用」のサンプル コードを参照してください。  
  
> [!NOTE]
> 透明なビジュアル オブジェクトのヒット テストも実行できます。  
  
<a name="using_default_hit_testing"></a>   
## <a name="using-default-hit-testing"></a>既定のヒット テストの使用  
 ポイントがビジュアルオブジェクトのジオメトリ内にあるかどうかを識別するには、 <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>メソッドを使用して、テスト対象のビジュアルオブジェクトとポイント座標値を指定します。 ビジュアル オブジェクトのパラメーターは、ヒット テストの検索のためのビジュアル ツリー内の開始点を識別します。 ビジュアルオブジェクトが、座標が含まれているビジュアルツリー内に存在する場合は、 <xref:System.Windows.Media.HitTestResult.VisualHit%2A> <xref:System.Windows.Media.HitTestResult>オブジェクトのプロパティに設定されます。 次<xref:System.Windows.Media.HitTestResult>に、 <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>メソッドからが返されます。 ヒットテストを行っているビジュアルサブツリーにポイントが含まれていない<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>場合`null`、はを返します。  
  
> [!NOTE]
> 既定のヒット テストでは、常に z オーダーで最上位のオブジェクトが返されます。 部分的または完全に隠されているものも含めて、すべてのビジュアル オブジェクトを識別するには、ヒット テストの結果のコールバックを使用します。  
  
 <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>メソッドの point パラメーターとして渡す座標値は、ヒットテストの対象となるビジュアルオブジェクトの座標空間に対して相対的である必要があります。 たとえば、入れ子になったビジュアル オブジェクトが親の座標空間の (100, 100) に定義されている場合、(0, 0) での子のビジュアルのヒット テストは、親の座標空間の (100, 100) でのヒット テストと同じになります。  
  
 次のコードは、ヒットテストに使用されるイベントを<xref:System.Windows.UIElement>キャプチャするために使用されるオブジェクトのマウスイベントハンドラーを設定する方法を示しています。  
  
 [!code-csharp[HitTestingOverview#100](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#100)]
 [!code-vb[HitTestingOverview#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#100)]  
  
### <a name="how-the-visual-tree-affects-hit-testing"></a>ヒット テストに対するビジュアル ツリーの影響  
 ビジュアル ツリー内の開始点によって、ヒット テストによるオブジェクトの列挙時に返されるオブジェクトが決定されます。 ヒット テストの対象となるオブジェクトが複数存在する場合、ビジュアル ツリー内の開始点として使用されるビジュアル オブジェクトは、対象となるすべてのオブジェクトの共通の先祖である必要があります。 たとえば、次の図のボタン要素と描画ビジュアルの両方のヒット テストを行う場合、ビジュアル ツリー内の開始点を、その両方の共通の先祖に設定する必要があります。 この場合、キャンバス要素がボタン要素と描画ビジュアルの両方の共通の先祖になります。  
  
 ![ビジュアルツリー階層の図](./media/wcpsdk-mmgraphics-visuals-overview-01.gif "wcpsdk_mmgraphics_visuals_overview_01")  
ビジュアル ツリー階層のダイアグラム  
  
> [!NOTE]
> プロパティ<xref:System.Windows.UIElement.IsHitTestVisible%2A>は、 <xref:System.Windows.UIElement>から派生したオブジェクトが、レンダリングされたコンテンツのある部分からのヒットテストの結果として返されるかどうかを宣言する値を取得または設定します。 これにより、ビジュアル ツリーを選択的に変更し、ヒット テストの対象となるビジュアル オブジェクトを決定することができます。  
  
<a name="using_a_hit_test_result_callback"></a>   
## <a name="using-a-hit-test-result-callback"></a>ヒット テスト結果のコールバックの使用  
 ジオメトリに指定した座標値が含まれるビジュアル ツリーのすべてのビジュアル オブジェクトを列挙できます。 これにより、他のビジュアル オブジェクトによって部分的または完全に隠されているものも含めて、すべてのビジュアル オブジェクトを識別することができます。 ビジュアルツリー内のビジュアルオブジェクトを列挙するに<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>は、メソッドをヒットテストコールバック関数と共に使用します。 ヒット テスト コールバック関数は、指定した座標値がビジュアル オブジェクトに含まれている場合にシステムによって呼び出されます。  
  
 ヒット テストの結果の列挙時には、ビジュアル ツリーを変更する操作を実行しないでください。 走査中のビジュアル ツリーに対してオブジェクトの追加または削除を行うと、予測不可能な動作を招く可能性があります。 メソッドから<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>制御が戻った後で、ビジュアルツリーを安全に変更できます。 ヒットテストの結果の列挙時に値を格納する<xref:System.Collections.ArrayList>ために、などのデータ構造を指定することもできます。  
  
 [!code-csharp[HitTestingOverview#101](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#101)]
 [!code-vb[HitTestingOverview#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#101)]  
  
 ヒット テストのコールバック メソッドは、ビジュアル ツリーの特定のビジュアル オブジェクトでヒット テストが識別されたときに、ユーザーが実行するアクションを定義します。 アクションを実行した後、他の<xref:System.Windows.Media.HitTestResultBehavior>ビジュアルオブジェクトの列挙を続行するかどうかを決定する値を返します。  
  
 [!code-csharp[HitTestingOverview#102](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#102)]
 [!code-vb[HitTestingOverview#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#102)]  
  
> [!NOTE]
> ヒットしたビジュアル オブジェクトの列挙の順序は、z オーダー順です。 z オーダーの最上位のビジュアル オブジェクトが最初に列挙されます。 その他のビジュアル オブジェクトは、z オーダーの上位から順に列挙されます。 この列挙の順序は、ビジュアルの描画順序に対応します。  
  
 ヒットテストコールバック関数では、を返す<xref:System.Windows.Media.HitTestResultBehavior.Stop>ことによっていつでもビジュアルオブジェクトの列挙を停止できます。  
  
 [!code-csharp[HitTestingOverview#103](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#103)]
 [!code-vb[HitTestingOverview#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#103)]  
  
<a name="using_a_hit_test_filter_callback"></a>   
## <a name="using-a-hit-test-filter-callback"></a>ヒット テスト フィルターのコールバックの使用  
 オプションのヒット テスト フィルターを使用して、ヒット テストの結果に渡されるオブジェクトを制限できます。 これにより、ヒット テストの結果でビジュアル ツリーの一部を処理する必要がない場合、その部分を無視できます。 ヒットテストフィルターを実装するには、ヒットテストフィルターのコールバック関数を定義し、メソッドを<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>呼び出すときにパラメーター値として渡します。  
  
 [!code-csharp[HitTestingOverview#104](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#104)]
 [!code-vb[HitTestingOverview#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#104)]  
  
 オプションのヒットテストフィルターのコールバック関数を指定しない場合は、 `null` <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>メソッドのパラメーターとして値を渡します。  
  
 [!code-csharp[HitTestingOverview#105](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#105)]
 [!code-vb[HitTestingOverview#105](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#105)]  
  
 ![ヒットテストフィルターを使用したビジュアルツリーの排除](./media/filteredvisualtree-01.png "FilteredVisualTree_01")  
ビジュアル ツリーの簡略化  
  
 ヒット テスト フィルターのコールバック関数を使用すると、描画されるコンテンツに指定した座標が含まれるすべてのビジュアルを列挙できます。 ただし、ヒット テストの結果のコールバック関数で、ビジュアル ツリーの一部の分岐を処理する必要がない場合、これらの分岐を無視できます。 ヒット テスト フィルターのコールバック関数の戻り値によって、ビジュアル オブジェクトの列挙体が実行するアクションの種類が決定されます。 たとえば、値を<xref:System.Windows.Media.HitTestFilterBehavior.ContinueSkipSelfAndChildren>返すと、ヒットテストの結果の列挙から現在のビジュアルオブジェクトとその子を削除できます。 つまり、ヒット テストの結果のコールバック関数は、列挙体でこれらのオブジェクトを認識しなくなります。 オブジェクトのビジュアル ツリーから余分なものを取り除くと、ヒット テストの結果の列挙体が渡されるときの処理を減らすことができます。 次のコード例では、フィルターはラベルとその子孫をスキップし、他のすべてのヒット テストを行います。  
  
 [!code-csharp[HitTestingOverview#106](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#106)]
 [!code-vb[HitTestingOverview#106](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#106)]  
  
> [!NOTE]
> ヒット テスト フィルターのコールバックは、ヒット テストの結果のコールバックが呼び出されない場合に呼び出されることがあります。  
  
<a name="overriding_default_hit_testing"></a>   
## <a name="overriding-default-hit-testing"></a>既定のヒット テストのオーバーライド  
 メソッドを<xref:System.Windows.Media.Visual.HitTestCore%2A>オーバーライドすると、ビジュアルオブジェクトの既定のヒットテストのサポートをオーバーライドできます。 これは、 <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>メソッドを呼び出すと、オーバーライドされた<xref:System.Windows.Media.Visual.HitTestCore%2A>の実装が呼び出されることを意味します。 座標がビジュアル オブジェクトの描画されるコンテンツの外側にあっても、ビジュアル オブジェクトの外接する四角形内でヒット テストが実行されると、オーバーライドされたメソッドが呼び出されます。  
  
 [!code-csharp[HitTestingOverview#107](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#107)]
 [!code-vb[HitTestingOverview#107](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#107)]  
  
 ビジュアル オブジェクトの外接する四角形と描画されるコンテンツの両方に対してヒット テストを行う必要が生じる場合もあります。 オーバーライド`PointHitTestParameters` <xref:System.Windows.Media.Visual.HitTestCore%2A>されたメソッドのパラメーター値を基本メソッドのパラメーターとして使用することで、ビジュアルオブジェクトの外接する四角形のヒットに基づいてアクションを実行し、次に対して2番目のヒットテストを実行できます。 <xref:System.Windows.Media.Visual.HitTestCore%2A>ビジュアルオブジェクトの描画されたコンテンツ。  
  
 [!code-csharp[HitTestingOverview#108](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#108)]
 [!code-vb[HitTestingOverview#108](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#108)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>
- <xref:System.Windows.Media.HitTestResult>
- <xref:System.Windows.Media.HitTestResultCallback>
- <xref:System.Windows.Media.HitTestFilterCallback>
- <xref:System.Windows.UIElement.IsHitTestVisible%2A>
- [ドローイングビジュアルサンプルを使用したヒットテスト](https://go.microsoft.com/fwlink/?LinkID=159994)
- [Win32 相互運用によるヒットテストのサンプル](https://go.microsoft.com/fwlink/?LinkID=159995)
- [ビジュアル内のジオメトリのヒット テストを実行する](how-to-hit-test-geometry-in-a-visual.md)
- [Win32 ホスト コンテナーを使用してヒット テストを実行する](how-to-hit-test-using-a-win32-host-container.md)
