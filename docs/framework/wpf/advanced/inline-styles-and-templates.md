---
title: "インライン スタイルおよびテンプレート"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- inline templates [WPF]
- styles [WPF], inline
- templates [WPF], inline
- inline styles [WPF]
ms.assetid: 69a1a3f9-acb5-4e2c-9c43-2e376c055ac4
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5dccf0b274121ff4fe88c9270119a2f631ffcf29
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="inline-styles-and-templates"></a>インライン スタイルおよびテンプレート
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]提供<xref:System.Windows.Style>オブジェクトとテンプレートのオブジェクト (<xref:System.Windows.FrameworkTemplate>サブクラス)、リソースで要素の外観を定義する手段として使用できるように複数回です。 このため、属性で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]型を受け取る<xref:System.Windows.Style>と<xref:System.Windows.FrameworkTemplate>新しいものをインラインで定義するのではなく、ほとんどの場合の既存のスタイルとテンプレートにリソース参照を作成します。  
  
## <a name="limitations-of-inline-styles-and-templates"></a>インライン スタイルとテンプレートの制限事項  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]スタイルとテンプレートのプロパティは、2 つの方法のいずれかで技術的に設定できます。 たとえば、リソース内で定義されたスタイルを参照する属性の構文を使用できます`<`*オブジェクト*`Style="{StaticResource`*myResourceKey*`}" .../>`です。 または、スタイルをインラインのインスタンスを定義するプロパティ要素構文を使用することができます。  
  
 `<`*object*`>`  
  
 `<`*object*`.Style>`  
  
 `<` `Style`  `.../>`  
  
 `</`*object*`.Style>`  
  
 `</`*object*`>`  
  
 属性の使用方法は、はるかに一般的です。 インラインで定義され、リソースではない定義でスタイルを含む要素のみを対象とするとは限りません、再使用できませんように簡単にリソース キーがあるないためです。 一般にリソース定義のスタイル汎用性と、有用であり、一般的な高く[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]プログラミング モデルの方針のマークアップでのデザイン コードでのプログラム ロジックを分離することです。  
  
 通常必要はありませんスタイルまたはテンプレートのインラインを設定する場合でも、その場所にそのスタイルまたはテンプレートを使用するだけです。 スタイルまたはテンプレートが実行できるほとんどの要素は、コンテンツのプロパティとコンテンツ モデルもサポートします。 論理ツリーをのみを使用している場合は、1 回スタイルまたはテンプレートで作成するは、さらに簡単に直接的なマークアップでの同等の子要素のコンテンツ プロパティを塗りつぶします。 これは、バイパス スタイルとテンプレート メカニズム完全します。  
  
 オブジェクトを返すマークアップ拡張機能を有効になっている他の構文もスタイルとテンプレートの考えられます。 可能なシナリオがあるこのような 2 つの拡張機能を含める[TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md)と<xref:System.Windows.Data.Binding>です。  
  
## <a name="see-also"></a>参照  
 [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)
