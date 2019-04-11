---
title: ColorConvertedBitmap のマークアップ拡張機能
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], ColorConvertedBitmap markup extension
- ColorConvertedBitmap markup extension [WPF]
ms.assetid: 18321c18-c898-4470-93fa-a702b47770c1
ms.openlocfilehash: e8a36a1b8592146eb2474805638cdc3697adb0c4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59172940"
---
# <a name="colorconvertedbitmap-markup-extension"></a>ColorConvertedBitmap のマークアップ拡張機能
ビットマップ ソースが埋め込まれたプロファイルを指定する方法を提供します。 色のコンテキスト プロファイルが指定/[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]イメージ ソースとして、[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]します。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```xml  
<object property="{ColorConvertedBitmap imageSource sourceIIC destinationIIC}" .../>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`imageSource`|[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]見積もるビットマップの。|  
|`sourceIIC`|[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]のソース プロファイルの構成。|  
|`destinationIIC`|[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]の移行先のプロファイルの構成|  
  
## <a name="remarks"></a>Remarks  
 このマークアップ拡張機能など、関連する一連のイメージ ソース プロパティの値を入力するものでは<xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>します。  
  
 属性構文は、このマークアップ拡張機能で使用される最も一般的な構文です。 `ColorConvertedBitmap` (または`ColorConvertedBitmapExtension`) 文字列は、最初のコンス トラクターで値として値が設定のみできるため、プロパティ要素構文では使用できません次の拡張機能の識別子。  
  
 `ColorConvertedBitmap` マークアップ拡張機能。 一般にマークアップ拡張機能を実装するのは、属性値をリテラル値やハンドラー名以外にエスケープする要件が存在し、その要件の適用範囲がグローバルで、特定の型やプロパティに型コンバーターを適用するだけにとどまらない場合です。 すべてのマークアップ拡張機能で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を使用して、{および} される規則は、それぞれの属性構文内の文字を[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサを認識するマークアップ拡張機能が、属性を処理する必要があります。 詳細については、次を参照してください。[マークアップ拡張機能と WPF XAML](markup-extensions-and-wpf-xaml.md)します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>
- [マークアップ拡張機能と WPF XAML](markup-extensions-and-wpf-xaml.md)
- [イメージングの概要](../graphics-multimedia/imaging-overview.md)
