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
ms.openlocfilehash: b68909d94ad8cc5bba75b2c520db82c5ccf1b922
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/31/2019
ms.locfileid: "70206182"
---
# <a name="mcignorable-attribute"></a>mc:Ignorable 属性
マークアップファイルで検出された[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 名前空間プレフィックスがプロセッサによって無視される可能性があるかどうかを指定します。[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 属性`mc:Ignorable`は、カスタム名前空間マッピング[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]とバージョン管理の両方で、マークアップ互換性をサポートしています。  
  
## <a name="xaml-attribute-usage-single-prefix"></a>XAML 属性の使用法 (単一のプレフィックス)  
  
```  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-attribute-usage-two-prefixes"></a>XAML 属性の使用法 (2 つのプレフィックス)  
  
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
|*ignorablePrefix、ignorablePrefix1、その他*|XML 1.0 仕様に従って、任意の有効なプレフィックス文字列。|  
|*ignorableUri*|XML 1.0 仕様に従って、名前空間を指定するための任意の有効な URI。|  
|*ThisElementCanBeIgnored*|基になる型を解決でき[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ない場合に、プロセッサ実装によって無視される可能性がある要素。|  
  
## <a name="remarks"></a>Remarks  
 名前空間プレフィックスは、互換性名前空間`http://schemas.openxmlformats.org/markup-compatibility/2006`を[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]マップするときに使用する推奨プレフィックス表記規則です。 `mc` [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]  
  
 要素名のプレフィックス部分がとして`mc:Ignorable`識別される要素または属性は、 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサによる処理時にエラーを発生させません。 その属性を基になる型またはプログラミング構成体に解決できなかった場合、その要素は無視されます。 ただし、無視された要素では、その要素が処理されないという副作用を伴う追加の要素の要件に対して、追加の解析エラーが発生する可能性があります。 たとえば、特定の要素のコンテンツモデルでは、1つの子要素だけが必要になる場合があり`mc:Ignorable`ますが、指定された子要素がプレフィックスに含まれていて[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 、指定された子要素が型に解決されない場合、プロセッサは次のようになります。エラーを発生させます。  
  
 `mc:Ignorable`識別子文字列への名前空間マッピングにのみ適用されます。 `mc:Ignorable`アセンブリへの名前空間マッピングには適用されません。アセンブリは、CLR 名前空間とアセンブリを指定します (または、現在の実行可能ファイルをアセンブリとして既定値として指定します)。  
  
 プロセッサを[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]実装する場合、として識別されるプレフィックスによって修飾されている要素または属性の型解決では、プロセッサ実装で解析`mc:Ignorable`または処理エラーが発生しないようにする必要があります。 しかし、プロセッサの実装では、前に示した1つの子要素の例のように、要素の読み込みまたは処理に失敗した場合の二次的な結果である例外が発生する可能性があります。  
  
 既定では、 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサは無視された要素内のコンテンツを無視します。 ただし、追加の属性である[mc: ProcessContent 属性](mc-processcontent-attribute.md)を指定して、次に使用可能な親要素によって無視された要素内のコンテンツを継続して処理する必要があります。  
  
 属性では、1つ以上の空白文字を区切り記号として使用することで、複数のプレフィックス`mc:Ignorable="ignore1 ignore2"`を指定できます。たとえば、のようになります。  

 名前`http://schemas.openxmlformats.org/markup-compatibility/2006`空間は、SDK のこの領域内には記載されていない他の要素と属性を定義します。 詳細については、「 [XML マークアップ互換性の仕様](/office/open-xml/introduction-to-markup-compatibility#markup-compatibility-in-the-open-xml-file-formats-specification)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Markup.XamlReader>
- [PresentationOptions:Freeze 属性](presentationoptions-freeze-attribute.md)
- [XAML の概要 (WPF)](xaml-overview-wpf.md)
- [WPF のドキュメント](documents-in-wpf.md)
