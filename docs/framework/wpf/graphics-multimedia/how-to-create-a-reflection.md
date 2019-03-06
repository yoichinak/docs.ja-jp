---
title: '方法: 反射を作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating reflections [WPF]
- brushes [WPF], creating reflections
- reflections [WPF], creating
ms.assetid: 4f017e16-ab80-43c7-98df-03b6bddbb203
ms.openlocfilehash: 8d29b29d349e9a5ee76ace72837d67e791c25d51
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57353570"
---
# <a name="how-to-create-a-reflection"></a>方法: 反射を作成する
この例は、使用する方法を示します、<xref:System.Windows.Media.VisualBrush>反射を作成します。 <xref:System.Windows.Media.VisualBrush>既存のビジュアルを表示することができます、反射や拡大などの興味深い視覚効果を生成するために、この機能を使用することができます。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Media.VisualBrush>の反射を作成、<xref:System.Windows.Controls.Border>いくつかの要素を格納しています。 次の図は、この例で生成される出力を示しています。  
  
 ![A がビジュアル オブジェクトを反映](./media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")  
反映された Visual オブジェクト  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 画面の一部を拡大する方法と反射を作成する方法を示す例が含まれているサンプル全体については、次を参照してください。 [VisualBrush のサンプル](https://go.microsoft.com/fwlink/?LinkID=160049)します。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Media.VisualBrush>
- [イメージ、描画、およびビジュアルによる塗りつぶし](painting-with-images-drawings-and-visuals.md)
