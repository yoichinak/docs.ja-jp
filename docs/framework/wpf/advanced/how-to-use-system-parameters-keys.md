---
title: '方法: システム パラメーター キーを使用する'
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemParameters class
- classes [WPF], SystemParameters
ms.assetid: 77571283-d16c-45bb-9f69-cafbbf72b21e
ms.openlocfilehash: 147f65b4bb214c12317309081c345251d7426cd6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59147336"
---
# <a name="how-to-use-system-parameters-keys"></a>方法: システム パラメーター キーを使用する
システム リソースは、開発者がシステム設定と一貫性のあるビジュアルを作成できるようにするために、多くのシステム メトリックをリソースとして公開します。 <xref:System.Windows.SystemParameters> システム パラメーターの値と値にバインドされるリソース キーの両方を含むクラスは、— たとえば、<xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A>と<xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>します。 システム パラメーター メトリックは、静的なリソースとしても、動的なリソースとしても使用できます。 アプリケーションの実行時にパラメーター メトリックを自動的に更新する場合は、動的リソースを使用します。それ以外の場合は、静的リソースを使用します。  
  
> [!NOTE]
>  動的リソースにキーワードを指定する*キー*プロパティ名に追加されます。  
  
 次の例では、ボタンのスタイル設定やカスタマイズを行うために、システム パラメーター動的リソースにアクセスして使用する方法を示します。 これは、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]例ボタンのサイズを割り当てることで<xref:System.Windows.SystemParameters>ボタンの幅と高さの値。  
  
## <a name="example"></a>例  
 [!code-xaml[SystemRes_snip#ParameterDynamicResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#parameterdynamicresources)]  
  
## <a name="see-also"></a>関連項目

- [システム ブラシで領域を塗りつぶす](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [SystemFonts を使用する](how-to-use-systemfonts.md)
- [SystemParameters を使用する](how-to-use-systemparameters.md)
