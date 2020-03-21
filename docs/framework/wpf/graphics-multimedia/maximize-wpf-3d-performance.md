---
title: 3D パフォーマンスを最大化
ms.date: 03/30/2017
helpviewer_keywords:
- 3D graphics [WPF]
ms.assetid: 4bcf949d-d92f-4d8d-8a9b-1e4c61b25bf6
ms.openlocfilehash: 3825ea8e57c6863e2ee654072efda623db21c2a8
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111999"
---
# <a name="maximize-wpf-3d-performance"></a>WPF の 3D パフォーマンスの最大化
を[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]使用して 3D コントロールを構築し、アプリケーションに 3D シーンを含める場合は、パフォーマンスの最適化を検討することが重要です。 このトピックでは、アプリケーションにパフォーマンスに影響を与える 3D クラスとプロパティの一覧と、それらを使用する際のパフォーマンスを最適化するための推奨事項を示します。  
  
 このトピックでは、3D[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]フィーチャの高度な理解を前提としています。 このドキュメントの提案は、ピクセル シェーダー バージョン 2.0 および頂点シェーダー バージョン 2.0 をサポートするハードウェアとして大まかに定義された "レンダリング層 2" に適用されます。 詳細については、「グラフィックス[レンダリング層](../advanced/graphics-rendering-tiers.md)」を参照してください。  
  
## <a name="performance-impact-high"></a>パフォーマンスへの影響: 高  
  
|プロパティ|推奨|  
|-|-|  
|<xref:System.Windows.Media.Brush>|ブラシ速度(最も速く遅い):<br /><br /> <xref:System.Windows.Media.SolidColorBrush><br /><br /> <xref:System.Windows.Media.LinearGradientBrush><br /><br /> <xref:System.Windows.Media.ImageBrush><br /><br /> <xref:System.Windows.Media.DrawingBrush>(キャッシュ)<br /><br /> <xref:System.Windows.Media.VisualBrush>(キャッシュ)<br /><br /> <xref:System.Windows.Media.RadialGradientBrush><br /><br /> <xref:System.Windows.Media.DrawingBrush>(キャッシュされていない)<br /><br /> <xref:System.Windows.Media.VisualBrush>(キャッシュされていない)|  
|<xref:System.Windows.UIElement.ClipToBoundsProperty>|明示的`Viewport3D.ClipToBounds`に Viewport3D の四角形[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]にコンテンツを明示的にクリップ<xref:System.Windows.Controls.Viewport3D>する必要がない場合は false に設定します。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]アンチエイリアスされたクリッピングは非常に遅く、`ClipToBounds`デフォルトでは<xref:System.Windows.Controls.Viewport3D>有効(遅い)です。|  
|<xref:System.Windows.UIElement.IsHitTestVisible%2A>|マウス`Viewport3D.IsHitTestVisible`ヒットテストを実行するときに、コンテンツ[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]を考慮する必要がない場合<xref:System.Windows.Controls.Viewport3D>は false に設定します。  3Dコンテンツのヒットテストはソフトウェアで行われ、大きなメッシュで遅くなることがあります。 <xref:System.Windows.UIElement.IsHitTestVisible%2A>は、既定では有効 (低速<xref:System.Windows.Controls.Viewport3D>) になっています。|  
|<xref:System.Windows.Media.Media3D.GeometryModel3D>|異なる材料または変換が必要な場合にのみ、異なるモデルを作成します。  それ以外の場合は、同じ<xref:System.Windows.Media.Media3D.GeometryModel3D>マテリアルと変換を使用して多数のインスタンスを結合して、<xref:System.Windows.Media.Media3D.GeometryModel3D>いくつかの<xref:System.Windows.Media.Media3D.MeshGeometry3D>大きなインスタンスとインスタンスに変換します。|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|メッシュ アニメーション (フレーム単位でメッシュの個々の頂点を変更する) は、常に[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]効率的であるとは限りません。  各頂点が変更されたときに変更通知のパフォーマンスへの影響を最小限に抑えるには、頂点ごとの変更を実行する前に、ビジュアル ツリーからメッシュをデタッチします。  メッシュが修正されたら、ビジュアル ツリーに再アタッチします。  また、この方法でアニメーション化されるメッシュのサイズを最小限に抑えるようにしてください。|  
|3D アンチエイリアシング|レンダリング速度を上げるには、添付プロパティ<xref:System.Windows.Controls.Viewport3D><xref:System.Windows.Media.RenderOptions.EdgeMode%2A>を に設定して、マルチ`Aliased`サンプリングを無効にします。  Windows では、ピクセルあたり 4 サンプルの 3D アンチエイリアシングがデフォルトで有効になっています。|  
|Text|3D シーン内のライブ テキスト (<xref:System.Windows.Media.DrawingBrush>または<xref:System.Windows.Media.VisualBrush>) 内にあるためライブ テキストは低速になる可能性があります。 テキストが変更されない限り、テキストのイメージ<xref:System.Windows.Media.Imaging.RenderTargetBitmap>を使用するようにしてください。|  
|<xref:System.Windows.Media.TileBrush>|ブラシのコンテンツが静的<xref:System.Windows.Media.VisualBrush>でないために<xref:System.Windows.Media.DrawingBrush>3D シーンで または を使用する必要がある場合は、ブラシをキャッシュしてみます (<xref:System.Windows.Media.RenderOptions.CachingHint%2A>添付`Cache`プロパティを に設定します)。  最小および最大スケールの無効化しきい値 (添付プロパティ<xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMinimum%2A>と) を<xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A>設定して、キャッシュされたブラシがあまり頻繁に再生成されないようにしながら、必要な品質レベルを維持します。  デフォルトでは、<xref:System.Windows.Media.DrawingBrush><xref:System.Windows.Media.VisualBrush>キャッシュされないので、ブラシでペイントしたものを再描画する必要があるたびに、ブラシの内容全体を中間サーフェスに再レンダリングする必要があります。|  
|<xref:System.Windows.Media.Effects.BitmapEffect>|<xref:System.Windows.Media.Effects.BitmapEffect>影響を受けるすべてのコンテンツを、ハードウェアアクセラレーションなしでレンダリングします。  最高のパフォーマンスを得るには<xref:System.Windows.Media.Effects.BitmapEffect>、 を使用しないでください。|  
  
## <a name="performance-impact-medium"></a>パフォーマンスへの影響: 中  
  
|プロパティ|推奨|  
|-|-|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|メッシュが共有頂点を持つ三角形に隣接するものとして定義され、それらの頂点の位置、法線、テクスチャ座標が同じである場合は、各共有頂点を 1 回だけ定義し<xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>、次にインデックスで三角形を定義します。|  
|<xref:System.Windows.Media.ImageBrush>|サイズを明示的に制御する場合 (または を使用<xref:System.Windows.Media.Imaging.RenderTargetBitmap>している場合) は、テクスチャ サイズを最小限に<xref:System.Windows.Media.ImageBrush>抑えるようにしてください。  解像度の低いテクスチャは、画質を低下させる可能性があるため、品質とパフォーマンスのバランスを適切に見つけ出してください。|  
|Opacity|半透明の 3D コンテンツ(反射など)をレンダリングする場合は、1 未満の<xref:System.Windows.Media.Brush.Opacity%2A>値に設定<xref:System.Windows.Media.Media3D.DiffuseMaterial.Color%2A><xref:System.Windows.Controls.Viewport3D>`Viewport3D.Opacity`して個別の半透明を作成するのではなく、ブラシまたはマテリアルの不透明度プロパティを使用します(または)|  
|<xref:System.Windows.Controls.Viewport3D>|シーンで使用している<xref:System.Windows.Controls.Viewport3D>オブジェクトの数を最小限に抑えます。  各モデルに対して別々の Viewport3D インスタンスを作成するのではなく、同じ Viewport3D に多数の 3D モデルを配置します。|  
|<xref:System.Windows.Freezable>|通常、再利用する場合は、<xref:System.Windows.Media.Media3D.MeshGeometry3D><xref:System.Windows.Media.Media3D.GeometryModel3D>ブラシ、およびマテリアルを使用すると効果的です。  から派生しているため、すべてマルチペアレント可能です`Freezable`。|  
|<xref:System.Windows.Freezable>|アプリケーションで<xref:System.Windows.Freezable.Freeze%2A>プロパティが変更されない場合は、Freezables でメソッドを呼び出します。  凍結は、ワーキングセットを減少させ、速度を増加させることができます。|  
|<xref:System.Windows.Media.Brush>|ブラシ<xref:System.Windows.Media.ImageBrush>の<xref:System.Windows.Media.VisualBrush>内容<xref:System.Windows.Media.DrawingBrush>が変わらないかの代わりに使用します。  2D コンテンツは<xref:System.Windows.Controls.Image>、ビア<xref:System.Windows.Media.Imaging.RenderTargetBitmap>に変換してから、 で使用<xref:System.Windows.Media.ImageBrush>できます。|  
|<xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A>|あなたの後ろ面<xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A>を実際に見る必要がない限り、使用<xref:System.Windows.Media.Media3D.GeometryModel3D>しないでください。|  
|<xref:System.Windows.Media.Media3D.Light>|軽い速度(最も速く遅い):<br /><br /> <xref:System.Windows.Media.Media3D.AmbientLight><br /><br /> <xref:System.Windows.Media.Media3D.DirectionalLight><br /><br /> <xref:System.Windows.Media.Media3D.PointLight><br /><br /> <xref:System.Windows.Media.Media3D.SpotLight>|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|メッシュ サイズを次の制限の下に保持するようにしてください。<br /><br /> <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>: 20,001<xref:System.Windows.Media.Media3D.Point3D>インスタンス<br /><br /> <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>: 60,003<xref:System.Int32>インスタンス|  
|<xref:System.Windows.Media.Media3D.Material>|材料速度(最も速く遅い):<br /><br /> <xref:System.Windows.Media.Media3D.EmissiveMaterial><br /><br /> <xref:System.Windows.Media.Media3D.DiffuseMaterial><br /><br /> <xref:System.Windows.Media.Media3D.SpecularMaterial>|  
|<xref:System.Windows.Media.Brush>|[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]3D は、不可視ブラシ (黒いアンビエント ブラシ、クリア ブラシなど) を一貫した方法で除外しません。  シーンからこれらを省略することを検討してください。|  
|<xref:System.Windows.Media.Media3D.MaterialGroup>|1<xref:System.Windows.Media.Media3D.Material>つの<xref:System.Windows.Media.Media3D.MaterialGroup>レンダリング パスのそれぞれは、多くのマテリアル(単純なマテリアルも含む)を含む GPU の充填要求を劇的に増加させる可能性があります。  の材料の数を最小限に<xref:System.Windows.Media.Media3D.MaterialGroup>抑えます。|  
  
## <a name="performance-impact-low"></a>パフォーマンスへの影響: 低  
  
|プロパティ|推奨|  
|-|-|  
|<xref:System.Windows.Media.Media3D.Transform3DGroup>|複数の変換を含むトランスフォーム グループを使用する代わりに、アニメーションやデータ バインディングが必要ない場合<xref:System.Windows.Media.Media3D.MatrixTransform3D>は、変換グループに独立して存在するすべての変換の積に設定する単一の を使用します。|  
|<xref:System.Windows.Media.Media3D.Light>|シーン内のライトの数を最小限に抑えます。 シーン内のライトが多すぎると、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]ソフトウェア レンダリングに強制的に戻ります。  制限は、およそ 110<xref:System.Windows.Media.Media3D.DirectionalLight>オブジェクト、70<xref:System.Windows.Media.Media3D.PointLight>個のオブジェクト<xref:System.Windows.Media.Media3D.SpotLight>、または 40 個のオブジェクトです。|  
|<xref:System.Windows.Media.Media3D.ModelVisual3D>|移動オブジェクトを別のインスタンスに配置して、静的<xref:System.Windows.Media.Media3D.ModelVisual3D>オブジェクトから分離します。  ModelVisual3D は、変換された境界<xref:System.Windows.Media.Media3D.GeometryModel3D>をキャッシュするためよりも"重い" です。  ジオメトリモデル3Dはモデルに最適化されています。ModelVisual3D は、シーン ノードに最適化されています。  ModelVisual3D を使用して、ジオメトリモデル3D の共有インスタンスをシーンに配置します。|  
|<xref:System.Windows.Media.Media3D.Light>|シーン内のライトの数を変更する回数を最小限に抑えます。  ライトカウントの各変更は、その設定が以前に存在していた (したがって、そのシェーダーがキャッシュされている) 場合を除き、シェーダーの再生成と再コンパイルを強制します。|  
|浅煎り|黒のライトは表示されませんが、レンダリング時間が増えます。それらを省略することを検討してください。|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|MeshGeometry3D、 、 、、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A><xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A><xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A>および<xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>、 など、 で大規模なコレクションの構築時間を最小限に抑えるには、値の作成前にコレクションのサイズを事前に設定します。 可能であれば、配列やリストなどのデータ構造体を事前に設定したコレクションのコンストラクターを渡します。|  
  
## <a name="see-also"></a>関連項目

- [3D グラフィックスの概要](3-d-graphics-overview.md)
