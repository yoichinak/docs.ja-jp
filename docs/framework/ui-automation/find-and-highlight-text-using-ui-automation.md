---
title: UI オートメーションを使用した、テキストの検索と強調表示
description: UI オートメーションを使用してテキストを検索し、強調表示します。 例では、テキストコントロールのコンテンツ内で文字列の出現箇所を順番に検索し、強調表示します。
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
ms.openlocfilehash: e4aca4b5ccdbc429a3d6267afc09b9f8b99cd7e9
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164201"
---
# <a name="find-and-highlight-text-using-ui-automation"></a>UI オートメーションを使用した、テキストの検索と強調表示
> [!NOTE]
> このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。  
  
 このトピックでは、を使用して、テキストコントロールのコンテンツ内の文字列の出現箇所を順番に検索し、強調表示する方法を示し [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] ます。  
  
## <a name="example"></a>例  
 次の例では、 <xref:System.Windows.Automation.TextPattern> テキストコントロールからオブジェクトを取得します。 <xref:System.Windows.Automation.Text.TextPatternRange>その後、ドキュメント全体のテキストコンテンツを表すオブジェクトが、こののプロパティを使用して作成され <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> <xref:System.Windows.Automation.TextPattern> ます。 その <xref:System.Windows.Automation.Text.TextPatternRange> 後、順次検索と強調表示の機能に対して、2つのオブジェクトが作成されます。  
  
[!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
[!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#SearchTarget](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#searchtarget)]
[!code-vb[FindText#SearchTarget](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#searchtarget)]  
  
## <a name="see-also"></a>関連項目

- [UI オートメーションを使用した、テキストの検索と強調表示](find-and-highlight-text-using-ui-automation.md)
