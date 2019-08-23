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
ms.openlocfilehash: 8bed7784b00f49178c9a87def74b62f7ce620ec7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923404"
---
# <a name="how-to-hit-test-using-geometry-as-a-parameter"></a>方法: パラメーターとしてジオメトリを使用してヒット テストを実行する
この例では、をヒットテストパラメーターとして使用して<xref:System.Windows.Media.Geometry> 、ビジュアルオブジェクトに対してヒットテストを実行する方法を示します。  
  
## <a name="example"></a>例  
 次の例では、 <xref:System.Windows.Media.GeometryHitTestParameters> <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>メソッドに対してを使用してヒットテストを設定する方法を示します。 メソッドに渡される<xref:System.Windows.Media.Geometry>値は、ヒットテストの範囲を拡張するためにオブジェクトを作成するために使用されます。 <xref:System.Windows.Point> `OnMouseDown`  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet10](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet10)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet10)]  
  
 <xref:System.Windows.Media.Geometry>の<xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> プロパティ<xref:System.Windows.Media.GeometryHitTestResult>は、をヒットテストパラメーターとして使用するヒットテストの結果に関する情報を提供します。 ヒット テストのジオメトリ (青い円) と対象のビジュアル オブジェクト (赤い正方形) の描画されるコンテンツとの関係を次の図に示します。  
  
 ![ヒットテストで使用される IntersectionDetail を示す図。](./media/how-to-hit-test-using-geometry-as-a-parameter/intersectiondetail-hit-test.png)  
  
 次の例は、 <xref:System.Windows.Media.Geometry>がヒットテストパラメーターとして使用されている場合にヒットテストコールバックを実装する方法を示しています。 パラメーターは、 <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A>プロパティの値<xref:System.Windows.Media.GeometryHitTestResult>を取得するためににキャストされます。 `result` プロパティ値を使用すると、ヒットテスト<xref:System.Windows.Media.Geometry>のターゲットのレンダリングされたコンテンツ内でヒットテストパラメーターが完全または部分的に含まれるかどうかを判断できます。 ここに示すサンプル コードでは、完全に対象の境界内に含まれるビジュアルについてのみ、ヒット テストの結果をリストに追加しています。  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet11](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet11)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet11)]  
  
> [!NOTE]
> 交差<xref:System.Windows.Media.HitTestResult>の詳細が<xref:System.Windows.Media.IntersectionDetail.Empty>の場合は、コールバックを呼び出さないでください。  
  
## <a name="see-also"></a>関連項目

- [ビジュアル層でのヒット テスト](hit-testing-in-the-visual-layer.md)
- [ビジュアル内のジオメトリのヒット テストを実行する](how-to-hit-test-geometry-in-a-visual.md)
