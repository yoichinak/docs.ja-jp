---
title: ColorConvertedBitmap のマークアップ拡張機能
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], ColorConvertedBitmap markup extension
- ColorConvertedBitmap markup extension [WPF]
ms.assetid: 18321c18-c898-4470-93fa-a702b47770c1
ms.openlocfilehash: 7d14ddc6276b9dd7baee12e267e8af1250bc11ab
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582776"
---
# <a name="colorconvertedbitmap-markup-extension"></a>ColorConvertedBitmap のマークアップ拡張機能
埋め込みプロファイルを持たないビットマップソースを指定する方法を提供します。 カラーコンテキスト/プロファイルは、イメージソース URI と同様に、URI によって指定されます。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```xml  
<object property="{ColorConvertedBitmap imageSource sourceIIC destinationIIC}" .../>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`imageSource`|プロファイルされていないビットマップの URI。|  
|`sourceIIC`|ソースプロファイル構成の URI。|  
|`destinationIIC`|送信先プロファイルの構成の URI|  
  
## <a name="remarks"></a>Remarks  
 このマークアップ拡張機能は、<xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A> などのイメージソースプロパティ値の関連するセットを埋めることを目的としています。  
  
 属性構文は、このマークアップ拡張機能で使用される最も一般的な構文です。 `ColorConvertedBitmap` (または `ColorConvertedBitmapExtension`) をプロパティ要素の構文で使用することはできません。値を設定できるのは、拡張機能の識別子に続く文字列である初期コンストラクターの値に限られているためです。  
  
 `ColorConvertedBitmap` はマークアップ拡張機能です。 一般にマークアップ拡張機能を実装するのは、属性値をリテラル値やハンドラー名以外にエスケープする要件が存在し、その要件の適用範囲がグローバルで、特定の型やプロパティに型コンバーターを適用するだけにとどまらない場合です。 @No__t_0 内のすべてのマークアップ拡張機能は、属性構文で {および} 文字を使用します。これは、マークアップ拡張機能が属性を処理する必要があることを [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] プロセッサが認識する規則です。 詳細については、「[マークアップ拡張機能」および「WPF XAML](markup-extensions-and-wpf-xaml.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>
- [マークアップ拡張機能と WPF XAML](markup-extensions-and-wpf-xaml.md)
- [イメージングの概要](../graphics-multimedia/imaging-overview.md)
