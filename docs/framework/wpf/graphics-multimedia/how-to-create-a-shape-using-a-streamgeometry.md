---
title: '方法: StreamGeometry を使用して図形を作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], shapes
- shapes [WPF], creating with StreamGeometry class
ms.assetid: 08f7c8ce-074b-49cd-9aba-cc9592d4ee51
ms.openlocfilehash: fd191e4cfdfa33c144389d4871a9641e9c811ed3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62054574"
---
# <a name="how-to-create-a-shape-using-a-streamgeometry"></a>方法: StreamGeometry を使用して図形を作成する
<xref:System.Windows.Media.StreamGeometry> 軽量の代わりには、<xref:System.Windows.Media.PathGeometry>幾何学的図形を作成するためです。 使用して、<xref:System.Windows.Media.StreamGeometry>複雑なジオメトリを記述する必要がある場合がデータ バインディング、アニメーション、または変更をサポートするオーバーヘッドを作成したくないです。 など、効率的であるため、<xref:System.Windows.Media.StreamGeometry>クラスは、装飾の記述に適しています。  
  
## <a name="example"></a>例  
 次の例では、属性構文を使用して、三角形を作成する<xref:System.Windows.Media.StreamGeometry>で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]します。  
  
 [!code-xaml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 詳細については<xref:System.Windows.Media.StreamGeometry>属性構文を参照してください、[パス マークアップ構文](path-markup-syntax.md)ページ。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Media.StreamGeometry>コードで三角形を定義します。 最初に、例、<xref:System.Windows.Media.StreamGeometry>を取得し、<xref:System.Windows.Media.StreamGeometryContext>それを使って、三角形の説明をします。  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/StreamGeometryTriangleExample.cs#streamgeometrytriangleexamplewholepage)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/streamgeometrytriangleexample.vb#streamgeometrytriangleexamplewholepage)]  
  
## <a name="example"></a>例  
 次の例は、使用するメソッドを作成、<xref:System.Windows.Media.StreamGeometry>と<xref:System.Windows.Media.StreamGeometryContext>を指定したパラメーターに基づいて、幾何学図形を定義します。  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#StreamGeometryExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/StreamGeometryExample.cs#streamgeometryexamplewholepage)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#StreamGeometryExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/streamgeometryexample.vb#streamgeometryexamplewholepage)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Media.StreamGeometry>
- <xref:System.Windows.Media.StreamGeometryContext>
- [PathGeometry を使用して図形を作成する](how-to-create-a-shape-by-using-a-pathgeometry.md)
- [ジオメトリの概要](geometry-overview.md)
