---
title: XAML 2009 言語機能
ms.date: 03/30/2017
helpviewer_keywords:
- XAML 2009 [XAML Services]
- XAML [XAML Services], XAML 2009
ms.assetid: f6bb18d8-c86a-4549-8862-323e6b32a8dd
ms.openlocfilehash: 05f811cd0d95f7605963dae851430fb6bf0e9f7a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59162281"
---
# <a name="xaml-2009-language-features"></a>XAML 2009 言語機能
XAML 2009 とは、既存の XAML 言語仕様を拡張した、XAML の新しい言語機能の短縮名です。 XAML 2009 には、いくつかの新しいディレクティブとコンストラクトが導入されています。 含まれます、 [X:arguments ディレクティブ](x-arguments-directive.md)、 [X:factorymethod ディレクティブ](x-factorymethod-directive.md)、 [X:reference マークアップ拡張機能](x-reference-markup-extension.md)、 [X:typearguments ディレクティブ](x-typearguments-directive.md); 共通言語プリミティブの組み込み型 (たとえば`x:Char`)。  
  
<a name="xaml_2009_support_in_wpf_and_visual_studio"></a>   
## <a name="xaml-2009-support-in-wpf-and-visual-studio"></a>XAML 2009 は、WPF および Visual Studio でサポートされています。  
 WPF では XAML 2009 の機能を使用できますが、WPF マークアップ コンパイルされていない XAML に限定されます。 マークアップ コンパイルされた XAML、および XAML の BAML 形式は、現在、XAML 2009 言語のキーワードと機能をサポートしていません。  
  
 なお、WPF に Loose XAML を読み込むための既存の方法には、CLR 型および型システムに対するセキュリティ制限およびアクセス制限が課されていることがあります。この制限は、マークアップ コンパイルされた XAML に対する制限よりも限定的です。 詳細については、「 [セキュリティ (WPF)](../wpf/security-wpf.md) 」または「 [WPF のセキュリティ方針 - プラットフォーム セキュリティ](../wpf/wpf-security-strategy-platform-security.md)」を参照してください。  
  
 また、XAML 2009 では、以前の XAML 2006 構造を変更するか、または基本的なマークアップ形式を変更する、追加機能も導入されました。  
  
### <a name="xkey-as-an-object-element"></a>オブジェクトの要素としての x:Key  
 XAML 2009 では `x:Key` をオブジェクト (オブジェクト要素値を持つプロパティ要素) としてサポートできます。XAML 2006 では、 `x:Key` は属性としてのみサポートされていました。 「 [x:Key Directive](x-key-directive.md)」の「XAML 2009」のセクションを参照してください。  
  
### <a name="xmlns-on-property-elements"></a>プロパティ要素の xmlns  
 XAML 2009 は、プロパティ要素に対する XAML 名前空間 (xmlns) の定義をサポートできます。XAML 2006 では、オブジェクト要素に対してのみ xmlns 定義をサポートしていました。  
  
### <a name="event-attributes"></a>イベント属性  
 イベントによってサポートされる属性については、XAML 2006 ではマークアップ コンパイルが関係していると仮定されて、イベントはマークアップ コンパイルに送信されます。 XAML 2009 はマークアップ拡張機能に似たマークアップ形式をサポートします。このマークアップ形式は、XAML のランタイム解析と読み込みが行われるまでイベント接続を遅延します。 ただし、WPF アプリケーション、および WPF の UI の XAML シナリオでは、一般にこの機能は使用しません。 WPF およびその XAML 2006 の実装では、イベント属性処理の大部分に対し、 <xref:System.Windows.UIElement> レベルで定義されたルーティング イベントのイベント ハンドラー接続と、そのマークアップ コンパイラ手順の組み合わせを使用します。 マークアップ コンパイラは、XAML 内に見つかるすべてのイベント属性を事前に処理し、マークアップ コンパイラが使用されることがビルド アクションによって宣言されます。  
  
## <a name="see-also"></a>関連項目

- [XAML の概要 (WPF)](../wpf/advanced/xaml-overview-wpf.md)
