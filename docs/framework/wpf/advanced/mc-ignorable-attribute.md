---
title: mc:Ignorable 属性
ms.date: 03/30/2017
helpviewer_keywords:
- mc XML namespace prefix [WPF]
- mc:Ignorable attribute
- XML [WPF], mc namespace prefix
- XAML [WPF], mc:Ignorable attribute
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: acd9a6ef-b7ca-4146-abb6-60f3b366e9ec
ms.openlocfilehash: 03439a2c4a1a4de375e90d0e5121e690541e2f0f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61805146"
---
# <a name="mcignorable-attribute"></a>mc:Ignorable 属性
指定します[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]マークアップ ファイルで発生した名前空間プレフィックスを無視できます、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサ。 `mc:Ignorable`属性は、カスタムの名前空間のマッピングとのマークアップの互換性をサポートしている[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]バージョン管理します。  
  
## <a name="xaml-attribute-usage-single-prefix"></a>XAML 属性使用量 (1 つのプレフィックス)  
  
```  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-attribute-usage-two-prefixes"></a>XAML 属性の使用方法 (2 つのプレフィックス)  
  
```  
<object  
  xmlns:ignorablePrefix1="ignorableUri"  
  xmlns:ignorablePrefix2="ignorableUri2"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix1 ignorablePrefix2"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|*ignorablePrefix、ignorablePrefix1 など。*|有効なプレフィックスは、任意の文字列、XML 1.0 仕様に準拠します。|  
|*ignorableUri*|XML 1.0 仕様の名前空間を指定する有効な URI です。|  
|*ThisElementCanBeIgnored*|要素を無視できる[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]プロセッサの実装を基になる型を解決できない場合。|  
  
## <a name="remarks"></a>Remarks  
 `mc` [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]名前空間プレフィックスは、マッピング時に使用する推奨されるプレフィックス規則、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]互換性名前空間[!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)]します。  
  
 要素または属性として、要素名のプレフィックス部分を識別する、`mc:Ignorable`によって処理されるときにエラーが発生しません、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサ。 その属性を基になる型またはプログラミング コンストラクトに解決できませんでした、その要素は無視されます。 ただし無視された要素が処理されていない、その要素の副作用である追加の要素の要件の追加の解析エラーを生成可能性がありますもに注意してください。 たとえば、特定の要素のコンテンツ モデルがときに指定された子要素が、ただ 1 つの子要素を必要があります、`mc:Ignorable`プレフィックス、および指定された子要素は、型に解決できませんでした、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサ可能性がありますエラーが発生します。  
  
 `mc:Ignorable` 識別子の文字列に名前空間のマッピングにのみ適用されます。 `mc:Ignorable` 名前空間のマッピングにアセンブリを指定するには適用されませんを[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]名前空間とアセンブリ (または、アセンブリと実行可能ファイルの現在の既定値)。  
  
 実装する場合、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサ、プロセッサの実装する必要がありますいないを発生させる解析や処理の任意の要素または属性として識別されるプレフィックスで修飾されている型の解決でエラー`mc:Ignorable`します。 プロセッサの実装セカンダリ要素の前に示した例では、1 つの子要素など、処理をロードまたは失敗の結果である例外が発生することができます。  
  
 既定で、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサは、無視された要素内のコンテンツを無視します。 ただし、追加の属性を指定できます[mc:ProcessContent 属性](mc-processcontent-attribute.md)、[次へ] の使用可能な親要素によって無視された要素内のコンテンツの継続処理を要求します。  
  
 たとえば、区切り記号として 1 つ以上の空白文字を使用して、属性で複数のプレフィックスを指定できます:`mc:Ignorable="ignore1 ignore2"`します。  

 [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)]名前空間は、他の要素とのこの領域内に記載されていない属性を定義、[!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)]します。 詳細については、次を参照してください。 [XML マークアップ互換性仕様](/office/open-xml/introduction-to-markup-compatibility#markup-compatibility-in-the-open-xml-file-formats-specification)します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Markup.XamlReader>
- [PresentationOptions:Freeze 属性](presentationoptions-freeze-attribute.md)
- [XAML の概要 (WPF)](xaml-overview-wpf.md)
- [WPF のドキュメント](documents-in-wpf.md)
