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
ms.openlocfilehash: bf94f1d61ee3080c9d3582e55e0695b269801c80
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2019
ms.locfileid: "73733360"
---
# <a name="xstatic-markup-extension"></a>x:Static のマークアップ拡張機能
共通言語仕様 (CLS: Common Language Specification) に準拠した方法で定義されている静的な値渡しのコードエンティティを参照します。 参照される静的プロパティは、XAML でプロパティの値を指定するために使用できます。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```xaml  
<object property="{x:Static prefix:typeName.staticMemberName}" .../>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
| | |  
|-|-|  
|`prefix`|省略可能です。 既定以外のマップされた XAML 名前空間を参照するプレフィックス。 既定の XAML 名前空間からの静的なプロパティを参照することはほとんどないため、`prefix` は明示的に使用されます。 「解説」を参照してください。|  
|`typeName`|必須です。 目的の静的メンバーを定義する型の名前。|  
|`staticMemberName`|必須です。 目的の静的な値のメンバーの名前 (定数、静的プロパティ、フィールド、または列挙値)。|  
  
## <a name="remarks"></a>Remarks  

参照されるコードエンティティは、次のいずれかである必要があります。  
  
- 定数  
- 静的プロパティ  
- フィールド  
- 列挙値

非静的プロパティなどの他のコードエンティティを指定すると、XAML がマークアップコンパイルされた場合、または XAML 読み込み時の解析例外が発生した場合に、コンパイル時エラーが発生します。  

現在の XAML ドキュメントの既定の XAML 名前空間に含まれていない静的フィールドまたは静的プロパティへの `x:Static` 参照を作成できます。ただし、これにはプレフィックスマッピングが必要です。 XAML 名前空間は、ほとんどの場合、XAML ドキュメントのルート要素で定義されます。  

静的プロパティの参照操作は、既定の XAML スキーマコンテキストを使用して実行されている場合に、xaml サービスとその XAML リーダーおよび XAML ライター .NET Framework によって実行できます。 この XAML スキーマコンテキストは、CLR リフレクションを使用して、オブジェクトグラフの構築に必要な静的な値を提供できます。 指定する `typeName` は実際には CLR 型名ではなく XAML 型名ですが、既定の XAML スキーマコンテキストを使用する場合、または既存の CLR ベースの XAML を実装するすべてのフレームワークを使用する場合は、基本的に同じ名前になります。  

プロパティの値の型ではなく、直接 `x:Static` 参照を作成する場合は注意してください。 XAML 処理シーケンスでは、マークアップ拡張機能から指定された値は、追加の値変換を呼び出しません。 これは、`x:Static` 参照によってテキスト文字列が作成され、テキスト文字列に基づく属性値の値変換が、通常、その特定のメンバーまたは戻り値の型のメンバー値に対して行われる場合にも当てはまります。  

属性構文は、このマークアップ拡張機能で使用される最も一般的な構文です。 `x:Static` 識別子文字列の後に設定される文字列トークンは、基になる <xref:System.Windows.Markup.StaticExtension.Member%2A> 拡張クラスの <xref:System.Windows.Markup.StaticExtension> 値として割り当てられます。  

他にも、技術的には可能な XAML の使用方法が2つあります。 ただし、これらの使用方法は、不必要に冗長であるため、あまり一般的ではありません。  

1. オブジェクト要素の構文。

    ```xaml
    <x:Static Member="prefix:typeName.staticMemberName" ... />
    ```

2. 初期化文字列の明示的なメンバープロパティを持つ属性構文。

    ```xaml
    <object property="{x:Static Member=prefix:typeName.staticMemberName}" ... />
    ```

.NET Framework XAML サービスの実装では、このマークアップ拡張機能の処理は <xref:System.Windows.Markup.StaticExtension> クラスによって定義されます。  

`x:Static` はマークアップ拡張機能です。 XAML のすべてのマークアップ拡張は、属性構文で `{` と `}` 文字を使用します。これは、マークアップ拡張機能が値を提供する必要があることを XAML プロセッサが認識する規則です。 マークアップ拡張機能について詳しくは、「 [Markup Extensions for XAML Overview](markup-extensions-for-xaml-overview.md)」をご覧ください。  
  
## <a name="wpf-usage-notes"></a>WPF の使用上の注意  
 WPF プログラミングに使用する既定の XAML 名前空間には、多くの便利な静的プロパティが含まれていません。便利な静的プロパティのほとんどは、`{x:Static}` を必要とせずに使用を容易にする型コンバーターなどのサポートがあります。 静的プロパティの場合、次のいずれかに該当する場合は、XAML 名前空間のプレフィックスをマップする必要があります。  
  
- WPF に存在する型を参照していますが、WPF (`http://schemas.microsoft.com/winfx/2006/xaml/presentation`) の既定の XAML 名前空間に含まれていません。 これは、`x:Static`を使用するための非常に一般的なシナリオです。 たとえば、<xref:System.Environment> クラスの静的プロパティを参照するために、<xref:System> CLR 名前空間と mscorlib アセンブリに対する XAML 名前空間のマッピングを含む `x:Static` 参照を使用できます。  
  
- カスタムアセンブリから型を参照している。  
  
- WPF アセンブリに存在する型を参照していますが、その型は、WPF の既定の XAML 名前空間の一部としてマップされていない CLR 名前空間内にあります。 WPF の既定の XAML 名前空間への CLR 名前空間のマッピングは、さまざまな WPF アセンブリの定義によって実行されます (この概念の詳細については、「 [WPF xaml の Xaml 名前空間と名前空間のマッピング](../wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)」を参照してください)。 マップされていない CLR 名前空間は、CLR 名前空間が主に XAML 用ではないクラス定義 (<xref:System.Windows.Threading>など) で構成されている場合に存在する可能性があります。  
  
 WPF でプレフィックスと XAML 名前空間を使用する方法の詳細については、「 [WPF xaml の Xaml 名前空間と名前空間のマッピング](../wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [x:Type マークアップ拡張機能](x-type-markup-extension.md)
- [WPF から System.Xaml に移行した型](types-migrated-from-wpf-to-system-xaml.md)
