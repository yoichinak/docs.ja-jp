---
title: WPF の 3D パフォーマンスの最大化
ms.date: 03/30/2017
helpviewer_keywords:
- 3-D graphics [WPF]
ms.assetid: 4bcf949d-d92f-4d8d-8a9b-1e4c61b25bf6
ms.openlocfilehash: 8629748c37aae8e35bb928c5a8d5a9caa7046942
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59147525"
---
# <a name="maximize-wpf-3d-performance"></a>WPF の 3D パフォーマンスの最大化
使用すると、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]を 3D コントロールをビルドし、アプリケーションで 3D シーンを含めることがパフォーマンスの最適化を考慮すべき重要です。 このトピックでは、3 D クラスとそれらを使用するときにパフォーマンスを最適化するための推奨事項と共に、アプリケーションのパフォーマンスに影響を与えるプロパティの一覧を示します。  
  
 このトピックには、高度な理解が前提としています[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]3D 機能。 「描画層 2」に、このドキュメントでの推奨事項が適用-ほぼピクセル シェーダーのバージョン 2.0 と頂点シェーダーのバージョン 2.0 をサポートするハードウェアとして定義されています。 詳細については、次を参照してください。[グラフィックスの描画層](../advanced/graphics-rendering-tiers.md)します。  
  
## <a name="performance-impact-high"></a>パフォーマンスに影響します。High  
  
|プロパティ|推奨事項|  
|-|-|  
|<xref:System.Windows.Media.Brush>|ブラシの速度 (最高への最も遅い):<br /><br /> <xref:System.Windows.Media.SolidColorBrush><br /><br /> <xref:System.Windows.Media.LinearGradientBrush><br /><br /> <xref:System.Windows.Media.ImageBrush><br /><br /> <xref:System.Windows.Media.DrawingBrush> (キャッシュ済み)<br /><br /> <xref:System.Windows.Media.VisualBrush> (キャッシュ済み)<br /><br /> <xref:System.Windows.Media.RadialGradientBrush><br /><br /> <xref:System.Windows.Media.DrawingBrush> (キャッシュされていない)<br /><br /> <xref:System.Windows.Media.VisualBrush> (キャッシュされていない)|  
|<xref:System.Windows.UIElement.ClipToBoundsProperty>|設定`Viewport3D.ClipToBounds`を false にする必要はありませんたびに[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]のコンテンツを明示的にクリップを<xref:System.Windows.Controls.Viewport3D>Viewport3D の四角形にします。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] アンチ エイリアス処理されたクリッピングは非常に低速、および`ClipToBounds`は (遅い) 既定で有効に<xref:System.Windows.Controls.Viewport3D>します。|  
|<xref:System.Windows.UIElement.IsHitTestVisible%2A>|設定`Viewport3D.IsHitTestVisible`を必要としないときに false に[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]の内容を考慮する、<xref:System.Windows.Controls.Viewport3D>パフォーマンス マウス ヒット テストします。  ヒット テスト 3 D コンテンツは、ソフトウェアでは行われ、メッシュが多いと低速にすることができます。 <xref:System.Windows.UIElement.IsHitTestVisible%2A> 既定で有効に低速で<xref:System.Windows.Controls.Viewport3D>します。|  
|<xref:System.Windows.Media.Media3D.GeometryModel3D>|さまざまな資料または変換に必要な場合にのみ、さまざまなモデルを作成します。  それ以外の場合、coalesce 多くしよう<xref:System.Windows.Media.Media3D.GeometryModel3D>資料と変換が同じでインスタンスをいくつかの拡大に<xref:System.Windows.Media.Media3D.GeometryModel3D>と<xref:System.Windows.Media.Media3D.MeshGeometry3D>インスタンス。|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|メッシュのアニメーションなど、フレームごとにメッシュの個々 の頂点を変更する — において効率的とは限りません[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]。  各頂点が変更されたときに変更通知のパフォーマンスに与える影響を最小限に抑えるには、頂点ごとの変更を実行する前に、ビジュアル ツリーからメッシュをデタッチします。  メッシュが変更された後は、ビジュアル ツリーに接続し直します。  また、この方法でアニメーション化するメッシュのサイズを最小化してみてください。|  
|3D アンチエイリアシング|レンダリング速度を上げるでのマルチ サンプリングを無効にする<xref:System.Windows.Controls.Viewport3D>添付プロパティを設定して<xref:System.Windows.Media.RenderOptions.EdgeMode%2A>に`Aliased`します。  既定で 3D アンチエイリアシングが無効になって[!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)]で有効になっていると[!INCLUDE[TLA#tla_longhorn](../../../../includes/tlasharptla-longhorn-md.md)]1 ピクセルあたり 4 つのサンプルとします。|  
|テキスト|3D シーンでテキストをライブ (live されているため、<xref:System.Windows.Media.DrawingBrush>または<xref:System.Windows.Media.VisualBrush>) 遅くなることです。 代わりに、テキストのイメージを使用しようとしています (を使用して<xref:System.Windows.Media.Imaging.RenderTargetBitmap>)、テキストは変更しない限り、します。|  
|<xref:System.Windows.Media.TileBrush>|使用する場合、<xref:System.Windows.Media.VisualBrush>または<xref:System.Windows.Media.DrawingBrush>3D シーンでブラシのコンテンツが静的でないため、再試行してください、ブラシのキャッシュ (添付プロパティを設定<xref:System.Windows.Media.RenderOptions.CachingHint%2A>に`Cache`)。  スケールの最小値と最大の無効化のしきい値の設定 (添付プロパティを持つ<xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMinimum%2A>と<xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A>) できるように、キャッシュされたブラシは、必要なレベルの品質を維持しながら、あまり頻繁に再生成するされません。  既定では、<xref:System.Windows.Media.DrawingBrush>と<xref:System.Windows.Media.VisualBrush>はキャッシュされません、つまり、たびに再表示すると何かのブラシで塗りつぶされますがある、ブラシのコンテンツ全体する必要があります最初に再描画される中間の画面にします。|  
|<xref:System.Windows.Media.Effects.BitmapEffect>|<xref:System.Windows.Media.Effects.BitmapEffect> 影響を受けるすべてのハードウェア高速化なしで表示される内容を強制的にします。  最適なパフォーマンスを使用しないでください<xref:System.Windows.Media.Effects.BitmapEffect>します。|  
  
## <a name="performance-impact-medium"></a>パフォーマンスに影響します。Medium  
  
|プロパティ|推奨事項|  
|-|-|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|メッシュが共有の頂点を三角形として定義されているし、これらの頂点が同じ位置、標準、およびテクスチャの座標にある、共有される各頂点を 1 回だけ定義し、でのインデックスを使用して、三角形を定義<xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>します。|  
|<xref:System.Windows.Media.ImageBrush>|サイズを明示的に制御がある場合は、テクスチャのサイズを最小限に抑えてください (使用している場合、<xref:System.Windows.Media.Imaging.RenderTargetBitmap>や、 <xref:System.Windows.Media.ImageBrush>)。  下部のテクスチャの解像度が画質の低下、品質とパフォーマンスのバランスを探してみましょうできますに注意してください。|  
|Opacity|半透明の 3D の反射) などのコンテンツを描画、ときに、不透明度プロパティを使用して、ブラシまたはマテリアル (を使用して<xref:System.Windows.Media.Brush.Opacity%2A>または<xref:System.Windows.Media.Media3D.DiffuseMaterial.Color%2A>) 半透明別に作成するのではなく<xref:System.Windows.Controls.Viewport3D>を設定して`Viewport3D.Opacity`1 未満の値にします。|  
|<xref:System.Windows.Controls.Viewport3D>|数を最小限に抑える<xref:System.Windows.Controls.Viewport3D>シーンでを使用しているオブジェクトします。  モデルごとに個別の Viewport3D インスタンスを作成するのではなく、同じ Viewport3D で多くの 3D モデルを配置します。|  
|<xref:System.Windows.Freezable>|通常は再利用すると解消<xref:System.Windows.Media.Media3D.MeshGeometry3D>、<xref:System.Windows.Media.Media3D.GeometryModel3D>ブラシ、および資料。  派生しているために、すべてのどれ`Freezable`します。|  
|<xref:System.Windows.Freezable>|呼び出す、<xref:System.Windows.Freezable.Freeze%2A>アプリケーションでそのプロパティが残っているとフリーズ可能オブジェクトのメソッドは変更されません。  固定は、ワーキング セットの低下し、速度を上げることができます。|  
|<xref:System.Windows.Media.Brush>|使用<xref:System.Windows.Media.ImageBrush>の代わりに<xref:System.Windows.Media.VisualBrush>または<xref:System.Windows.Media.DrawingBrush>ときに、ブラシの内容は変更されません。  2D のコンテンツに変換できる、<xref:System.Windows.Controls.Image>を介して<xref:System.Windows.Media.Imaging.RenderTargetBitmap>しで使用、<xref:System.Windows.Media.ImageBrush>します。|  
|<xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A>|使用しない<xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A>実際の背面を確認する必要があるなければ、<xref:System.Windows.Media.Media3D.GeometryModel3D>します。|  
|<xref:System.Windows.Media.Media3D.Light>|ライトの速度 (最高への最も遅い):<br /><br /> <xref:System.Windows.Media.Media3D.AmbientLight><br /><br /> <xref:System.Windows.Media.Media3D.DirectionalLight><br /><br /> <xref:System.Windows.Media.Media3D.PointLight><br /><br /> <xref:System.Windows.Media.Media3D.SpotLight>|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|これらの制限の下のメッシュのサイズを維持しようとしてください。<br /><br /> <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>:20, 001<xref:System.Windows.Media.Media3D.Point3D>インスタンス<br /><br /> <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>:60,003<xref:System.Int32>インスタンス|  
|<xref:System.Windows.Media.Media3D.Material>|素材の速度 (最高への最も遅い):<br /><br /> <xref:System.Windows.Media.Media3D.EmissiveMaterial><br /><br /> <xref:System.Windows.Media.Media3D.DiffuseMaterial><br /><br /> <xref:System.Windows.Media.Media3D.SpecularMaterial>|  
|<xref:System.Windows.Media.Brush>|[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 一貫した方法で 3D を非表示ブラシ (黒のアンビエント ブラシ、クリア ブラシなど) オプトアウトしません。  シーンからこれらを省略することを検討してください。|  
|<xref:System.Windows.Media.Media3D.MaterialGroup>|各<xref:System.Windows.Media.Media3D.Material>で、<xref:System.Windows.Media.Media3D.MaterialGroup>のため多くの資料を含む別のレンダリング パスと、単純な資料があっても、ご使用の GPU の塗りつぶしの要求を大幅に向上させることができます。  内の素材の数を最小限に抑える、<xref:System.Windows.Media.Media3D.MaterialGroup>します。|  
  
## <a name="performance-impact-low"></a>パフォーマンスに影響します。Low  
  
|プロパティ|推奨事項|  
|-|-|  
|<xref:System.Windows.Media.Media3D.Transform3DGroup>|アニメーションが不要またはデータ変換を複数の変換を含むグループを使用する代わりに、バインディングを使用して、1 つと<xref:System.Windows.Media.Media3D.MatrixTransform3D>がそれ以外の場合独立して存在変換グループ内のすべての変換の製品であることには、設定します。|  
|<xref:System.Windows.Media.Media3D.Light>|ライト、シーン内の数を最小限に抑えます。 強制的にシーンが多すぎるの電気[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]ソフトウェア レンダリングにフォールバックします。  制限は、約 110<xref:System.Windows.Media.Media3D.DirectionalLight>オブジェクト、70<xref:System.Windows.Media.Media3D.PointLight>オブジェクト、または 40<xref:System.Windows.Media.Media3D.SpotLight>オブジェクト。|  
|<xref:System.Windows.Media.Media3D.ModelVisual3D>|静的オブジェクトから個別に置くことによってオブジェクトの移動を区切る<xref:System.Windows.Media.Media3D.ModelVisual3D>インスタンス。  ModelVisual3D はより「重い」<xref:System.Windows.Media.Media3D.GeometryModel3D>変換された境界がキャッシュされるためです。  GeometryModel3D には、モデルに最適化されました。ModelVisual3D は、シーン ノードに最適化されます。  GeometryModel3D の共有インスタンスをシーンに配置するのにには、ModelVisual3D を使用します。|  
|<xref:System.Windows.Media.Media3D.Light>|シーン内のライトの数を変更する回数を最小限に抑えます。  ライトの数のそれぞれの変更では、その構成が以前存在していた (とそのシェーダーがキャッシュしたため) 場合を除き、再生成され、再コンパイルを強制します。|  
|淡色|黒のライトには、表示されませんが、時間を表示するために追加されます。省略することを検討してください。|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|大規模なコレクションの構築時を最小限に抑える[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]、MeshGeometry3D のなど<xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>、 <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A>、 <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A>、および<xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>値の母集団の前に、コレクションのサイズを事前。 可能であれば、配列やリストなど、コレクションのコンス トラクター事前設定されたデータの構造体を渡します。|  
  
## <a name="see-also"></a>関連項目

- [3-D グラフィックスの概要](3-d-graphics-overview.md)
