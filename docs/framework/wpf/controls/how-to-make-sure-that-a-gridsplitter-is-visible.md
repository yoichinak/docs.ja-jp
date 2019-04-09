---
title: '方法: GridSplitter を表示されるようにする'
ms.date: 03/30/2017
helpviewer_keywords:
- GridSplitter control [WPF], ensuring visibility of
ms.assetid: 0a62a964-89c8-48f0-9023-5df721a8cf47
ms.openlocfilehash: b7543d14ba39d854b5a2c3f4d0d19b9a457ea89b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59147148"
---
# <a name="how-to-make-sure-that-a-gridsplitter-is-visible"></a>方法: GridSplitter を表示されるようにする
確認する方法を示します、<xref:System.Windows.Controls.GridSplitter>で他のコントロールによってコントロールが非、<xref:System.Windows.Controls.Grid>します。  
  
## <a name="example"></a>例  
 <xref:System.Windows.Controls.Panel.Children%2A>の<xref:System.Windows.Controls.Grid>コントロールは、マークアップまたはコードで定義されている順序で表示されます。 <xref:System.Windows.Controls.GridSplitter> 最後の要素として定義する実行されていない場合、その他のコントロールでコントロールを隠すことが、<xref:System.Windows.Controls.Panel.Children%2A>コレクションまたはその他を付与するかどうかより高度な制御<xref:System.Windows.Controls.Panel.ZIndexProperty>します。  
  
 防ぐために非表示<xref:System.Windows.Controls.GridSplitter>コントロールは、次のいずれかを実行します。  
  
-   確認します<xref:System.Windows.Controls.GridSplitter>コントロールは、最後の<xref:System.Windows.Controls.Panel.Children%2A>に追加、<xref:System.Windows.Controls.Grid>します。 次の例は、<xref:System.Windows.Controls.GridSplitter>の最後の要素として、<xref:System.Windows.Controls.Panel.Children%2A>のコレクション、<xref:System.Windows.Controls.Grid>します。  
  
 [!code-xaml[GridSplitterSnips#GridSplitterLastChild](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplitterlastchild)]  
  
-   設定、<xref:System.Windows.Controls.Panel.ZIndexProperty>上、<xref:System.Windows.Controls.GridSplitter>にコントロールを非はそれ以外の場合よりも高くなります。 次の例では、<xref:System.Windows.Controls.GridSplitter>より高度な制御<xref:System.Windows.Controls.Panel.ZIndexProperty>よりも、<xref:System.Windows.Controls.Button>コントロール。  
  
 [!code-xaml[GridSplitterSnips#GridSplitterZIndex](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplitterzindex)]  
  
-   それ以外の場合非表示にするコントロールのマージンを設定、<xref:System.Windows.Controls.GridSplitter>ように、<xref:System.Windows.Controls.GridSplitter>公開されます。 次の例では、余白を設定コントロールをオーバーレイはそれ以外の場合と非表示にする、<xref:System.Windows.Controls.GridSplitter>します。  
  
 [!code-xaml[GridSplitterSnips#GridSplitterMargin](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplittermargin)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.GridSplitter>
- [方法のトピック](gridsplitter-how-to-topics.md)
