---
title: '方法: ビジュアル内のジオメトリのヒット テストを実行する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], on visual objects comprising Geometry objects [WPF]
- visual objects [WPF], hit tests on
- Geometry objects [WPF], visual objects comprising
ms.assetid: 8bf2643f-d7f9-4cb4-9ea6-5b893c23200d
ms.openlocfilehash: 87b626e575d889447ef061d1ed62ef28efe5dfeb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59227341"
---
# <a name="how-to-hit-test-geometry-in-a-visual"></a>方法: ビジュアル内のジオメトリのヒット テストを実行する
この例は、1 つまたは複数で構成されるビジュアル オブジェクトに対してヒット テストを実行する方法を示しています。<xref:System.Windows.Media.Geometry>オブジェクト。  
  
## <a name="example"></a>例  
 次の例は、取得する方法を示します、<xref:System.Windows.Media.DrawingGroup>を使用するビジュアル オブジェクトから、<xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A>メソッド。 各描画の描画されるコンテンツのヒット テストが実行、<xref:System.Windows.Media.DrawingGroup>をヒットしたジオメトリを判断します。  
  
> [!NOTE]
>  ほとんどの場合、使用すると、<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>ポイントと交差するビジュアルの表示内容にするかどうかを判断するメソッド。  
  
 [!code-csharp[VisualsOverview#VisualsOverviewSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#visualsoverviewsnippet4)]
 [!code-vb[VisualsOverview#VisualsOverviewSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#visualsoverviewsnippet4)]  
  
 <xref:System.Windows.Media.Geometry.FillContains%2A>メソッドがオーバー ロードされたメソッドを使用すると、指定されたを使用してヒット テストを<xref:System.Windows.Point>または<xref:System.Windows.Media.Geometry>します。 ジオメトリに線が付いている場合は、塗りつぶしの境界の外側までストロークを拡張できます。 呼び出すしたい場合は、<xref:System.Windows.Media.Geometry.StrokeContains%2A>に加えて<xref:System.Windows.Media.Geometry.FillContains%2A>します。  
  
 提供することも、<xref:System.Windows.Media.ToleranceType>ベジエ平坦化のために使用されます。  
  
> [!NOTE]
>  このサンプルでは、ジオメトリに適用される可能性のある変換やクリッピングは考慮していません。 また、スタイルが設定されたコントロールには直接関連付けられた描画がないので、このサンプルはスタイルが設定されたコントロールに対しては機能しません。  
  
## <a name="see-also"></a>関連項目

- [ビジュアル層でのヒット テスト](hit-testing-in-the-visual-layer.md)
- [パラメーターとしてジオメトリを使用してヒット テストを実行する](how-to-hit-test-using-geometry-as-a-parameter.md)
