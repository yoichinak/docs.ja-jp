---
title: 3D グラフィックスの概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3D graphics [WPF]
- graphics [WPF], 3D
ms.assetid: 67f31ed4-e36b-4b02-9889-dcce245d7afc
ms.openlocfilehash: e4918f7737bbe57a4f29c6c5cff1099f4f21674b
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291818"
---
# <a name="3d-graphics-overview"></a>3D グラフィックスの概要
<a name="introduction"></a>3D 機能では[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]、マークアップと手続き型の両方のコードで 3D グラフィックスを描画、変換、アニメーション化できます。 開発者は、2D グラフィックスと 3D グラフィックスを組み合わせて、リッチ コントロールを作成したり、複雑なデータの図を提供したり、アプリケーションのインターフェイスのユーザー エクスペリエンスを向上させることができます。 3D サポート[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は、フル機能のゲーム開発プラットフォームを提供するようには設計されていません。 このトピックでは、グラフィックス システムの 3D[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]機能の概要について説明します。  

<a name="threed_in_2d"></a>
## <a name="3d-in-a-2d-container"></a>2D コンテナ内の 3D  
 3D[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]グラフィックス コンテンツは要素 にカプセル化<xref:System.Windows.Controls.Viewport3D>され、2 次元要素構造に含めることができます。 グラフィックス システムは<xref:System.Windows.Controls.Viewport3D>、 の他の多くの要素と同様に[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、2 次元のビジュアル要素として扱われます。 <xref:System.Windows.Controls.Viewport3D>は、ビューポートのウィンドウとして 3 次元シーンに変換されます。 より正確には、3D シーンが投影されるサーフェスです。  
  
 従来の 2D アプリケーションでは<xref:System.Windows.Controls.Viewport3D>、Grid や Canvas などの別のコンテナ要素と同じように使用します。  同じシーン<xref:System.Windows.Controls.Viewport3D>グラフ内の他の 2D 図面オブジェクトと一緒に使用できますが、2D オブジェクトと<xref:System.Windows.Controls.Viewport3D>3D オブジェクトを内に入れることはできません。  このトピックでは、 内に 3D グラフィックスを<xref:System.Windows.Controls.Viewport3D>描画する方法について説明します。  
  
<a name="coord_space"></a>
## <a name="3d-coordinate-space"></a>3D 座標空間  
 2D グラフィックスの座標系は[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、レンダリング領域 (通常は画面) の左上に原点を配置します。 2D システムでは、正の x 軸の値が右に進み、正の y 軸の値が下降します。  ただし、3D 座標系では、原点はレンダリング領域の中心にあり、正の x 軸の値は右に進み、正の y 軸値は上向きに進み、正の Z 軸の値は原点から外側に進みます。視聴者に向かって。  
  
 ![座標系](./media/coordsystem-1.png "コドシステム-1")  
従来の 2D および 3D 座標系の表現  
  
 これらの軸で定義されるスペースは、 の 3D オブジェクトの定常[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]参照フレームです。 この空間内にモデルを構築し、それらを表示するためのライトとカメラを作成するときは、この静止した基準枠 ("ワールド空間") と、モデルに変換を適用するときにモデルごとに作成するローカルな基準枠を区別することをお勧めします。 また、ワールド空間内のオブジェクトは、ライトとカメラの設定により、まったく違って見えたり、またはまったく見えなくなることがありますが、カメラの位置によってワールド空間内のオブジェクトの場所が変化することはないことに注意してください。  
  
<a name="cameras"></a>
## <a name="cameras-and-projections"></a>カメラと投影  
 2D で作業する開発者は、2 次元の画面に描画プリミティブを配置することに慣れています。 3D シーンを作成する場合は、実際には 3D オブジェクトの 2D 表現を作成することに注意してください。 3D シーンは見物人の視点によって異なって見えるので、その視点を指定する必要があります。 <xref:System.Windows.Media.Media3D.Camera>クラスを使用すると、3D シーンのこの視点を指定できます。  
  
 2D サーフェス上での 3D シーンの表現方法を理解するもう 1 つの方法は、シーンをビューサーフェス上の投影として記述することです。 <xref:System.Windows.Media.Media3D.ProjectionCamera>では、さまざまな投影法とそのプロパティを指定して、見物人が 3D モデルを表示する方法を変更できます。 A<xref:System.Windows.Media.Media3D.PerspectiveCamera>は、シーンを短縮する投影を指定します。  言い換えれば、<xref:System.Windows.Media.Media3D.PerspectiveCamera>消失点の視点を提供します。  シーンの座標空間内でのカメラの位置、カメラの方向と視野、およびシーン内での "上" の方向を定義するベクトルを指定できます。 次の図は、's の投影法を<xref:System.Windows.Media.Media3D.PerspectiveCamera>示しています。  
  
 カメラ<xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A>の<xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A><xref:System.Windows.Media.Media3D.ProjectionCamera>投影範囲を制限するプロパティとプロパティ。 カメラはシーン内の任意の場所に配置できるため、カメラをモデルの内部またはモデルの非常に近くに実際に配置することができ、オブジェクトを正しく識別するのが困難になる場合があります。  <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A>では、オブジェクトを描画しない範囲のカメラからの最小距離を指定できます。  逆に、<xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A>オブジェクトを描画しないカメラからの距離を指定して、オブジェクトが認識できないほど遠く離れているオブジェクトがシーンに含まれないようにすることができます。  
  
 ![カメラの設定](./media/coordsystem-6.png "コドシステム-6")  
カメラの位置  
  
 <xref:System.Windows.Media.Media3D.OrthographicCamera>2D ビジュアル サーフェスに対する 3D モデルの直交投影を指定します。 他のカメラと同じように、位置、視線方向、および "上" の向きを指定します。 ただし<xref:System.Windows.Media.Media3D.PerspectiveCamera>、とは<xref:System.Windows.Media.Media3D.OrthographicCamera>異なり、遠近法の短縮を含まない投影法を記述します。 つまり、<xref:System.Windows.Media.Media3D.OrthographicCamera>カメラのポイントで辺が交わりするビューボックスではなく、平行なビューボックスを表します。 次の図は、 と を使用<xref:System.Windows.Media.Media3D.PerspectiveCamera>して<xref:System.Windows.Media.Media3D.OrthographicCamera>表示したモデルと同じモデルを示しています。  
  
 ![正投影と透視投影](./media/camera-projections4.png "Camera_projections4")  
透視投影と正投影  
  
 次のコードでは、カメラの一般的な設定を示します。  
  
 [!code-csharp[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexampleinline1)]
 [!code-vb[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexampleinline1)]  
  
<a name="models_meshes"></a>
## <a name="model-and-mesh-primitives"></a>モデルとメッシュ プリミティブ  
  
 <xref:System.Windows.Media.Media3D.Model3D>は、汎用的な 3D オブジェクトを表す抽象基本クラスです。 3D シーンを作成するには、表示するオブジェクトが必要で、シーン グラフを構成するオブジェクトが から<xref:System.Windows.Media.Media3D.Model3D>派生します。 現在、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]では、 を使用<xref:System.Windows.Media.Media3D.GeometryModel3D>してジオメトリをモデリングできます。 この<xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A>モデルのプロパティは、メッシュ プリミティブを取得します。  
  
 モデルを構築するには、最初にプリミティブ (メッシュ) を作成します。 3D プリミティブは、単一の 3D エンティティを形成する頂点の集合です。 ほとんどの 3D システムは、最も単純な閉じた図形(3 つの頂点で定義された三角形)をモデル化したプリミティブを提供します。  三角形の 3 つの頂点は同一平面上にあるため、三角形の追加を続けて、メッシュと呼ばれる複雑な図形をモデル化できます。  
  
 3D システムは[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]現在クラス<xref:System.Windows.Media.Media3D.MeshGeometry3D>を提供しており、これにより任意のジオメトリを指定できます。現在、球体や立方体のような定義済みの 3D プリミティブはサポートされていません。 プロパティとして三<xref:System.Windows.Media.Media3D.MeshGeometry3D>角形の頂点のリストを指定して作成を<xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>開始します。 各頂点は<xref:System.Windows.Media.Media3D.Point3D>.  (では[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]、このプロパティを、各頂点の座標を表す 3 つの数値にグループ化された数値のリストとして指定します。ジオメトリによっては、メッシュは多くの三角形で構成され、一部は同じコーナー(頂点)を共有します。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] でメッシュを正しく描画するには、どの頂点がどの三角形によって共有されているのかということに関する情報が必要です。 この情報を提供するには、<xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>プロパティに三角形のインデックスのリストを指定します。 このリストは、リストで指定された点が三角形<xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>を決定する順序を指定します。  
  
 [!code-xaml[basic3d#Basic3DXAML3DN3](~/samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn3)]  
  
 前の例では、このリスト<xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>は、立方体型のメッシュを定義する 8 つの頂点を指定しています。 この<xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>プロパティは、3 つのインデックスから構成される 12 のグループのリストを指定します。  リスト内の各番号は、リスト内のオフセット<xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>を参照します。  たとえば、リストで指定された最初の<xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>3 つの頂点は(1、1、0、0、0、0)、(0,0,0)です。 リストで指定された最初の<xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>3 つのインデックスは、<xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>リストの最初、3 番目、2 番目のポイントに対応する 0、2、1 です。 つまり、この立方体モデルを構成する最初の三角形は、(1,1,0)、(0,1,0)、(0,0,0) から作成されます。残りの 11 個の三角形も同じようにして決定されます。  
  
 プロパティ<xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A>の値を指定することで、<xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A>モデルの定義を続行できます。  グラフィックス システムがモデルのサーフェイスをレンダリングするには、特定の三角形において面が向いている方向に関する情報が必要です。 この情報を使って、モデルの照明の計算が行われます。光源に正対しているサーフェイスは、光源に対して角度のあるサーフェスより明るくなります。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は位置座標を使って既定の法線ベクトルを決定できますが、曲面の外観を近似する別の法線ベクトルを指定することもできます。  
  
 この<xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A>プロパティは、テクスチャが<xref:System.Windows.Point>メッシュの頂点にどのように描画されるのかを決定する座標をマップする方法をグラフィックス システムに指示する s のコレクションを指定します。 <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A>は 0 から 1 までの範囲の値で指定します。  プロパティと同様<xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A>に、グラフィックス システムは既定のテクスチャ座標を計算できますが、繰り返しパターンの一部を含むテクスチャのマッピングを制御するために、異なるテクスチャ座標を設定することもできます。 テクスチャ座標について詳しくは、マネージド Direct3D SDK の後続のトピックをご覧ください。  
  
 次の例では、手続き型コードで立方体モデルの 1 つの面を作成する方法を示します。 キューブ全体を単一のジオメトリモデル3Dとして描画できます。この例では、後で各面に個別のテクスチャを適用するために、キューブの面を別個のモデルとして描画します。  
  
 [!code-csharp[3doverview#3DOverview3DN6](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn6)]
 [!code-vb[3doverview#3DOverview3DN6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn6)]  
  
 [!code-csharp[3doverview#3DOverview3DN7](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn7)]
 [!code-vb[3doverview#3DOverview3DN7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn7)]  
  
<a name="materials"></a>'
## <a name="applying-materials-to-the-model"></a>モデルへのマテリアルの適用  
  
 メッシュが 3 次元のオブジェクトのように見えるには、頂点と三角形によって定義されたサーフェイスをカバーするようにテクスチャを適用し、カメラで照明および投影できるようにする必要があります。 2D では、このクラス<xref:System.Windows.Media.Brush>を使用して、画面の領域に色、パターン、グラデーション、またはその他の視覚的なコンテンツを適用します。  ただし、3D オブジェクトの外観は、適用されるカラーやパターンだけでなく、照明モデルの機能です。 現実世界のオブジェクトは、サーフェイスの質によって光の反射が異なります。光沢のあるサーフェイスの見た目は荒くて艶のないサーフェイスとは異なり、光を吸収するオブジェクトや反射するオブジェクトがあります。 同じブラシをすべて 2D オブジェクトに適用できる 3D オブジェクトに適用できますが、直接適用することはできません。  
  
 モデルのサーフェスの特性を定義するには、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]抽象クラスを使用<xref:System.Windows.Media.Media3D.Material>します。 Material の具象サブクラスでは、モデルのサーフェイスの一部の外観特性が決まり、SolidColorBrush、TileBrush、または VisualBrush を渡すことができる Brush プロパティも提供されます。  
  
- <xref:System.Windows.Media.Media3D.DiffuseMaterial>モデルが拡散して点灯したように、ブラシがモデルに適用されることを指定します。 拡散を使用する材料は、2Dモデル上で直接ブラシを使用することに最も似ています。モデルサーフェスは、光沢のように光を反射しません。  
  
- <xref:System.Windows.Media.Media3D.SpecularMaterial>モデルのサーフェスが硬いか光沢があり、ハイライトを反射できるかのように、ブラシをモデルに適用することを指定します。 <xref:System.Windows.Media.Media3D.SpecularMaterial.SpecularPower%2A>プロパティの値を指定することで、テクスチャがこの反射品質を示す度合いを設定できます。  
  
- <xref:System.Windows.Media.Media3D.EmissiveMaterial>では、モデルがブラシの色と等しい光を放出しているかのようにテクスチャを適用するように指定できます。 これによってモデルが明るくなることはありませんが、DiffuseMaterial または SpecularMaterial のテクスチャとは異なるシャドウになります。  
  
 パフォーマンスを向上させるには、<xref:System.Windows.Media.Media3D.GeometryModel3D>シーンから(カメラのモデルの反対側にあるため、見えなくなっている面)の背面がシーンからカリングされます。  平面のようなモデル<xref:System.Windows.Media.Media3D.Material>の裏面に適用する を指定するには、モデルの<xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A>プロパティを設定します。  
  
 光彩効果や反射効果など、ある種のサーフェイス品質を実現するには、複数の異なるブラシを連続してモデルに適用することが必要な場合があります。 クラスを使用して、複数のマテリアルを<xref:System.Windows.Media.Media3D.MaterialGroup>適用および再利用できます。 MaterialGroup の子は、複数のレンダリング パスの最初から最後まで適用されます。  
  
 次のコード例は、3D モデルにブラシとしてソリッド カラーと描画を適用する方法を示しています。  
  
 [!code-xaml[basic3d#Basic3DXAML3DN5](~/samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn5)]  
  ' [!code-xaml[3doverview#3DOverview3DN9](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/app.xaml#3doverview3dn9)]  
 ' [!code-csharp[3doverview#3DOverview3DN8](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn8)]
  [!code-vb[3doverview#3DOverview3DN8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn8)]  
  
<a name="lights"></a>
## <a name="illuminating-the-scene"></a>シーンの照明  
 3D グラフィックスのライトは、現実世界でのライトの実行を行います: サーフェスが表示されます。 さらに重要なことは、ライトによって投影に含まれるシーンの部分が決まります。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の Light オブジェクトは、さまざまなライト効果とシャドウ効果を作成し、現実世界のさまざまな照明の動作に従ってモデル化されます。 シーンに少なくとも 1 つのライトを含めるか、モデルが表示されません。  
  
 次のライトは、基本クラスから<xref:System.Windows.Media.Media3D.Light>派生します。  
  
- <xref:System.Windows.Media.Media3D.AmbientLight>: 位置や方向に関係なく、すべてのオブジェクトを均一に照らすアンビエント 照明を提供します。  
  
- <xref:System.Windows.Media.Media3D.DirectionalLight>: 遠くの光源のように照らされます。  指向性光源は<xref:System.Windows.Media.Media3D.DirectionalLight.Direction%2A>Vector3D として指定されていますが、指定された位置はありません。  
  
- <xref:System.Windows.Media.Media3D.PointLight>: 近くの光源のように照らされます。 PointLight には位置があり、その位置から光を投射します。 シーン内のオブジェクトは、その位置および光源からの距離に応じて照らされます。 <xref:System.Windows.Media.Media3D.PointLightBase><xref:System.Windows.Media.Media3D.PointLightBase.Range%2A>は、モデルがライトによって照らされない距離を決定するプロパティを公開します。 PointLight は減衰プロパティも公開し、距離の間に光の強度がどのように減少するかを決定します。 光の減衰には、一定、線形、または 2 次補間を指定できます。  
  
- <xref:System.Windows.Media.Media3D.SpotLight>: から<xref:System.Windows.Media.Media3D.PointLight>継承します。 SpotLight は PointLight と同じように照らし、位置と方向の両方を持ちます。 これらのプロパティは、角度で指定された<xref:System.Windows.Media.Media3D.SpotLight.InnerConeAngle%2A>、設定されたコーン形状<xref:System.Windows.Media.Media3D.SpotLight.OuterConeAngle%2A>の領域とプロパティにライトを投影します。  
  
 ライトは<xref:System.Windows.Media.Media3D.Model3D>オブジェクトであるため、位置、色、方向、範囲などのライト プロパティを変換してアニメートできます。  
  
 [!code-xaml[hittest3d#HitTest3D3DN6](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml#hittest3d3dn6)]  
  
 [!code-csharp[basic3d#Basic3D3DN11](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn11)]
 [!code-vb[basic3d#Basic3D3DN11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn11)]  
  
 [!code-csharp[basic3d#Basic3D3DN12](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn12)]
 [!code-vb[basic3d#Basic3D3DN12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn12)]  
  
 [!code-csharp[basic3d#Basic3D3DN13](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn13)]
 [!code-vb[basic3d#Basic3D3DN13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn13)]  
  
<a name="transforms"></a>
## <a name="transforming-models"></a>モデルの変換  
 モデルを作成するとき、モデルにはシーン内で特定の位置があります。 モデルをシーン内で移動したり、回転したり、そのサイズを変更したりするのに、モデル自体を定義する頂点を変更するのは実用的ではありません。  代わりに、2D と同様に、モデルに変換を適用します。  
  
 各モデル オブジェクトには<xref:System.Windows.Media.Media3D.Model3D.Transform%2A>、モデルの移動、方向変更、サイズ変更を行うことができるプロパティがあります。  変換を適用するときは、ベクトルにより、または変換で指定する値により、モデルのすべてのポイントをオフセットします。 つまり、モデルが定義されている座標空間 ("モデル空間") を変換するのであって、シーン全体の座標系 ("ワールド空間") 内でモデルのジオメトリを構成する値を変更するのではありません。  
  
 モデルの変換の詳細については[、「3D 変換の概要」を](3-d-transformations-overview.md)参照してください。  
  
<a name="animations"></a>
## <a name="animating-models"></a>モデルのアニメーション化  
 3D 実装は[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、2D グラフィックスと同じタイミングおよびアニメーション システムに参加します。 つまり、3D シーンをアニメートするには、モデルのプロパティをアニメートします。 プリミティブのプロパティを直接アニメーション化することもできますが、通常は、モデルの位置や外観を変更する変換をアニメーション化する方が簡単です。 変換はオブジェクトだけでなく個々のモデル<xref:System.Windows.Media.Media3D.Model3DGroup>にも適用できるため、Model3DGroup の子に 1 つのアニメーションセットを適用し、別のアニメーションセットを子オブジェクトのグループに適用することができます。 また、シーンの照明のプロパティをアニメーション化することにより、さまざまな視覚効果を実現できます。 最後に、カメラの位置または視野をアニメーション化することで、投影自体をアニメーション化することもできます。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のタイミングおよびアニメーション システムの背景情報については、「[アニメーションの概要](animation-overview.md)」、「[ストーリーボードの概要](storyboards-overview.md)」、および「[Freezable オブジェクトの概要](../advanced/freezable-objects-overview.md)」の各トピックをご覧ください。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のオブジェクトをアニメーション化するには、タイムラインを作成し、アニメーションを定義して (時間経過と共に一部のプロパティの値を実際に変更します)、アニメーションを適用するプロパティを指定します。 3D シーン内のすべてのオブジェクトは<xref:System.Windows.Controls.Viewport3D>の子であるため、シーンに適用するアニメーションの対象となるプロパティは Viewport3D のプロパティです。  
  
 その場で揺れるように見えるモデルを作成したいものとします。 モデルに を適用<xref:System.Windows.Media.Media3D.RotateTransform3D>し、あるベクトルから別のベクトルへの回転軸をアニメートすることもできます。 次のコード例では、RotateTransform3D が TransformGroup でモデルに適用される複数の変換の 1 つであるものとして、変換の Rotation3D の Axis プロパティに Vector3DAnimation を適用する方法を示します。  
  
 [!code-csharp[3doverview#3DOverview3DN1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn1)]
 [!code-vb[3doverview#3DOverview3DN1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn1)]  
  
 [!code-csharp[3doverview#3DOverview3DN3](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn3)]
 [!code-vb[3doverview#3DOverview3DN3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn3)]  
  
 [!code-csharp[3doverview#3DOverview3DN4](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn4)]
 [!code-vb[3doverview#3DOverview3DN4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn4)]  
  
 [!code-csharp[3doverview#3DOverview3DN5](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn5)]
 [!code-vb[3doverview#3DOverview3DN5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn5)]  
  
<a name="animations1"></a>
## <a name="add-3d-content-to-the-window"></a>ウィンドウに 3D コンテンツを追加する  
 シーンをレンダリングするには、モデルとライトを<xref:System.Windows.Media.Media3D.Model3DGroup>に追加してから、<xref:System.Windows.Media.Media3D.Model3DGroup>の<xref:System.Windows.Media.Media3D.ModelVisual3D.Content%2A>を<xref:System.Windows.Media.Media3D.ModelVisual3D>に設定します。 の<xref:System.Windows.Media.Media3D.ModelVisual3D>コレクションに<xref:System.Windows.Controls.Viewport3D.Children%2A>を追加します<xref:System.Windows.Controls.Viewport3D>。 カメラのプロパティを<xref:System.Windows.Controls.Viewport3D>設定して、<xref:System.Windows.Controls.Viewport3D.Camera%2A>カメラをに追加します。  
  
 最後に、<xref:System.Windows.Controls.Viewport3D>をウィンドウに追加します。 が<xref:System.Windows.Controls.Viewport3D>Canvas などのレイアウト要素のコンテンツとして含まれる場合は、Viewport3D のサイズを<xref:System.Windows.FrameworkElement.Height%2A><xref:System.Windows.FrameworkElement.Width%2A>指定します。 <xref:System.Windows.FrameworkElement>  
  
 [!code-xaml[hostingwpfusercontrolinwf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.Viewport3D>
- <xref:System.Windows.Media.Media3D.PerspectiveCamera>
- <xref:System.Windows.Media.Media3D.DirectionalLight>
- <xref:System.Windows.Media.Media3D.Material>
- [3D 変換の概要](3-d-transformations-overview.md)
- [WPF の 3D パフォーマンスの最大化](maximize-wpf-3d-performance.md)
- [方法のトピック](3-d-graphics-how-to-topics.md)
- [WPF での図形と基本描画の概要](shapes-and-basic-drawing-in-wpf-overview.md)
- [イメージ、描画、およびビジュアルによる塗りつぶし](painting-with-images-drawings-and-visuals.md)
