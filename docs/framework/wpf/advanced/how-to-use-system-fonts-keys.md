---
title: '方法: システム フォント キーを使用する'
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemFonts class
ms.assetid: 036ebea7-5677-4f60-8ba4-56c9f9d9b8bd
ms.openlocfilehash: 7283e4225b75909322fa312583e9f1a0679762e2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918382"
---
# <a name="how-to-use-system-fonts-keys"></a>方法: システム フォント キーを使用する
システム リソースは、開発者がシステム設定と一貫性のあるビジュアルを作成できるようにするために、多くのシステム メトリックをリソースとして公開します。 <xref:System.Windows.SystemFonts>は、システムフォント値と、値にバインドされるシステムフォントリソース (や<xref:System.Windows.SystemFonts.CaptionFontFamily%2A> <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>など) の両方を含むクラスです。  
  
 システム フォント メトリックは、静的なリソースとしても、動的なリソースとしても使用できます。 アプリケーションの実行時にフォント メトリックを自動的に更新する場合は、動的リソースを使用します。それ以外の場合は、静的リソースを使用します。  
  
> [!NOTE]
> 動的リソースには、プロパティ名にキーワード*Key*が付加されています。  
  
 次の例では、システム フォント動的リソースにアクセスして使用し、ボタンのスタイル設定またはカスタマイズを行う方法を示します。 この[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]例では、ボタンに値<xref:System.Windows.SystemFonts>を割り当てるボタンスタイルを作成します。  
  
## <a name="example"></a>例  
 [!code-xaml[SystemRes_snip#FontDynamicResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#fontdynamicresources)]  
  
## <a name="see-also"></a>関連項目

- [システム ブラシで領域を塗りつぶす](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [SystemParameters を使用する](how-to-use-systemparameters.md)
- [SystemFonts を使用する](how-to-use-systemfonts.md)
