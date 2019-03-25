---
title: '方法: FlowDocument の列区切り属性を使用する'
ms.date: 03/30/2017
helpviewer_keywords:
- FlowDocument column-separating attributes
- column-separating attributes
- documents [WPF], FlowDocument column-separating attributes
ms.assetid: c7a822f8-aeca-45bd-a258-2852ff28005c
ms.openlocfilehash: 27491b21da587fa198061ba52d8daed5d3f28de3
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2019
ms.locfileid: "58410902"
---
# <a name="how-to-use-flowdocument-column-separating-attributes"></a>方法: FlowDocument の列区切り属性を使用する
この例では、列区切りの機能を使用して、<xref:System.Windows.Documents.FlowDocument>します。  
  
## <a name="example"></a>例  
 次の例では、定義、 <xref:System.Windows.Documents.FlowDocument>、設定と、 <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>、 <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>、および<xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A>属性。  <xref:System.Windows.Documents.FlowDocument>サンプルのコンテンツの 1 つの段落が含まれています。  
  
 [!code-xaml[FlowDocumentSnippets#_FlowDocumentColumnStuffXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml#_flowdocumentcolumnstuffxaml)]  
  
 次の図の効果を示します、 <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>、 <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>、および<xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A>でレンダリングされる属性<xref:System.Windows.Documents.FlowDocument>します。  
  
 ![FlowDocument Intra 列属性を示すスクリーン ショット。](./media/how-to-use-flowdocument-column-separating-attributes/flowdocument-intra-column.png)
