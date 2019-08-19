---
title: mc:ProcessContent 属性
ms.date: 03/30/2017
helpviewer_keywords:
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: 2689b2c8-b4dc-4b71-b9bd-f95e619122d7
ms.openlocfilehash: bc406659bec3fd8d5da87b597356a3411c7a2605
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567396"
---
# <a name="mcprocesscontent-attribute"></a>mc:ProcessContent 属性
[Mc: Ignorable 属性](mc-ignorable-attribute.md)を指定することが原因で、直接の親要素が[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサによって無視される場合でも、関連する親要素によって処理されるコンテンツを保持する要素を指定します。[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 属性`mc:ProcessContent`は、カスタム名前空間マッピング[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]とバージョン管理の両方で、マークアップ互換性をサポートしています。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...  
  mc:ProcessContent="ignorablePrefix:ThisElementCanBeIgnored"  
>  
    <ignorablePrefix:ThisElementCanBeIgnored>  
        [content]  
    </ignorablePrefix:ThisElementCanBeIgnored>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|*ignorablePrefix*|XML 1.0 仕様に従って、任意の有効なプレフィックス文字列。|  
|*ignorableUri*|XML 1.0 仕様に従って、名前空間を指定するための任意の有効な URI。|  
|*ThisElementCanBeIgnored*|基になる型を解決でき[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ない場合に、プロセッサ実装によって無視される可能性がある要素。|  
|*情報*|*ThisElementCanBeIgnored*は無視としてマークされます。 プロセッサがその要素を無視した場合、 *[content]* は*オブジェクト*によって処理されます。|  
  
## <a name="remarks"></a>Remarks  
 既定では、 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサは無視された要素内のコンテンツを無視します。 によって`mc:ProcessContent` [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]特定の要素を指定することができ、プロセッサは無視された要素内のコンテンツを処理し続けます。 これは通常、コンテンツが複数のタグで入れ子になっている場合に使用されます。少なくとも1つは無視可能で、少なくとも1つは無視可能ではありません。  
  
 属性では、スペース区切り記号 (など`mc:ProcessContent="ignore:Element1 ignore:Element2"`) を使用して、複数のプレフィックスを指定できます。  
  
 名前[!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)]空間は、SDK のこの領域内には記載されていない他の要素と属性を定義します。 詳細については、「 [XML マークアップ互換性の仕様](https://go.microsoft.com/fwlink/?LinkId=73824)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [mc:Ignorable 属性](mc-ignorable-attribute.md)
- [XAML の概要 (WPF)](xaml-overview-wpf.md)
