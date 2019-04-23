---
title: インライン スタイルおよびテンプレート
ms.date: 03/30/2017
helpviewer_keywords:
- inline templates [WPF]
- styles [WPF], inline
- templates [WPF], inline
- inline styles [WPF]
ms.assetid: 69a1a3f9-acb5-4e2c-9c43-2e376c055ac4
ms.openlocfilehash: b566e157e2d4a9e9be21a678541bf5d5341a898c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59091435"
---
# <a name="inline-styles-and-templates"></a>インライン スタイルおよびテンプレート
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供<xref:System.Windows.Style>オブジェクトおよびオブジェクトのテンプレート (<xref:System.Windows.FrameworkTemplate>サブクラス) リソース内の要素の視覚的な外観を定義する方法、として使用できるように複数回です。 このため、属性[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]型を受け取る<xref:System.Windows.Style>と<xref:System.Windows.FrameworkTemplate>インライン新しいものを定義するのではなく、ほとんどの場合に既存のスタイルとテンプレートにリソース参照を作成します。  
  
## <a name="limitations-of-inline-styles-and-templates"></a>インライン スタイルおよびテンプレートの制限事項  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]スタイルとテンプレートのプロパティは、2 つの方法のいずれかで技術的には設定できます。 たとえば、リソース内で定義されたスタイルを参照する属性の構文を使用できます`<`*オブジェクト*`Style="{StaticResource`*myResourceKey*`}" .../>`します。 または、インスタンスのスタイルをインラインを定義するプロパティ要素構文を使用することができます。  
  
 `<` *object* `>`  
  
 `<` *object* `.Style>`  
  
 `<` `Style`  `.../>`  
  
 `</` *object* `.Style>`  
  
 `</` *object* `>`  
  
 属性の使用法が一般的です。 スタイルはインラインで定義で定義されていないリソースにのみ、含まれる要素のスコープは必ずしも、再使用できませんに簡単にリソース キーがあるないためです。 リソースによって定義されたスタイルの汎用性と有用では、一般とが高く、一般的な[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]モデルのコードでのプログラム ロジックを分離する、マークアップでのデザイン原則をプログラミングします。  
  
 通常は、スタイルまたはテンプレートのインラインを設定する理由の場所にそのスタイルまたはテンプレートを使用する場合でも、 スタイルまたはテンプレートが実行できるほとんどの要素では、コンテンツのプロパティとコンテンツ モデルもサポートします。 論理ツリーをのみを使用している場合は、スタイルまたはテンプレートで 1 回作成する、だけコンテンツ プロパティを直接マークアップで同等の子要素を格納するより簡単になります。 これは、バイパス、スタイルとテンプレート メカニズム完全します。  
  
 オブジェクトを返すマークアップ拡張機能によって有効になっているその他の構文は、スタイルとテンプレートのこともできます。 考えられるシナリオがある場合、このような 2 つの拡張子を含める[TemplateBinding](templatebinding-markup-extension.md)と<xref:System.Windows.Data.Binding>します。  
  
## <a name="see-also"></a>関連項目

- [スタイルとテンプレート](../controls/styling-and-templating.md)
