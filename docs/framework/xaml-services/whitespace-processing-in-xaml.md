---
title: XAML での空白の処理
ms.date: 03/30/2017
helpviewer_keywords:
- East Asian characters [XAML Services]
- XAML [XAML Services], white-space processing
- white-space processing in XAML [XAML Services]
- characters [XAML Services], East Asian
ms.assetid: cc9cc377-7544-4fd0-b65b-117b90bb0b23
ms.openlocfilehash: 930e8a0013dd601aaafcd81340b3b9b8b69f8fdd
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458499"
---
# <a name="white-space-processing-in-xaml"></a>XAML での空白の処理
[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] のプロセッサ実装によって有意な空白が処理される必要がある XAML 状態の言語規則。 ここでは、それらの XAML 言語規則について説明します。 また、XAML プロセッサの [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] 実装と、シリアル化用の XAML ライターによって定義される追加の空白文字の処理についても説明します。  
  
<a name="whitespace_definition"></a>   
## <a name="white-space-definition"></a>空白の定義  
 [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)]との整合性、[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] 内の空白文字は、スペース、改行、およびタブです。これらは、それぞれ Unicode 値0020、000A、および0009に対応します。  
  
<a name="whitespace_normalization"></a>   
## <a name="white-space-normalization"></a>空白の正規化  
 既定では、[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] プロセッサが [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] ファイルを処理するときに、次の空白の正規化が行われます。  
  
1. 東アジア言語の文字間の改行文字が削除されます。 この用語の定義については、後の「東アジア言語の文字」を参照してください。  
  
2. すべての空白文字 (スペース、改行、タブ) は、スペースに変換されます。  
  
3. 連続した複数のスペースはすべて削除され、1 つのスペースに置換されます。  
  
4. 開始タグの直後にあるスペースは削除されます。  
  
5. 終了タグの直前にあるスペースは削除されます。  
  
 "既定" とは、 [xml:space](xml-space-handling-in-xaml.md) 属性の既定値で表される状態に対応します。  
  
<a name="whitespace_in_inner_text_and_string_primitives"></a>   
## <a name="white-space-in-inner-text-and-string-primitives"></a>内部テキスト内の空白、および文字列プリミティブ  
 前の正規化規則は、XAML 要素内で検出された内部テキストに適用されます。 正規化の後、XAML プロセッサは、次のようにして、すべての内部テキストを適切な型に変換します。  
  
- プロパティの型がコレクションでなく、直接的に <xref:System.Object> 型でもない場合、XAML プロセッサはその型の型コンバーターを使用して、その型への変換を試みます。 その際、変換に失敗すると、コンパイル時のエラーが発生します。  
  
- プロパティの型がコレクションで、内部テキストが連続している (間に要素タグがない) 場合、その内部テキストは単一の <xref:System.String>として解析されます。 そのコレクション型が <xref:System.String>を受け入れない場合にも、コンパイル時のエラーが発生します。  
  
- プロパティの型が <xref:System.Object>である場合、その内部テキストは単一の <xref:System.String>として解析されます。 その内部テキストの中に要素タグが含まれている場合には、コンパイル時のエラーが発生します。これは、 <xref:System.Object> 型は単一のオブジェクト (<xref:System.String> またはそれ以外) であることを意味しているためです。  
  
- プロパティの型がコレクションであり、内部テキストが連続していないことがあります。この場合、最初の部分文字列は <xref:System.String> に変換されてコレクション項目として追加されます。中間にある要素はコレクション項目として追加され、この要素の後に続く部分文字列 (存在する場合) は 3 番目の <xref:System.String> 項目としてコレクションに追加されます。  
  
<a name="preserving_whitespace"></a>   
## <a name="preserving-white-space"></a>保持 (空白を)  
 [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] プロセッサの空白の正規化によって影響を受けない最終的なプレゼンテーションのために、ソース [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] の空白を維持するためのいくつかの手法があります。  
  
 **xml: space = "preserve"** : 空白を保持する必要がある要素のレベルでこの属性を指定します。 この場合、要素を視覚的にわかりやすい入れ子として "美しく表示する" ためにコード編集アプリケーションによって追加されたスペースも含めて、すべての空白が保持されます。 ただし、これらのスペースが表示されるかどうかは、スペースを含んでいる要素のコンテンツ モデルによって決まります。 属性の設定方法に関係なく、ほとんどのオブジェクトモデルでは空白を考慮しないため、ルートレベルで `xml:space="preserve"` を指定することは避けてください。 グローバルに `xml:space` を設定すると、一部の実装で XAML 処理 (特にシリアル化) のパフォーマンスに影響することがあります。 属性は、文字列内の空白を表示する要素のレベルでのみ設定することをお勧めします。または、空白の有意なコレクションである場合にのみ設定することをお勧めします。  
  
 **エンティティと非互換性スペース**: [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] では、テキストオブジェクトモデル内に任意の Unicode エンティティを配置できます。 非区切り領域 (& \#160; UTF-8 エンコード) などの専用エンティティを使用できます。 また、改行しないスペース文字をサポートするリッチ テキスト コントロールを使用することもできます。 インデントなどのレイアウト特性をシミュレートするためにエンティティを使用する場合には、エンティティの実行時出力が、一般的なレイアウト システムにおけるインデントの生成機能を使用した場合よりも多くの要因 (パネルや余白の適切な使用など) に基づいて変化するため、注意が必要です。 たとえば、エンティティはフォントにマッピングされ、ユーザーのフォント選択に応じてサイズが変わる可能性があります。  
  
<a name="east_asian_characters"></a>   
## <a name="east-asian-characters"></a>東アジア言語の文字  
 "東アジア言語の文字" は、Unicode 文字の範囲である U + 20000 ~ u + 2FFFD、U + 30000 から U + いのセットとして定義されています。 このサブセットは、「CJK 表意文字」と呼ばれることもあります。 詳細については、「<https://www.unicode.org>」を参照してください。  
  
<a name="whitespace_and_text_content_models"></a>   
## <a name="white-space-and-text-content-models"></a>空白とテキストコンテンツモデル  
 実際には、空白の保持は、すべての可能なコンテンツモデルのサブセットについてのみ問題になります。 このサブセットに含まれるのは、ある種のシングルトン <xref:System.String> 型、専用の <xref:System.String> コレクション、または <xref:System.String> や <xref:System.Collections.IList> コレクションでの <xref:System.Collections.Generic.ICollection%601> と他の型の組み合わせをとることのできるコンテンツ モデルです。  
  
### <a name="white-space-and-text-content-models-in-wpf"></a>WPF での空白とテキストコンテンツモデル  
 一例として、このセクションの残りの部分では、WPF によって定義されている特定の型について説明します。 このトピックで説明する空白の処理機能は、通常、.NET Framework XAML サービスと WPF の両方に関連します。 これらの動作を実際に見るには、何かの WPF XAML マークアップを使用し、オブジェクト グラフでその結果を確認し、再度マークアップにシリアル化してください。  
  
 文字列を受け取ることができるコンテンツモデルの場合でも、これらのコンテンツモデル内の既定の動作では、残っている空白は重要なものとして扱われません。 たとえば、<xref:System.Windows.Controls.ListBox> は <xref:System.Collections.IList> を受け取りますが、空白 (各 <xref:System.Windows.Controls.ListBoxItem> の間の改行など) は保持されず、レンダリングされません。 改行文字を <xref:System.Windows.Controls.ListBoxItem> 項目の文字列間の区切り記号として使用しても、まったく機能しません。改行文字で区切られた文字列は、1 つの文字列および 1 つの項目として扱われます。  
  
 空白を有意として扱うコレクションは、通常、フロードキュメントモデルの一部です。 空白を保持する動作をサポートするプライマリコレクションは <xref:System.Windows.Documents.InlineCollection> です。 このコレクションクラスは <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>を使用して宣言されています。この属性が検出されると、[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] プロセッサはコレクション内の空白を重要なものとして扱います。 コレクションを表す <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> 内の `xml:space="preserve"` と空白の組み合わせは、すべての空白が保持されて表示されることを示します。 <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> 内の `xml:space="default"` と空白の組み合わせによって、前に説明した最初の空白の正規化が行われます。これにより、特定の位置に1つのスペースが残され、それらのスペースは保持され、レンダリングされます。 どちらの動作が望ましいかは、開発者の意図によって異なります。そのため、 `xml:space` は、必要な動作が有効となるように、選択的に使用する必要があります。  
  
 また、フロードキュメントモデルで linebreak を意味する特定のインライン要素では、空白の有意なコレクションでも余分なスペースを導入しないようにする必要があります。 たとえば、<xref:System.Windows.Documents.LineBreak> 要素は HTML の \<BR/> タグと同じ目的を持ち、マークアップで読みやすくするために、通常、<xref:System.Windows.Documents.LineBreak> は、作成された改行によって後続のテキストから分離されています。 その改行は、正規化されて後続の行の先頭のスペースになってはなりません。 この動作を有効にするために、<xref:System.Windows.Documents.LineBreak> 要素のクラス定義によって <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>が適用されます。これは [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] プロセッサによって解釈され、<xref:System.Windows.Documents.LineBreak> 周辺の空白が常に切り捨てられます。  
  
## <a name="see-also"></a>関連項目

- [XAML の概要 (WPF)](../../desktop-wpf/fundamentals/xaml.md)
- [XML 文字エンティティと XAML](xml-character-entities-and-xaml.md)
- [xml: XAML での領域の処理](xml-space-handling-in-xaml.md)
