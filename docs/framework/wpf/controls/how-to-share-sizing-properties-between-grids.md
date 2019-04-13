---
title: '方法: グリッド間でサイズ設定プロパティを共有する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], sharing sizing data of columns
- sizing data in Grid controls [WPF]
- Grid control [WPF], sharing sizing data of rows
ms.assetid: a0535a6f-ff04-4b25-9912-7dd856e11044
ms.openlocfilehash: d5ab2ac612d55c8cbc34ae6d7d9d63b9f8aa23e7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59190341"
---
# <a name="how-to-share-sizing-properties-between-grids"></a>方法: グリッド間でサイズ設定プロパティを共有する
この例は、列のサイズ設定データを共有する方法を示していて、行の間で<xref:System.Windows.Controls.Grid>一貫性のあるサイズ設定するには要素です。  
  
## <a name="example"></a>例  
 次の例では、2 つを紹介<xref:System.Windows.Controls.Grid>要素の親の子要素として<xref:System.Windows.Controls.DockPanel>します。 <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A>添付プロパティの<xref:System.Windows.Controls.Grid>親が定義されて<xref:System.Windows.Controls.DockPanel>します。  
  
 例では、2 つを使用してプロパティ値を操作する<xref:System.Windows.Controls.Button>要素は、ブール型プロパティ値の各要素は 1 つ。 ときに、<xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A>プロパティの値に設定されて`true`の各列または行のメンバー、<xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A>行または列のコンテンツに関係なく、サイズ設定情報を共有します。  
  
 [!code-xaml[gridIssharedsizescopeProp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#1)]  
  
 ...  
  
 [!code-xaml[gridIssharedsizescopeProp#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]  
  
 分離コード例では、次の処理方法をボタン<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベントを発生させます。 例では、これらのメソッド呼び出しの結果を書き込みます<xref:System.Windows.Controls.TextBlock>使用に関連する要素が文字列として新しいプロパティ値を出力するメソッドを取得します。  
  
 [!code-csharp[gridIssharedsizescopeProp#3](~/samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml.cs#3)]
 [!code-vb[gridIssharedsizescopeProp#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gridIssharedsizescopeProp/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A>
- [パネルの概要](panels-overview.md)
