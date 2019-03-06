---
title: '方法: パラメーターとしてジオメトリを使用してヒット テストを実行する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], on visual objects using Geometry objects [WPF]
- visual objects [WPF], hit tests on
- Geometry objects [WPF], hit tests on visual objects [WPF]
ms.assetid: 6c8bdbf2-19e0-4fbb-bf89-c1252b2ebc61
ms.openlocfilehash: 15a33d05cb3ca4fd40f04170bd1756e466631275
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57366362"
---
# <a name="how-to-hit-test-using-geometry-as-a-parameter"></a>方法: パラメーターとしてジオメトリを使用してヒット テストを実行する
この例を使用して、ビジュアル オブジェクトに対してヒット テストを実行する方法を示しています、<xref:System.Windows.Media.Geometry>ヒット テスト パラメーター。  
  
## <a name="example"></a>例  
 次の例を使用してヒット テストを設定する方法を示しています。<xref:System.Windows.Media.GeometryHitTestParameters>の、<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>メソッド。 <xref:System.Windows.Point>に渡される値、`OnMouseDown`メソッドの使用を作成、<xref:System.Windows.Media.Geometry>ヒット テストの範囲を拡張するためにオブジェクト。  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet10](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet10)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet10)]  
  
 <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A>プロパティの<xref:System.Windows.Media.GeometryHitTestResult>を使用するヒット テストの結果に関する情報を提供します、<xref:System.Windows.Media.Geometry>ヒット テスト パラメーター。 ヒット テストのジオメトリ (青い円) と対象のビジュアル オブジェクト (赤い正方形) の描画されるコンテンツとの関係を次の図に示します。  
  
 ![ヒット テストで使用される IntersectionDetail のダイアグラム](./media/intersectiondetail01.png "IntersectionDetail01")  
ヒット テストのジオメトリと対象のビジュアル オブジェクトの交差部分  
  
 次の例は、ヒット テスト コールバックを実装する方法を示しています。 ときに、<xref:System.Windows.Media.Geometry>ヒット テスト パラメーターとして使用されます。 `result`にパラメーターをキャスト、<xref:System.Windows.Media.GeometryHitTestResult>の値を取得するために、<xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A>プロパティ。 プロパティの値を使用するかどうか、<xref:System.Windows.Media.Geometry>ヒット テスト パラメーター完全または部分的に含まれるヒット テスト対象の表示内容。 ここに示すサンプル コードでは、完全に対象の境界内に含まれるビジュアルについてのみ、ヒット テストの結果をリストに追加しています。  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet11](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet11)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet11)]  
  
> [!NOTE]
>  <xref:System.Windows.Media.HitTestResult> 、Intersectiondetail がときに、コールバックを呼び出すことはできません<xref:System.Windows.Media.IntersectionDetail.Empty>します。  
  
## <a name="see-also"></a>関連項目
- [ビジュアル層でのヒット テスト](hit-testing-in-the-visual-layer.md)
- [ビジュアル内のジオメトリのヒット テストを実行する](how-to-hit-test-geometry-in-a-visual.md)
