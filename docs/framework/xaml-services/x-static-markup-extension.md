---
title: x:Static のマークアップ拡張機能
ms.date: 03/30/2017
f1_keywords:
- StaticExtension
- xStatic
- x:Static
helpviewer_keywords:
- x:Static markup extension [XAML Services]
- Static markup extension in XAML [XAML Services]
- XAML [XAML Services], x:Static markup extension
ms.assetid: 056aee79-7cdd-434f-8174-dfc856cad343
ms.openlocfilehash: 3da2f6afc7e7ecf20c91f0badca38bc26083d3ae
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59295711"
---
# <a name="xstatic-markup-extension"></a>x:Static のマークアップ拡張機能
定義されている任意の静的な値をコード エンティティを参照、 [!INCLUDE[TLA#tla_cls](../../../includes/tlasharptla-cls-md.md)]– に準拠した方法。 XAML のプロパティの値を提供する、参照されている静的プロパティを使用できます。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```xaml  
<object property="{x:Static prefix:typeName.staticMemberName}" .../>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
| | |  
|-|-|  
|`prefix`|任意。 割り当てられた、既定以外の XAML 名前空間を参照するプレフィックス。 `prefix` 明示的に使用量のため表示から既定の XAML 名前空間を静的プロパティを参照することはほとんどありません。 「解説」を参照してください。|  
|`typeName`|必須。 必要な静的メンバーを定義する型の名前。|  
|`staticMemberName`|必須。 (定数、静的プロパティ、フィールド、または列挙値) の静的な値が必要なメンバーの名前。|  
  
## <a name="remarks"></a>Remarks  

参照されているコード エンティティは、次のいずれかである必要があります。  
  
-   定数  
-   静的プロパティ  
-   フィールド  
-   列挙値

非静的のプロパティなど、他のコード エンティティを指定すると、XAML がコンパイルされると、マークアップまたは XAML 読み込み時の解析の例外の場合は、コンパイル時エラーとします。  

行うことができます`x:Static`静的フィールドまたは現在の XAML ドキュメントの既定の XAML 名前空間に属さないプロパティへの参照ただし、プレフィックスのマッピングが必要です。 XAML 名前空間は、ほとんどの場合に、XAML ドキュメントのルート要素で定義されます。  

既定の XAML スキーマ コンテキストで実行されている場合、.NET Framework XAML サービスおよびその XAML リーダーと XAML ライターによって静的なプロパティの検索操作を実行できます。 この XAML スキーマ コンテキストでは、CLR リフレクションを使用して、オブジェクト グラフの構築のために必要な静的な値を指定します。 `typeName`を指定する実際には XAML 型名を CLR 型名ではなく、これらは基本的に同じ名前、既定の XAML スキーマ コンテキストを使用する場合、または既存のすべての CLR ベース XAML 実装するフレームワークを使用する場合は。  

行ったと注意して使用`x:Static`直接プロパティの値の型ではない参照をします。 XAML マークアップ拡張機能で指定した値のシーケンス処理を呼び出さないでください追加の値の変換。 これは、true の場合でも、`x:Static`参照は、文字列を作成し、通常のテキスト文字列に基づく属性値の値の変換は、特定のメンバーまたは戻り値の型のメンバー値のいずれかに発生します。  

属性構文は、このマークアップ拡張機能で使用される最も一般的な構文です。 `x:Static` 識別子文字列の後に設定される文字列トークンは、基になる <xref:System.Windows.Markup.StaticExtension.Member%2A> 拡張クラスの <xref:System.Windows.Markup.StaticExtension> 値として割り当てられます。  

技術的に可能なその他の 2 つの XAML 使用法があります。 ただし、これらの使用方法は、不必要に詳細があまり一般的なは。  

1. オブジェクト要素構文です。

    ```xaml
    <x:Static Member="prefix:typeName.staticMemberName" ... />
    ```

2. 初期化文字列の明示的なメンバー プロパティの構文を属性します。

    ```xaml
    <object property="{x:Static Member=prefix:typeName.staticMemberName}" ... />
    ```

このマークアップ拡張機能の処理がによって定義されている、.NET Framework XAML サービス実装、<xref:System.Windows.Markup.StaticExtension>クラス。  

`x:Static` マークアップ拡張機能。 XAML の使用中のすべてのマークアップ拡張機能、`{`と`}`マークアップ拡張機能が値を指定する必要がありますを XAML プロセッサが認識する規則は、それぞれの属性構文内の文字。 マークアップ拡張機能について詳しくは、「 [Markup Extensions for XAML Overview](markup-extensions-for-xaml-overview.md)」をご覧ください。  
  
## <a name="wpf-usage-notes"></a>WPF の使用上の注意  
 WPF プログラミングで使用する既定の XAML 名前空間に多数の便利な静的プロパティが含まれていないと、便利な静的プロパティのほとんどはなどを必要とせず、使用状況を容易にする型コンバーターをサポート`{x:Static}`します。 静的プロパティは、次のいずれかが true の場合、XAML 名前空間のプレフィックスをマップする必要があります。  
  
-   WPF に存在しますが、WPF の既定の XAML 名前空間の一部でない型を参照している ([!INCLUDE[TLA#tla_wpfxmlnsv1](../../../includes/tlasharptla-wpfxmlnsv1-md.md)])。 これは、非常に一般的なシナリオを使用するため`x:Static`します。 たとえば、使用する場合があります、`x:Static`へのマッピングを XAML 名前空間を持つ参照、<xref:System>の静的プロパティを参照するには CLR 名前空間と mscorlib アセンブリ、<xref:System.Environment>クラス。  
  
-   カスタム アセンブリから型を参照しています。  
  
-   その型が既定の WPF XAML 名前空間の一部としてマップされていませんでしたが CLR 名前空間は WPF アセンブリに存在する型を参照しています。 WPF の既定の XAML 名前空間に CLR 名前空間のマッピングは、さまざまな WPF アセンブリ内の定義によって実行されます (この概念の詳細については、次を参照してください。 [XAML 名前空間および WPF XAML の Namespace マッピング](../wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md))。 CLR 名前空間のマッピングされていないがその CLR 名前空間が、通常は想定されていません、XAML などのクラス定義のほとんどの場合で構成される場合に存在できる<xref:System.Windows.Threading>します。  
  
 WPF のプレフィックスと XAML 名前空間を使用する方法の詳細については、次を参照してください。 [XAML 名前空間および WPF XAML のマッピングの Namespace](../wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)します。  
  
## <a name="see-also"></a>関連項目

- [x:Type マークアップ拡張機能](x-type-markup-extension.md)
- [WPF から System.Xaml に移行した型](types-migrated-from-wpf-to-system-xaml.md)
