---
title: UI オートメーションを使用して混合テキスト属性の詳細を取得する
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d0e4c005-abd1-42bb-92a4-5faf87097311
ms.openlocfilehash: f52ff1b669f821d102a65888189d9bbf2c000da8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59158484"
---
# <a name="obtain-mixed-text-attribute-details-using-ui-automation"></a>UI オートメーションを使用して混合テキスト属性の詳細を取得する
> [!NOTE]
>  このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 に関する最新情報については[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]を参照してください[Windows Automation API:UI オートメーション](https://go.microsoft.com/fwlink/?LinkID=156746)します。  
  
 このトピックでは、 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] を使用して、複数の属性値にまたがるテキスト範囲からテキスト属性の詳細を取得する方法を示します。 テキスト範囲は、ドキュメント内のキャレットの現在の位置 (または低次元選択)、テキストの連続した選択、非連続のテキスト選択のコレクション、またはドキュメントのテキスト コンテンツ全体に対応します。  
  
## <a name="example"></a>例  
 次のコード例は、 <xref:System.Windows.Automation.TextPattern.FontNameAttribute> が <xref:System.Windows.Automation.Text.TextPatternRange.GetAttributeValue%2A> オブジェクトを返すテキスト範囲から <xref:System.Windows.Automation.TextPattern.MixedAttributeValue> を取得する方法を示しています。  
  
[!code-csharp[FindText#RetrieveMixedAttributes](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#retrievemixedattributes)]
[!code-vb[FindText#RetrieveMixedAttributes](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#retrievemixedattributes)]  
  
 <xref:System.Windows.Automation.TextPattern> コントロール パターンは、 <xref:System.Windows.Automation.Text.TextPatternRange> クラスと共に、基本的なテキスト属性、プロパティ、およびメソッドをサポートします。 <xref:System.Windows.Automation.TextPattern> または <xref:System.Windows.Automation.Text.TextPatternRange>によってサポートされないコントロール固有の機能の場合、UI オートメーション クライアントが対応するネイティブ オブジェクト モデルにアクセスできるように、 <xref:System.Windows.Automation.AutomationElement> クラスがメソッドを提供します。  
  
## <a name="see-also"></a>関連項目

- [UI オートメーション TextPattern の概要](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)
- [UI オートメーションを使用した、テキスト ボックスへのコンテンツの追加](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)
- [UI オートメーションを使用した、テキストの検索と強調表示](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)
- [UI オートメーション コントロール パターンの概要](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [クライアントの UI オートメーション コントロール パターン](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [UI オートメーションを使用してテキスト属性を取得する](../../../docs/framework/ui-automation/obtain-text-attributes-using-ui-automation.md)
