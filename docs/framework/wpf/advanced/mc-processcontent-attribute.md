---
title: mc:ProcessContent 属性
ms.date: 03/30/2017
helpviewer_keywords:
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: 2689b2c8-b4dc-4b71-b9bd-f95e619122d7
ms.openlocfilehash: 865b1a3ccc30ff5efab4b08956bf7ba2bba4769c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110587"
---
# <a name="mcprocesscontent-attribute"></a>mc:ProcessContent 属性
指定します[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]要素もコンテンツがある、関連する親要素によって処理によって直接の親要素が無視される場合でも、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を指定するためのプロセッサ[mc: Ignorable 属性](mc-ignorable-attribute.md). `mc:ProcessContent`属性は、カスタムの名前空間のマッピングとのマークアップの互換性をサポートしている[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]バージョン管理します。  
  
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
|*ignorablePrefix*|有効なプレフィックスは、任意の文字列、XML 1.0 仕様に準拠します。|  
|*ignorableUri*|XML 1.0 仕様の名前空間を指定する有効な URI です。|  
|*ThisElementCanBeIgnored*|要素を無視できる[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]プロセッサの実装を基になる型を解決できない場合。|  
|*[コンテンツ]*|*ThisElementCanBeIgnored* ignorable にマークされます。 プロセッサが、その要素を無視する場合は *[コンテンツ]* によって処理される*オブジェクト*します。|  
  
## <a name="remarks"></a>Remarks  
 既定で、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサは、無視された要素内のコンテンツを無視します。 特定の要素を指定する`mc:ProcessContent`、および[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサが無視された要素内のコンテンツの処理を続行します。 これは通常、使用、コンテンツがうち少なくとも 1 つは無視でき、うち少なくとも 1 つは無視のいくつかのタグ内で入れ子になった場合。  
  
 たとえば、領域の区切り記号を使用して、属性で複数のプレフィックスを指定する場合があります:`mc:ProcessContent="ignore:Element1 ignore:Element2"`します。  
  
 [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)]名前空間は、他の要素とのこの領域内に記載されていない属性を定義、[!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)]します。 詳細については、次を参照してください。 [XML マークアップ互換性仕様](https://go.microsoft.com/fwlink/?LinkId=73824)します。  
  
## <a name="see-also"></a>関連項目

- [mc:Ignorable 属性](mc-ignorable-attribute.md)
- [XAML の概要 (WPF)](xaml-overview-wpf.md)
