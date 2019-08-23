---
title: '方法: SystemFonts を使用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- system fonts [WPF]
- fonts [WPF], system fonts
- classes [WPF], SystemFonts
ms.assetid: 3f46a4ec-2225-408a-8123-8838a8f7057a
ms.openlocfilehash: 7438705a82faee464649b5f6f577627a379e9a8c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918364"
---
# <a name="how-to-use-systemfonts"></a>方法: SystemFonts を使用する
この例では、ボタンのスタイル設定やカスタマイズ<xref:System.Windows.SystemFonts>を行うために、クラスの静的リソースを使用する方法を示します。  
  
## <a name="example"></a>例  
 システム リソースは、システム設定と一貫性のあるビジュアルを作成できるようにするために、いくつかのシステムによって決定される値を、リソースおよびプロパティの両方として公開します。 <xref:System.Windows.SystemFonts>は、静的プロパティとしてのシステムフォント値と、実行時にそれらの値に動的にアクセスするために使用できるリソースキーを参照するプロパティの両方を含むクラスです。 たとえば、 <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> <xref:System.Windows.SystemFonts>は値<xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>であり、は対応するリソースキーです。  
  
 で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]は、のメンバーを静的プロパティ<xref:System.Windows.SystemFonts>または動的リソース参照 (キーとして静的なプロパティ値として使用) のいずれかとして使用できます。 アプリケーションの実行時にフォント メトリックを自動的に更新する場合は、動的リソース参照を使用します。それ以外の場合は、静的な値参照を使用します。  
  
> [!NOTE]
> リソース キーでは、プロパティ名に"Key"というサフィックスが付いています。  
  
 次の例は、ボタンのスタイル設定やカスタマイズを<xref:System.Windows.SystemFonts>行うために、のプロパティを静的な値として使用する方法を示しています。 このマークアップの<xref:System.Windows.SystemFonts>例では、ボタンに値を割り当てます。  
  
 [!code-xaml[SystemRes_snip#FontStaticResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#fontstaticresources)]  
  
 コードでの<xref:System.Windows.SystemFonts>値を使用するには、静的な値または動的リソース参照を使用する必要はありません。 代わりに、 <xref:System.Windows.SystemFonts>クラスの非キープロパティを使用します。 キー以外のプロパティは静的なプロパティとして定義されていますが[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 、システムによってホストされるの実行時の動作では、プロパティがリアルタイムで再評価され、ユーザーによるシステム値の変更が適切に考慮されます。 次の例では、ボタンのフォント設定を指定する方法を示します。  
  
 [!code-csharp[SystemRes_snip#FontResourcesCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#fontresourcescode)]
 [!code-vb[SystemRes_snip#FontResourcesCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#fontresourcescode)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.SystemFonts>
- [システム ブラシで領域を塗りつぶす](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [SystemParameters を使用する](how-to-use-systemparameters.md)
- [システム フォント キーを使用する](how-to-use-system-fonts-keys.md)
- [方法トピック](resources-how-to-topics.md)
- [x:Static のマークアップ拡張機能](../../xaml-services/x-static-markup-extension.md)
- [XAML リソース](xaml-resources.md)
- [DynamicResource マークアップ拡張](dynamicresource-markup-extension.md)
