---
title: 3-D 変換の概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3-D transformations
- transformations [WPF], 3-D
ms.assetid: e45e555d-ac1e-4b36-aced-e433afe7f27f
ms.openlocfilehash: bbb3c413148bd2e2ab8de8a1a725f2d9a8acf2f6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59190632"
---
# <a name="3-d-transformations-overview"></a>3-D 変換の概要
このトピックでは、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] グラフィックス システムで 3-D モデルに変換を適用する方法について説明します。 変換を使うと、モデルを定義する基本の値を変更することなく、モデルの位置、サイズ、向きを変更できます。  

## <a name="3-d-coordinate-space"></a>3-D 座標空間  
 3-D グラフィックス コンテンツ[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]は、要素にカプセル化<xref:System.Windows.Controls.Viewport3D>、2 次元要素の構造に含めることができます。 グラフィックス システムは、Viewport3D を、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 内の他の多くの要素と同じ 2 次元のビジュアル要素として処理します。 Viewport3D は、3 次元シーンのウィンドウ (ビューポート) として機能します。 より正確には、3-D シーンが投影されるサーフェイスです。  同じシーン グラフ内で他の 2-D 描画オブジェクトと共に Viewport3D を使うことができますが、Viewport3D 内の 2-D オブジェクトと 3-D オブジェクトを相互に貫通させることはできません。 以下の説明で、座標空間は Viewport3D 要素に含まれています。  
  
 2-D グラフィックス用の [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 座標系の原点は、レンダリング サーフェイスの (通常は画面) の左上にあります。 2-D システムでは、x 軸の正の値は右に向かって大きくなり、y 軸の正の値は下に向かって大きくなります。 一方、3-D 座標系では、原点は画面の中央にあり、x 軸の正の値は右に向かって大きくなりますが、y 軸の正の値は上に向かって大きくなり、z 軸の正の値は原点から手前に向かって大きくなります。  
  
 ![座標系](./media/coordsystem-1.png "CoordSystem 1")  
座標系の比較  
  
 これらの軸によって定義される空間は、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 内の 3-D オブジェクトのための静止した基準枠です。 この空間内にモデルを構築し、それらを表示するためのライトとカメラを作成するときは、この静止した基準枠 ("ワールド空間") と、モデルに変換を適用するときにモデルごとに作成するローカルな基準枠を区別することをお勧めします。 また、ワールド空間内のオブジェクトは、ライトとカメラの設定により、まったく違って見えたり、またはまったく見えなくなることがありますが、カメラの位置によってワールド空間内のオブジェクトの場所が変化することはないことに注意してください。  
  
## <a name="transforming-models"></a>モデルの変換  
 モデルを作成するとき、モデルにはシーン内で特定の位置があります。 モデルをシーン内で移動したり、回転したり、そのサイズを変更したりするのに、モデル自体を定義する頂点を変更するのは実用的ではありません。 そのような場合は、2-D と同じように、モデルに変換を適用します。  
  
 各モデル オブジェクトには、<xref:System.Windows.Media.Media3D.Model3D.Transform%2A>プロパティが、移動、向きを変更したり、モデルのサイズを変更します。 変換を適用するときは、ベクトルにより、または変換で指定する値により、モデルのすべてのポイントをオフセットします。 つまり、モデルが定義されている座標空間 ("モデル空間") を変換するのであって、シーン全体の座標系 ("ワールド空間") 内でモデルのジオメトリを構成する値を変更するのではありません。  
  
## <a name="translation-transformations"></a>平行移動変換  
 3-D 変換は、抽象基本クラスから継承<xref:System.Windows.Media.Media3D.Transform3D>; アフィン変換クラスが含まれます<xref:System.Windows.Media.Media3D.TranslateTransform3D>、 <xref:System.Windows.Media.Media3D.ScaleTransform3D>、および<xref:System.Windows.Media.Media3D.RotateTransform3D>します。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3-D システムも用意されています。、<xref:System.Windows.Media.Media3D.MatrixTransform3D>できるようにするクラスは、より簡潔な行列演算で同じ変換を指定します。  
  
 <xref:System.Windows.Media.Media3D.TranslateTransform3D> 指定したオフセット ベクトルの方向、model3d のすべてのポイントを移動、 <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A>、 <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetY%2A>、および<xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetZ%2A>プロパティ。 たとえば、立方体の 1 つの頂点が (2,2,2) にあるものとすると、オフセット ベクトル (0,1.6,1) により頂点 (2,2,2) は (2,3.6,3) に移動します。 モデル空間内での立方体の頂点はまだ (2,2,2) にありますが、モデル空間の (2,2,2) がワールド空間では (2,3.6,3) になるように、モデル空間とワールド空間の関係が変更されています。  
  
 ![平行移動の図](./media/transforms-translate.png "変換の変換")  
オフセットでの平行移動  
  
 次のコード例は、平行移動を適用する方法を示しています。  
  
 [!code-xaml[animation3dgallery_snip#Translation3DAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationexamplewholepage)]  
  
## <a name="scale-transformations"></a>スケール変換  
 <xref:System.Windows.Media.Media3D.ScaleTransform3D> 指定したスケール ベクター中心点で、モデルのスケールを変更します。 一様なスケールを指定すると、モデルは X、Y、Z 軸の方向に同じ比率だけ拡大縮小され、それに比例してモデルのサイズが変化します。 たとえば、設定する変換の<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>、 <xref:System.Windows.Media.ScaleTransform.ScaleY%2A>、および<xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A>プロパティを 0.5 に、モデルのサイズの半分は、次の 3 つすべての軸のスケールを 2 倍に同じプロパティを 2 に設定します。  
  
 ![ScaleTransform3D の統一された](./media/threecubes-uniformscale-1.png "threecubes_uniformscale_1")  
ScaleVector の例  
  
 一様ではないスケール変換 (X、Y、Z すべての値が同じではないスケール変換) を指定すると、3 つの方向をそれぞれ独立して拡大または縮小できます。 例では、<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>を 1 に<xref:System.Windows.Media.ScaleTransform.ScaleY%2A>2 と<xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A>を 1 には 2 倍に高さが、X、Z 軸に沿ったままにすると、モデルが発生します。  
  
 既定では、ScaleTransform3D では原点 (0,0,0) を基準にして頂点が拡大または縮小します。 ただし、変換するモデルが原点から描画されていない場合は、原点からモデルを拡大縮小すると、モデルのスケールは "その場" では変化しません。 代わりに、モデルの頂点がスケール ベクトルで乗算されて、スケール演算にはモデルの平行移動と拡大縮小の効果があります。  
  
 ![指定した中心点で 3 つのキューブがスケールされる](./media/threecubes-scaledwithcenter-1.png "threecubes_scaledwithcenter_1")  
スケールの中心点の例  
  
 「インプレース」のモデルを拡張するためには、ScaleTransform3D を設定して、モデルの中心を指定<xref:System.Windows.Media.ScaleTransform.CenterX%2A>、 <xref:System.Windows.Media.ScaleTransform.CenterY%2A>、および<xref:System.Windows.Media.Media3D.ScaleTransform3D.CenterZ%2A>プロパティ。 これにより、グラフィックス システムはモデル空間を拡大または縮小し、変換されますが、指定した中心<xref:System.Windows.Media.Media3D.Point3D>します。 逆に、原点を基準にモデルを構築し、異なる中心点を指定すると、モデルは原点から離れるように平行移動されます。  
  
## <a name="rotation-transformations"></a>回転変換  
 3-D のモデルは複数の方法で回転できます。 一般的な回転変換では、軸と、その軸の周りの回転角度を指定します。 <xref:System.Windows.Media.Media3D.RotateTransform3D>クラスを使用すると、定義、<xref:System.Windows.Media.Media3D.Rotation3D>でその<xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A>プロパティ。 指定します<xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A>と<xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A>プロパティをここでは、Rotation3D、 <xref:System.Windows.Media.Media3D.AxisAngleRotation3D>、変換を定義します。 次の例では、Y 軸を中心に 60 度だけモデルを回転します。  
  
 [!code-xaml[animation3dgallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
 注:[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]3-D は右手座標系の軸を中心に反時計回りに回転回転の角度の正の値が得られることを意味するです。  
  
 軸角度の回転は、値が指定されていない場合、回転は原点を想定しています、 <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterX%2A>、 <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterY%2A>、および<xref:System.Windows.Media.Media3D.RotateTransform3D.CenterZ%2A>RotateTransform3D のプロパティ。 拡大縮小と同様に、回転でもモデルの座標空間全体が変換されることを憶えておくと役に立ちます。 モデルが原点を中心として作成されていない場合、または前に平行移動されている場合は、その場での回転ではなく、原点を中心とする "ピボット" になる可能性があります。  
  
 ![新しい中心点による回転](./media/threecubes-rotationwithcenter-1.png "threecubes_rotationwithcenter_1")  
指定された新しい中心による回転  
  
 モデルを "その場で" 回転するには、モデルの実際の中心を回転の中心として指定します。 通常、ジオメトリは原点を中心にモデル化されるので、ほとんどの場合は、最初にモデルのサイズを変更し (スケーリング)、次に向きを設定し (回転)、最後に目的の位置に移動することにより (平行移動)、変換のセットで意図した結果が得られます。  
  
 ![X 60 度回転&#45;と y&#45;軸](./media/twocubes-rotation2axes-1.png "twocubes_rotation2axes_1")  
回転の例  
  
 軸角度の回転は、静的な変換と一部のアニメーションで問題なく行われます。 ただし、立方体モデルを X 軸を中心に 60 度回転してから、Z 軸を中心に 45 度回転する場合を考えてみてください。 この変換は、2 つの個別のアフィン変換として、または行列として記述できます。 しかし、この方法で定義された回転をスムーズにアニメーション化するのは難しい場合があります。 どちらの方法で計算してもモデルの最初と最後の位置は同じですが、モデルの中間の位置は計算上は不確定です。 四元数は、回転の開始と終了の間の補間を計算する別の方法を表します。  
  
 四元数では、3-D 空間内の軸と、その軸を中心とする回転が表されます。 たとえば、四元数では、(1,1,2) の軸と 50 度の回転といったように表されます。 回転の定義における四元数の威力は、合成と補間という 2 つの操作を実行できることです。 ジオメトリに適用される 2 つの四元数の合成とは、"ジオメトリを、axis2 を中心に rotation2 だけ回転した後、axis1 を中心に rotation1 だけ回転する" ことを意味します。 合成を使うと、ジオメトリに対する 2 つの回転を組み合わせて、結果を表す 1 つの四元数を得ることができます。 四元数の補間では、ある軸と向きから別の軸と向きへの滑らかで適切なパスを計算できるので、オリジナルから合成された四元数への補間を行うことで、ある状態から別の状態へのスムーズな移行を実現して、変換をアニメーション化できます。 アニメーション化するモデルでは、宛先を指定できる<xref:System.Windows.Media.Media3D.Quaternion>を使用して、回転、<xref:System.Windows.Media.Media3D.QuaternionRotation3D>の<xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A>プロパティ。  
  
## <a name="using-transformation-collections"></a>変換のコレクションの使用  
 シーンを作成する場合、通常はモデルに複数の変換を適用します。 追加する変換、<xref:System.Windows.Media.Media3D.Transform3DGroup.Children%2A>のコレクション、<xref:System.Windows.Media.Media3D.Transform3DGroup>をグループ化するクラスは、シーン内のさまざまなモデルに適用する便利なことに変換します。 各インスタンスに異なる変換セットを適用することでモデルを再利用できるように、多くの場合、複数の異なるグループで変換を再利用すると便利です。 変換をコレクションに追加する順序が重要であることに注意してください。コレクション内の変換は、最初から最後まで順番に適用されます。  
  
## <a name="animating-transformations"></a>変換のアニメーション化  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] の 3-D の実装は、2-D グラフィックスと同じタイミングおよびアニメーション システムに参加しています。 つまり、3-D シーンをアニメーション化するには、そのモデルのプロパティをアニメーション化します。 プリミティブのプロパティを直接アニメーション化することもできますが、通常は、モデルの位置や外観を変更する変換をアニメーション化する方が簡単です。 変換に適用できるため、<xref:System.Windows.Media.Media3D.Model3DGroup>オブジェクト個々 のモデル、およびアニメーションの 1 つのセットを Model3Dgroup の子と別のオブジェクトのグループにアニメーション セットを適用することができます。  [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] のタイミングおよびアニメーション システムの背景情報については、「[アニメーションの概要](animation-overview.md)」および「[ストーリーボードの概要](storyboards-overview.md)」トピックをご覧ください。  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] のオブジェクトをアニメーション化するには、タイムラインを作成し、アニメーションを定義して (時間経過と共に一部のプロパティの値を実際に変更します)、アニメーションを適用するプロパティを指定します。 このプロパティは、FrameworkElement のプロパティである必要があります。 3-D シーンのすべてのオブジェクトは Viewport3D の子なので、シーンに適用するアニメーションの対象となるプロパティは、Viewport3D のプロパティのプロパティです。 構文が冗長になる場合があるので、アニメーションのプロパティ パスを慎重に検討することが重要です。  
  
 オブジェクトをその場で回転させ、さらに揺れる動作を適用してオブジェクトの多くの部分が見えるようにしたいものとします。 そのためには、RotateTransform3D をモデルに適用し、回転軸をあるベクトルから別のベクトルにアニメーション化します。 次のコード例では、適用することを示します、 <xref:System.Windows.Media.Animation.Vector3DAnimation> 、変換の Rotation3D の Axis プロパティに、rotatetransform3d をモデルに適用されるいくつかの変換のいずれかを指定する、<xref:System.Windows.Media.TransformGroup>します。  
  
 [!code-csharp[3doverview#3DOverview3DN1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn1)]
 [!code-vb[3doverview#3DOverview3DN1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn1)]  
  
 [!code-csharp[3doverview#3DOverview3DN3](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn3)]
 [!code-vb[3doverview#3DOverview3DN3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn3)]  
  
 オブジェクトを移動または拡大縮小するには、他の変換プロパティを対象に同様の構文を使います。  たとえば、適用する場合があります、<xref:System.Windows.Media.Animation.Point3DAnimation>モデルの形状をスムーズにスケール変換の ScaleCenter プロパティにします。  
  
 上記の例のプロパティの変換が<xref:System.Windows.Media.Media3D.GeometryModel3D>シーン内の他のモデルのプロパティを変換することもできます。  Light オブジェクトに適用される変換をアニメーション化することで、モデルの外観を劇的に変えることができる、移動する照明効果とシャドウ効果を作成できます。  
  
 カメラもモデルなので、カメラのプロパティを変換することもできます。  カメラの位置または平面距離を変換することにより (実際には、シーン全体の投影を変換して) シーンの外観を変更できますが、この方法で得られる効果の多くは、シーン内のモデルの場所や位置に適用される変換ほど大きな "視覚的意味" を見ている人に与えられない場合があることに注意してください。  
  
## <a name="see-also"></a>関連項目

- [3-D グラフィックスの概要](3-d-graphics-overview.md)
- [変換の概要](transforms-overview.md)
- [2-D 変換のサンプル](https://go.microsoft.com/fwlink/?LinkID=158252)
