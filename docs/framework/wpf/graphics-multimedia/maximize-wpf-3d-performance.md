---
title: WPF の 3D パフォーマンスの最大化
ms.date: 03/30/2017
helpviewer_keywords:
- 3-D graphics [WPF]
ms.assetid: 4bcf949d-d92f-4d8d-8a9b-1e4c61b25bf6
ms.openlocfilehash: e1a90406423e36dd10b8b108e076fe73f99947f0
ms.sourcegitcommit: 77e33b682db39955e331b8e8eda4ef1925a24e78
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70133847"
---
# <a name="maximize-wpf-3d-performance"></a>WPF の 3D パフォーマンスの最大化
を使用[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]して3d コントロールを構築し、アプリケーションに3d シーンを含めると、パフォーマンスの最適化を考慮することが重要になります。 このトピックでは、アプリケーションのパフォーマンスに影響を与える3D クラスとプロパティの一覧と、それらを使用するときのパフォーマンスを最適化するための推奨事項について説明します。  
  
 このトピックでは、3d 機能[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]の高度な知識を前提としています。 このドキュメントの提案は、"レンダリング層 2" に適用されます。これは、ピクセルシェーダーバージョン2.0 と頂点シェーダーバージョン2.0 をサポートするハードウェアとしてほぼ定義されています。 詳細については、「[グラフィックスの描画層](../advanced/graphics-rendering-tiers.md)」を参照してください。  
  
## <a name="performance-impact-high"></a>パフォーマンスへの影響:High  
  
|プロパティ|推奨事項|  
|-|-|  
|<xref:System.Windows.Media.Brush>|ブラシの速度 (最速から低速):<br /><br /> <xref:System.Windows.Media.SolidColorBrush><br /><br /> <xref:System.Windows.Media.LinearGradientBrush><br /><br /> <xref:System.Windows.Media.ImageBrush><br /><br /> <xref:System.Windows.Media.DrawingBrush>た<br /><br /> <xref:System.Windows.Media.VisualBrush>た<br /><br /> <xref:System.Windows.Media.RadialGradientBrush><br /><br /> <xref:System.Windows.Media.DrawingBrush>キャッシュされ<br /><br /> <xref:System.Windows.Media.VisualBrush>キャッシュされ|  
|<xref:System.Windows.UIElement.ClipToBoundsProperty>|の`Viewport3D.ClipToBounds`内容を Viewport3D's 四角形に[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]明示的にクリップする必要がない場合は<xref:System.Windows.Controls.Viewport3D> 、常に false に設定します。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]アンチエイリアス化されたクリッピングは`ClipToBounds`非常に遅くなり、で<xref:System.Windows.Controls.Viewport3D>は既定で有効 (低速) になります。|  
|<xref:System.Windows.UIElement.IsHitTestVisible%2A>|マウス`Viewport3D.IsHitTestVisible`ヒットテストを実行するときに[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]のコンテンツを考慮する必要<xref:System.Windows.Controls.Viewport3D>がない場合は、常に false に設定します。  ヒットテスト3D コンテンツはソフトウェアで実行され、大きなメッシュでは速度が低下する可能性があります。 <xref:System.Windows.UIElement.IsHitTestVisible%2A>は、で<xref:System.Windows.Controls.Viewport3D>は既定で有効 (低速) です。|  
|<xref:System.Windows.Media.Media3D.GeometryModel3D>|異なるモデルを作成するのは、異なる素材または変換が必要な場合のみにしてください。  それ以外の場合は、 <xref:System.Windows.Media.Media3D.GeometryModel3D>同じ素材を使用して多数のインスタンスを結合<xref:System.Windows.Media.Media3D.GeometryModel3D>し<xref:System.Windows.Media.Media3D.MeshGeometry3D> 、より大きなインスタンスとインスタンスに変換します。|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|メッシュアニメーション—フレームごとにメッシュの個々の頂点を変更することは、では常に効率的[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]であるとは限りません。  各頂点が変更されたときの変更通知のパフォーマンスへの影響を最小限に抑えるには、頂点ごとの変更を実行する前に、ビジュアルツリーからメッシュをデタッチします。  メッシュが変更されたら、ビジュアルツリーに再アタッチします。  また、この方法でアニメーション化されるメッシュのサイズを最小化してみてください。|  
|3D アンチエイリアシング|レンダリング速度を上げるには、添付プロパティ<xref:System.Windows.Controls.Viewport3D> <xref:System.Windows.Media.RenderOptions.EdgeMode%2A>をに`Aliased`設定して、のマルチサンプリングを無効にします。  既定では、3D アンチエイリアシングは、1ピクセルあたり4サンプルの Windows で有効になっています。|  
|テキスト|3d シーン内のライブテキスト ( <xref:System.Windows.Media.DrawingBrush>または<xref:System.Windows.Media.VisualBrush>にあるためライブテキスト) が低速になることがあります。 テキストが変更されない限り、テキストの<xref:System.Windows.Media.Imaging.RenderTargetBitmap>イメージを (経由で) 使用してください。|  
|<xref:System.Windows.Media.TileBrush>|ブラシのコンテンツが静的<xref:System.Windows.Media.VisualBrush>でない<xref:System.Windows.Media.DrawingBrush>ために3d シーンでまたはを使用する必要がある場合は、ブラシのキャッシュを試して<xref:System.Windows.Media.RenderOptions.CachingHint%2A>み`Cache`てください (添付プロパティをに設定します)。  必要な品質レベルを維持したまま、キャッシュされ<xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMinimum%2A>た<xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A>ブラシが頻繁に再生成されないように、(添付プロパティとを使用して) スケール無効化の最小しきい値と最大値を設定します。  既定<xref:System.Windows.Media.DrawingBrush>では、 <xref:System.Windows.Media.VisualBrush>とはキャッシュされません。つまり、ブラシで塗りつぶされたものを再描画する必要があるたびに、ブラシのコンテンツ全体を中間サーフェイスに再描画する必要があります。|  
|<xref:System.Windows.Media.Effects.BitmapEffect>|<xref:System.Windows.Media.Effects.BitmapEffect>影響を受けるすべてのコンテンツを強制的にハードウェアアクセラレータなしで表示します。  最適なパフォーマンスを得るには<xref:System.Windows.Media.Effects.BitmapEffect>、を使用しないでください。|  
  
## <a name="performance-impact-medium"></a>パフォーマンスへの影響:Medium  
  
|プロパティ|推奨事項|  
|-|-|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|メッシュが共有頂点を持つ隣接する三角形として定義され、それらの頂点の位置、法線、およびテクスチャの座標が同じである場合は、各共有頂点を<xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>1 回だけ定義し、でインデックスを使用して三角形を定義します。|  
|<xref:System.Windows.Media.ImageBrush>|サイズを明示的に制御している場合 ( <xref:System.Windows.Media.Imaging.RenderTargetBitmap> <xref:System.Windows.Media.ImageBrush>またはを使用している場合) は、テクスチャのサイズを最小限に抑えてください。  解像度が低くなると、画質が低下する可能性があるので、品質とパフォーマンスのバランスを適切に見つけることができます。|  
|Opacity|半透明の3d コンテンツ (反射など) をレンダリングする場合は、を1より小さい値に<xref:System.Windows.Media.Brush.Opacity%2A>設定<xref:System.Windows.Media.Media3D.DiffuseMaterial.Color%2A> `Viewport3D.Opacity`することによって、別<xref:System.Windows.Controls.Viewport3D>の半透明のを作成するのではなく、(またはを使用して) ブラシまたはマテリアルの不透明度プロパティを使用します。|  
|<xref:System.Windows.Controls.Viewport3D>|シーンで使用し<xref:System.Windows.Controls.Viewport3D>ているオブジェクトの数を最小限に抑えます。  モデルごとに個別の Viewport3D インスタンスを作成するのではなく、複数の3D モデルを同じ Viewport3D に配置します。|  
|<xref:System.Windows.Freezable>|通常は、、 <xref:System.Windows.Media.Media3D.MeshGeometry3D> <xref:System.Windows.Media.Media3D.GeometryModel3D>、ブラシ、マテリアルを再利用すると便利です。  は、から`Freezable`派生したものであるため、すべてはマルチ parentにできます。|  
|<xref:System.Windows.Freezable>|アプリケーションで<xref:System.Windows.Freezable.Freeze%2A>プロパティが変更されていない場合は、freezable でメソッドを呼び出します。  固定すると、ワーキングセットを減らして速度を上げることができます。|  
|<xref:System.Windows.Media.Brush>|ブラシ<xref:System.Windows.Media.ImageBrush>の内容が<xref:System.Windows.Media.DrawingBrush>変更されない場合は、またはの<xref:System.Windows.Media.VisualBrush>代わりにを使用します。  2d コンテンツは、を<xref:System.Windows.Controls.Image>使用<xref:System.Windows.Media.Imaging.RenderTargetBitmap>し<xref:System.Windows.Media.ImageBrush>てに変換し、で使用できます。|  
|<xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A>|実際に<xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> <xref:System.Windows.Media.Media3D.GeometryModel3D>の背面を見る必要がない場合は、を使用しないでください。|  
|<xref:System.Windows.Media.Media3D.Light>|ライト速度 (最速から低速):<br /><br /> <xref:System.Windows.Media.Media3D.AmbientLight><br /><br /> <xref:System.Windows.Media.Media3D.DirectionalLight><br /><br /> <xref:System.Windows.Media.Media3D.PointLight><br /><br /> <xref:System.Windows.Media.Media3D.SpotLight>|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|次の制限事項の下でメッシュサイズを維持してください:<br /><br /> <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>:20001 <xref:System.Windows.Media.Media3D.Point3D>インスタンス<br /><br /> <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>:60003 <xref:System.Int32>インスタンス|  
|<xref:System.Windows.Media.Media3D.Material>|素材の速度 (最速から低速):<br /><br /> <xref:System.Windows.Media.Media3D.EmissiveMaterial><br /><br /> <xref:System.Windows.Media.Media3D.DiffuseMaterial><br /><br /> <xref:System.Windows.Media.Media3D.SpecularMaterial>|  
|<xref:System.Windows.Media.Brush>|[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]3D は、一貫した方法で非表示のブラシ (黒のアンビエントブラシ、クリアブラシなど) をオプトアウトしません。  これらをシーンから省略することを検討してください。|  
|<xref:System.Windows.Media.Media3D.MaterialGroup>|内の各<xref:System.Windows.Media.Media3D.Material>で別のレンダリングパスが生成されるため、多くの素材を含め、単純な素材でも、GPUでの入力要求が大幅に増加する可能性があります。<xref:System.Windows.Media.Media3D.MaterialGroup>  の素材<xref:System.Windows.Media.Media3D.MaterialGroup>の数を最小限に抑えます。|  
  
## <a name="performance-impact-low"></a>パフォーマンスへの影響:Low  
  
|プロパティ|推奨事項|  
|-|-|  
|<xref:System.Windows.Media.Media3D.Transform3DGroup>|アニメーションまたはデータバインディングが不要な場合は、複数の変換を含む変換グループを使用するの<xref:System.Windows.Media.Media3D.MatrixTransform3D>ではなく、1つのを使用して、変換グループに独立して存在するすべての変換の積として設定します。|  
|<xref:System.Windows.Media.Media3D.Light>|シーンのライト数を最小限に抑えます。 シーン内のライトが多すぎると[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 、ソフトウェアのレンダリングにフォールバックします。  制限は、約 110 <xref:System.Windows.Media.Media3D.DirectionalLight>オブジェクト、70 <xref:System.Windows.Media.Media3D.PointLight>オブジェクト、または<xref:System.Windows.Media.Media3D.SpotLight> 40 オブジェクトです。|  
|<xref:System.Windows.Media.Media3D.ModelVisual3D>|オブジェクトを別<xref:System.Windows.Media.Media3D.ModelVisual3D>のインスタンスに配置することで、オブジェクトを静的オブジェクトから分離します。  ModelVisual3D は<xref:System.Windows.Media.Media3D.GeometryModel3D> 、変換された境界をキャッシュするため、"重い" です。  GeometryModel3D はモデルとして最適化されています。ModelVisual3D はシーンノードになるように最適化されています。  ModelVisual3D を使用して、GeometryModel3D の共有インスタンスをシーンに配置します。|  
|<xref:System.Windows.Media.Media3D.Light>|シーンのライト数を変更する回数を最小限に抑えます。  これらの構成が既に存在していて、シェーダーがキャッシュされている場合を除き、ライト数を変更するたびにシェーダーの再生成と再コンパイルが行われます。|  
|淡色|黒のライトは表示されませんが、レンダリング時間が追加されます。省略することを検討してください。|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|MeshGeometry3D's [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 、<xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> 、、<xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>など、の大きなコレクションの構築時間を最小限に抑えるには、値の作成前にコレクションのサイズを事前に設定します。 <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A> 可能であれば、コレクションのコンストラクターに、配列やリストなどの事前設定されたデータ構造を渡します。|  
  
## <a name="see-also"></a>関連項目

- [3-D グラフィックスの概要](3-d-graphics-overview.md)
