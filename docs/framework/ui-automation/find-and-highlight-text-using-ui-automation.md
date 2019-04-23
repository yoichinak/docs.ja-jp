---
title: UI オートメーションを使用した、テキストの検索と強調表示
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text, highlighting
- finding text
- text, finding
- UI automation, highlighting text
- UI automation, finding text
- highlighting text
ms.assetid: b77693f5-87bb-4b29-a297-05ff882e2044
ms.openlocfilehash: fafd3fc7345f94d3907163ff9dcf0ab293f85f3f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59157158"
---
# <a name="find-and-highlight-text-using-ui-automation"></a>UI オートメーションを使用した、テキストの検索と強調表示
> [!NOTE]
>  このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 に関する最新情報については[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]を参照してください[Windows Automation API:UI オートメーション](https://go.microsoft.com/fwlink/?LinkID=156746)します。  
  
 このトピックでは、順番に検索し、文字列を使用してテキスト コントロールのコンテンツ内で出現するたびに強調表示する方法を示します[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]します。  
  
## <a name="example"></a>例  
 次の例では、取得、<xref:System.Windows.Automation.TextPattern>テキスト コントロールからのオブジェクト。 A <xref:System.Windows.Automation.Text.TextPatternRange> 、文書全体のテキスト コンテンツを表す、オブジェクトを使用して作成し、<xref:System.Windows.Automation.TextPattern.DocumentRange%2A>プロパティのこの<xref:System.Windows.Automation.TextPattern>します。 2 つ追加<xref:System.Windows.Automation.Text.TextPatternRange>オブジェクトは、順次検索が作成され、機能を強調表示します。  
  
[!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
[!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#SearchTarget](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#searchtarget)]
[!code-vb[FindText#SearchTarget](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#searchtarget)]  
  
## <a name="see-also"></a>関連項目

- [UI オートメーションを使用した、テキストの検索と強調表示](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)
