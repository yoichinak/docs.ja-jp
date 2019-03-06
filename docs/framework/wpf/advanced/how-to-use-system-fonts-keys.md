---
title: '方法: システム フォント キーを使用する'
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemFonts class
ms.assetid: 036ebea7-5677-4f60-8ba4-56c9f9d9b8bd
ms.openlocfilehash: 8d354bb598da6912bfa34f611cb55d4dcd7920a5
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352842"
---
# <a name="how-to-use-system-fonts-keys"></a>方法: システム フォント キーを使用する
システム リソースは、開発者がシステム設定と一貫性のあるビジュアルを作成できるようにするために、多くのシステム メトリックをリソースとして公開します。 <xref:System.Windows.SystemFonts> システム フォント値と値にバインドされるシステム フォント リソースの両方を含むクラスは、— たとえば、<xref:System.Windows.SystemFonts.CaptionFontFamily%2A>と<xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>します。  
  
 システム フォント メトリックは、静的なリソースとしても、動的なリソースとしても使用できます。 アプリケーションの実行時にフォント メトリックを自動的に更新する場合は、動的リソースを使用します。それ以外の場合は、静的リソースを使用します。  
  
> [!NOTE]
>  動的リソースにキーワードを指定する*キー*プロパティ名に追加されます。  
  
 次の例では、システム フォント動的リソースにアクセスして使用し、ボタンのスタイル設定またはカスタマイズを行う方法を示します。 これは、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を割り当てるボタン スタイルを作成する例<xref:System.Windows.SystemFonts>をボタンの値。  
  
## <a name="example"></a>例  
 [!code-xaml[SystemRes_snip#FontDynamicResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#fontdynamicresources)]  
  
## <a name="see-also"></a>関連項目
- [システム ブラシで領域を塗りつぶす](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [SystemParameters を使用する](how-to-use-systemparameters.md)
- [SystemFonts を使用する](how-to-use-systemfonts.md)
