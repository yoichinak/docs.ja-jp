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
ms.openlocfilehash: 52b9b99b0af38d797e4a3c98dc0979211c930c1f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923378"
---
# <a name="how-to-hit-test-geometry-in-a-visual"></a>方法: ビジュアル内のジオメトリのヒット テストを実行する
この例では、1つ<xref:System.Windows.Media.Geometry>以上のオブジェクトで構成されるビジュアルオブジェクトに対してヒットテストを実行する方法を示します。  
  
## <a name="example"></a>例  
 次の例は、 <xref:System.Windows.Media.DrawingGroup> <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A>メソッドを使用するビジュアルオブジェクトからを取得する方法を示しています。 次に、 <xref:System.Windows.Media.DrawingGroup>内の各描画のレンダリングされたコンテンツに対してヒットテストが実行され、ヒットしたジオメトリが特定されます。  
  
> [!NOTE]
> ほとんどの場合、 <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>メソッドを使用して、ビジュアルの描画されたコンテンツのいずれかにポイントが交差するかどうかを判断します。  
  
 [!code-csharp[VisualsOverview#VisualsOverviewSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#visualsoverviewsnippet4)]
 [!code-vb[VisualsOverview#VisualsOverviewSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#visualsoverviewsnippet4)]  
  
 メソッドは、指定されたまたは<xref:System.Windows.Media.Geometry>を使用してヒットテストを<xref:System.Windows.Point>実行できるようにする、オーバーロードされたメソッドです。 <xref:System.Windows.Media.Geometry.FillContains%2A> ジオメトリに線が付いている場合は、塗りつぶしの境界の外側までストロークを拡張できます。 そのような場合は、に<xref:System.Windows.Media.Geometry.StrokeContains%2A> <xref:System.Windows.Media.Geometry.FillContains%2A>加えて、を呼び出すこともできます。  
  
 また、ベジエフラット化<xref:System.Windows.Media.ToleranceType>の目的で使用されるを指定することもできます。  
  
> [!NOTE]
> このサンプルでは、ジオメトリに適用される可能性のある変換やクリッピングは考慮していません。 また、スタイルが設定されたコントロールには直接関連付けられた描画がないので、このサンプルはスタイルが設定されたコントロールに対しては機能しません。  
  
## <a name="see-also"></a>関連項目

- [ビジュアル層でのヒット テスト](hit-testing-in-the-visual-layer.md)
- [パラメーターとしてジオメトリを使用してヒット テストを実行する](how-to-hit-test-using-geometry-as-a-parameter.md)
