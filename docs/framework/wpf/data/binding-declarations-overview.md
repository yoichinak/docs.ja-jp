---
title: バインディング宣言の概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- markup extensions [WPF]
- data binding [WPF], declarations
- object element syntax [WPF]
- binding data [WPF], declarations
- syntax [WPF], object elements
- binding declarations [WPF]
ms.assetid: b97fd626-4c0d-4761-872a-2bca5820da2c
ms.openlocfilehash: c0fcbc8054272356c39ba7925041ecef05a0322c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59165270"
---
# <a name="binding-declarations-overview"></a>バインディング宣言の概要
このトピックでは、バインディングを宣言するさまざまな方法について説明します。  

<a name="Prereq"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックを読む前に、マークアップ拡張機能の概念と使用方法について理解している必要があります。 マークアップ拡張機能の詳細については、 「[マークアップ拡張機能と WPF XAML](../advanced/markup-extensions-and-wpf-xaml.md)」を参照してください。  
  
 このトピックでは、データ バインディングの概念については説明しません。 データ バインディングの概念の詳細については、「[Data Binding Overview](data-binding-overview.md)」を参照してください。  
  
<a name="BindinginXAML"></a>   
## <a name="declaring-a-binding-in-xaml"></a>XAML でのバインディングの宣言  
 このセクションでは、XAML でバインディングを宣言する方法について説明します。  
  
<a name="MarkupExtensionSyntax"></a>   
### <a name="markup-extension-usage"></a>マークアップ拡張機能の使用方法  
 <xref:System.Windows.Data.Binding> はマークアップ拡張機能です。 バインディング拡張機能を使用してバインディングを宣言するとき、この宣言は、`Binding` キーワードに続く一連の句で構成され、コンマ (,) で区切られます。 バインディング宣言内の句の順序は任意で、多数の組み合わせが可能です。 句は*名前*=*値*ペアで*名前*の名前を指定します、<xref:System.Windows.Data.Binding>プロパティと*値*はプロパティを設定する値。  
  
 マークアップでバインディング宣言文字列を作成する場合、この文字列はターゲット オブジェクトの特定の依存関係プロパティにアタッチする必要があります。 次の例では、バインドする方法を示しています、<xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>バインド拡張機能を使用して、指定するプロパティ、<xref:System.Windows.Data.Binding.Source%2A>と<xref:System.Windows.Data.Binding.Path%2A>プロパティ。  
  
 [!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#L37-L37)]  
  
 ほとんどのプロパティを指定することができます、<xref:System.Windows.Data.Binding>クラスのこのようにします。 バインディング拡張は、の一覧の場合と同様の詳細については<xref:System.Windows.Data.Binding>バインド拡張機能を使用して設定できないプロパティを参照してください、[バインディング マークアップ拡張](../advanced/binding-markup-extension.md)の概要。  
  
<a name="ObjectElementSyntax"></a>   
### <a name="object-element-syntax"></a>オブジェクト要素構文  
 オブジェクト要素構文は、バインディング宣言を作成する代替の方法です。 ほとんどの場合は、マークアップ拡張機能の使用とオブジェクト要素構文の使用のどちらにも特別な利点はありません。 ただし、マークアップ拡張機能がサポートしないシナリオでは (プロパティ値が文字列タイプではなく、このタイプの変換が存在しない場合)、オブジェクト要素構文を使用する必要があります。  
  
 オブジェクト要素構文とマークアップ拡張機能の使用の両方の例を次に示します。  
  
 [!code-xaml[BindConversionMarkup#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindConversionMarkup/CSharp/Page1.xaml#1)]  
  
 例では、バインド、<xref:System.Windows.Controls.TextBlock.Foreground%2A>拡張構文を使用してバインディングを宣言することでプロパティ。 バインディング宣言、<xref:System.Windows.Controls.TextBlock.Text%2A>プロパティは、オブジェクト要素構文を使用します。  
  
 別の用語の詳細については、「[XAML Syntax の詳細](../advanced/xaml-syntax-in-detail.md)」を参照してください。  
  
<a name="MBandPB"></a>   
### <a name="multibinding-and-prioritybinding"></a>MultiBinding と PriorityBinding  
 <xref:System.Windows.Data.MultiBinding> <xref:System.Windows.Data.PriorityBinding> XAML 拡張構文をサポートしていません。 宣言している場合、オブジェクト要素構文を使用する必要があります、<xref:System.Windows.Data.MultiBinding>または<xref:System.Windows.Data.PriorityBinding>XAML でします。  
  
<a name="BindinginCode"></a>   
## <a name="creating-a-binding-in-code"></a>コードでバインディングを作成する方法  
 バインディングを指定する別の方法がプロパティを直接設定するには、<xref:System.Windows.Data.Binding>コード内のオブジェクト。 次の例を作成する方法を示しています、<xref:System.Windows.Data.Binding>オブジェクトし、コードでプロパティを指定します。  この例で`TheConverter`を実装するオブジェクトには、<xref:System.Windows.Data.IValueConverter>インターフェイス。  
  
 [!code-csharp[BindConversion#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindConversion/CSharp/Window1.xaml.cs#1)]
 [!code-vb[BindConversion#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindConversion/visualbasic/window1.xaml.vb#1)]  
  
 バインドするオブジェクトがある場合、<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>呼び出すことができます、`SetBinding`メソッドをオブジェクトを使用してではなく、直接<xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType>します。 例については、「[Create a Binding in Code](how-to-create-a-binding-in-code.md)」を参照してください。  
  
<a name="Path_Syntax"></a>   
## <a name="binding-path-syntax"></a>バインディング パス構文  
 使用して、<xref:System.Windows.Data.Binding.Path%2A>プロパティにバインドするソース値を指定します。  
  
-   最も簡単なケースで、<xref:System.Windows.Data.Binding.Path%2A>プロパティの値など、バインドに使用するソース オブジェクトのプロパティの名前は、`Path=PropertyName`します。  
  
-   同様の構文でプロパティのサブプロパティを指定できますC#します。 たとえば、句 `Path=ShoppingCart.Order` は、バインディングをオブジェクトのサブプロパティ `Order` またはプロパティ `ShoppingCart` に設定します。  
  
-   添付プロパティにバインドするには、添付プロパティをかっこで囲みます。 たとえば、添付プロパティにバインドする<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>、構文は`Path=(DockPanel.Dock)`します。  
  
-   プロパティのインデクサーは、インデクサーが適用されているプロパティ名の後ろの角かっこ内に指定できます。 たとえば、句 `Path=ShoppingCart[0]` は、プロパティの内部インデックスがリテラル文字列「0」を処理する方法に対応するインデックスへのバインディングを設定します。 入れ子になったインデクサーもサポートします。  
  
-   `Path` 句ではインデクサーとサブプロパティを混在させることができます。例: `Path=ShoppingCart.ShippingInfo[MailingAddress,Street].`  
  
-   インデクサーの内側には、コンマ (,) で区切られた複数のインデクサー パラメーターを設定できます。 かっこで囲んで各パラメーターの型を指定できます。 たとえば、ある`Path="[(sys:Int32)42,(sys:Int32)24]"`ここで、`sys`にマップされて、`System`名前空間。  
  
-   ソースがコレクション ビューの場合は、スラッシュ (/) で、現在の項目を指定できます。 句ではたとえば、`Path=/`ビューの現在の項目にバインディングを設定します。 ソースがコレクションである場合は、この構文は、既定のコレクション ビューの現在の項目を指定します。  
  
-   プロパティは、コレクションを走査するプロパティの名前とスラッシュを結合できます。 たとえば、`Path=/Offices/ManagerName`を含むソース コレクションの現在の項目を指定します、`Offices`コレクションでもあるプロパティ。 現在の項目が格納しているオブジェクト、`ManagerName`プロパティ。  
  
-   必要に応じて、現在のソースにバインドするピリオド (.) のパスを使用できます。 たとえば、`Text="{Binding}"` は、`Text="{Binding Path=.}"` と同じです。  
  
### <a name="escaping-mechanism"></a>エスケープのしくみ  
  
-   インデクサー ([ ]) 内では、キャレット文字 (^) は次の文字をエスケープします。  
  
-   設定した場合<xref:System.Windows.Data.Binding.Path%2A>XAML でする必要がありますが、XML 言語定義に特殊な特定の文字エスケープ (XML エンティティを使用)。  
  
    -   文字 "&" をエスケープするには、`&` を使用します。  
  
    -   使用する`>`終了タグをエスケープする">"です。  
  
-   さらに、マークアップ拡張構文を使用して属性のバインディング全体を記述する場合、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] マークアップ拡張機能パーサーで特別な意味を持つ文字を (円記号 \\ を使用して) エスケープする必要があります。  
  
    -   円記号 (\\) はエスケープ文字そのものです。  
  
    -   等号 (=) は、プロパティ名とプロパティの値を区切ります。  
  
    -   コンマ (,) はプロパティを区切ります。  
  
    -   右中かっこ (}) は、マークアップ拡張機能の終わりです。  
  
<a name="Default"></a>   
## <a name="default-behaviors"></a>既定の動作  
 既定の動作は、宣言で指定されていない場合には次のとおりです。  
  
-   バインディング ソースの値とバインディング ターゲットの値の型変換を実行しようとする既定のコンバーターが作成されます。 変換を実行できない場合、既定のコンバーターは `null` を返します。  
  
-   設定しない場合<xref:System.Windows.Data.Binding.ConverterCulture%2A>、バインディング エンジンは、`Language`バインディング ターゲット オブジェクトのプロパティ。 XAML では、既定で "en-US" になるか、または明示的に設定されている場合にはページのルート要素 (または任意の要素) から値を継承します。  
  
-   バインディングと同じくらいは既にデータ コンテキスト (たとえば、継承されたデータ コンテキストの親要素から)、およびどのような項目またはそのコンテキストによって返されるコレクションは、バインディングの適切なパスの変更を必要とせず、バインディング宣言を持たない句で。`{Binding}` これは、多くの場合、データのスタイル設定、バインディングがコレクションには機能のバインドが指定する方法です。 詳細については、「[バインディング ソースの概要](binding-sources-overview.md)」の「バインディング ソースとして使用する全体オブジェクト」セクションを参照してください。  
  
-   既定の<xref:System.Windows.Data.Binding.Mode%2A>一方向と双方向で異なりますバインドされている依存関係プロパティによって異なります。 常にバインディング モードを明示的に宣言し、バインディングに目的の動作があることを確認できます。 一般的に、ユーザーが編集可能なコントロールのプロパティでなど<xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>と<xref:System.Windows.Controls.Primitives.RangeBase.Value%2A?displayProperty=nameWithType>、既定の他のほとんどのプロパティは既定で一方向のバインドは双方向のバインディング。  
  
-   既定の<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>値によって異なります<xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>と<xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>も、バインドされた依存関係プロパティによって異なります。 ほとんどの依存関係プロパティの既定値は <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> です。ただし、<xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> プロパティの既定値は <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> です。  
  
## <a name="see-also"></a>関連項目

- [データ バインディングの概要](data-binding-overview.md)
- [方法トピック](data-binding-how-to-topics.md)
- [データ バインディング](../advanced/optimizing-performance-data-binding.md)
- [PropertyPath の XAML 構文](../advanced/propertypath-xaml-syntax.md)
