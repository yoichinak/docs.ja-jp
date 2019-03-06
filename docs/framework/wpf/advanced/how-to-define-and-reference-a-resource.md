---
title: '方法: リソースを定義および参照する'
ms.date: 03/30/2017
helpviewer_keywords:
- resources [WPF], defining
- defining resources [WPF]
- resources [WPF], referencing
- referencing resources [WPF]
ms.assetid: b86b876b-0a10-489b-9a5d-581ea9b32406
ms.openlocfilehash: c429e3373ef1b78fba12dd5125af653f66cf5d74
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57371581"
---
# <a name="how-to-define-and-reference-a-resource"></a>方法: リソースを定義および参照する
この例は、リソースを定義し、内の属性を使用して参照する方法を示しています。[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]します。  
  
## <a name="example"></a>例  
 次の例では、2 種類のリソースを定義します。、<xref:System.Windows.Media.SolidColorBrush>リソース、およびいくつか<xref:System.Windows.Style>リソース。 <xref:System.Windows.Media.SolidColorBrush>リソース`MyBrush`各取るいくつかのプロパティの値を提供するため、<xref:System.Windows.Media.Brush>値を入力します。 <xref:System.Windows.Style>リソース`PageBackground`、`TitleText`と`Label`各対象になる特定のコントロールの種類。 スタイルは、そのスタイル リソースがリソース キーによって参照され、設定に使用されるときに、対象となるコントロールのさまざまなプロパティを設定、<xref:System.Windows.FrameworkElement.Style%2A>プロパティで定義されているいくつかの特定のコントロール要素の[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]します。  
  
 注いずれかのプロパティの setter 内で、`Label`スタイルを参照しても、`MyBrush`以前に定義されているリソース。 これは、一般的な手法が、リソースが解析され、指定した順序でリソース ディクショナリに入力したことに注意してください。 使用する場合は、ディクショナリ内で見つかった順序により、リソースが要求も、 [StaticResource マークアップ拡張機能](staticresource-markup-extension.md)他のリソース内から参照します。 参照されている任意のリソースがそのリソースを要求しよりリソースのコレクション内で以前に定義されていることを確認します。 かどうか、必要に応じて回避できます refererences のリソースの作成の厳密な順序を使用して、 [DynamicResource マークアップ拡張機能](dynamicresource-markup-extension.md)代わりに、実行時にリソースを参照するが、注意する必要がありますをこの DynamicResourceパフォーマンスに影響があります。 詳細については、次を参照してください。 [XAML リソース](xaml-resources.md)します。  
  
 [!code-xaml[FEResource#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResource/CS/default.xaml#xaml)]  
  
## <a name="see-also"></a>関連項目
- [XAML リソース](xaml-resources.md)
- [スタイルとテンプレート](../controls/styling-and-templating.md)
