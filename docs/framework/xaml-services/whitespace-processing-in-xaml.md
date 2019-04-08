---
title: XAML での空白の処理
ms.date: 03/30/2017
helpviewer_keywords:
- East Asian characters [XAML Services]
- XAML [XAML Services], white-space processing
- white-space processing in XAML [XAML Services]
- characters [XAML Services], East Asian
ms.assetid: cc9cc377-7544-4fd0-b65b-117b90bb0b23
ms.openlocfilehash: ca628a366b000b23a2abe38b1c8b7272299bff16
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102233"
---
# <a name="white-space-processing-in-xaml"></a>XAML での空白の処理
XAML の言語規則の状態によってその有意の空白を処理する必要があります、[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]プロセッサの実装。 ここでは、それらの XAML 言語規則について説明します。 定義されている追加の空白文字の処理が文書化も、 [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] XAML プロセッサとシリアル化のための XAML ライターの実装。  
  
<a name="whitespace_definition"></a>   
## <a name="white-space-definition"></a>空白の定義  
 一貫性のある[!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)]、空白文字がで[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]はスペース、改行、およびタブ。これらは、それぞれ [!INCLUDE[TLA#tla_unicode](../../../includes/tlasharptla-unicode-md.md)] 値の 0020、000A、および 0009 に対応します。  
  
<a name="whitespace_normalization"></a>   
## <a name="white-space-normalization"></a>空白文字の正規化  
 既定では、次の空白文字の正規化が発生したときに、[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]プロセッサ プロセス、[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]ファイル。  
  
1.  東アジア言語の文字間の改行文字が削除されます。 この用語の定義については、後の「東アジア言語の文字」を参照してください。  
  
2.  すべての空白文字 (スペース、改行、タブ) は、スペースに変換されます。  
  
3.  連続した複数のスペースはすべて削除され、1 つのスペースに置換されます。  
  
4.  開始タグの直後にあるスペースは削除されます。  
  
5.  終了タグの直前にあるスペースは削除されます。  
  
 "既定" とは、 [xml:space](xml-space-handling-in-xaml.md) 属性の既定値で表される状態に対応します。  
  
<a name="whitespace_in_inner_text_and_string_primitives"></a>   
## <a name="white-space-in-inner-text-and-string-primitives"></a>内部のテキスト、および文字列プリミティブ内の空白  
 前の正規化規則は、XAML 要素内で検出された内部テキストに適用されます。 正規化の後、XAML プロセッサは、次のようにして、すべての内部テキストを適切な型に変換します。  
  
-   プロパティの型がコレクションでなく、直接的に <xref:System.Object> 型でもない場合、XAML プロセッサはその型の型コンバーターを使用して、その型への変換を試みます。 その際、変換に失敗すると、コンパイル時のエラーが発生します。  
  
-   プロパティの型がコレクションで、内部テキストが連続している (間に要素タグがない) 場合、その内部テキストは単一の <xref:System.String>として解析されます。 そのコレクション型が <xref:System.String>を受け入れない場合にも、コンパイル時のエラーが発生します。  
  
-   プロパティの型が <xref:System.Object>である場合、その内部テキストは単一の <xref:System.String>として解析されます。 その内部テキストの中に要素タグが含まれている場合には、コンパイル時のエラーが発生します。これは、 <xref:System.Object> 型は単一のオブジェクト (<xref:System.String> またはそれ以外) であることを意味しているためです。  
  
-   プロパティの型がコレクションであり、内部テキストが連続していないことがあります。この場合、最初の部分文字列は <xref:System.String> に変換されてコレクション項目として追加されます。中間にある要素はコレクション項目として追加され、この要素の後に続く部分文字列 (存在する場合) は 3 番目の <xref:System.String> 項目としてコレクションに追加されます。  
  
<a name="preserving_whitespace"></a>   
## <a name="preserving-white-space"></a>空白を維持  
 ソース内の空白を保持するためのいくつかの方法はあります[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]によって影響を受けない最終的なプレゼンテーションの[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]プロセッサの空白文字の正規化します。  
  
 **xml:space="preserve"**:空白の維持が必要な場合、要素のレベルでは、この属性を指定します。 この場合、要素を視覚的にわかりやすい入れ子として "美しく表示する" ためにコード編集アプリケーションによって追加されたスペースも含めて、すべての空白が保持されます。 ただし、これらのスペースが表示されるかどうかは、スペースを含んでいる要素のコンテンツ モデルによって決まります。 指定しないように`xml:space="preserve"`ルート レベルのほとんどのオブジェクト モデルの場合は白考えないため、領域の属性を設定する方法に関係なく、重要な。 グローバルに `xml:space` を設定すると、一部の実装で XAML 処理 (特にシリアル化) のパフォーマンスに影響することがあります。 具体的には、文字列内の空白を表示するか、空白の意味を持つコレクションの要素のレベルでのみ、属性を設定することをお勧めすることをお勧めします。  
  
 **エンティティおよび改行しないスペース**: [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] では、テキスト オブジェクト モデル内に任意の [!INCLUDE[TLA#tla_unicode](../../../includes/tlasharptla-unicode-md.md)] エンティティを配置できます。 改行しないスペースなど、専用のエンティティを使用することができます ((& a)\#160; utf-8 エンコード)。 また、改行しないスペース文字をサポートするリッチ テキスト コントロールを使用することもできます。 インデントなどのレイアウト特性をシミュレートするためにエンティティを使用する場合には、エンティティの実行時出力が、一般的なレイアウト システムにおけるインデントの生成機能を使用した場合よりも多くの要因 (パネルや余白の適切な使用など) に基づいて変化するため、注意が必要です。 たとえば、エンティティはフォントにマッピングされ、ユーザーのフォント選択に応じてサイズが変わる可能性があります。  
  
<a name="east_asian_characters"></a>   
## <a name="east-asian-characters"></a>東アジア言語の文字  
 "東アジア言語の文字" は、U+20000 ～ U+2FFFD および U+30000 ～ U+3FFFD の範囲の [!INCLUDE[TLA2#tla_unicode](../../../includes/tla2sharptla-unicode-md.md)] 文字のセットとして定義されています。 このサブセットは、「CJK 表意文字」と呼ばれることもあります。 詳細については、「 <https://www.unicode.org> 」を参照してください。  
  
<a name="whitespace_and_text_content_models"></a>   
## <a name="white-space-and-text-content-models"></a>空白文字とテキスト コンテンツ モデル  
 実際には、空白の維持のみのすべてのコンテンツ モデルのサブセットの問題です。 このサブセットに含まれるのは、ある種のシングルトン <xref:System.String> 型、専用の <xref:System.String> コレクション、または <xref:System.String> や <xref:System.Collections.IList> コレクションでの <xref:System.Collections.Generic.ICollection%601> と他の型の組み合わせをとることのできるコンテンツ モデルです。  
  
### <a name="white-space-and-text-content-models-in-wpf"></a>WPF での空白文字とテキストのコンテンツ モデル  
 一例として、このセクションの残りの部分では、WPF によって定義されている特定の型について説明します。 このトピックで説明する空白文字の処理機能は、一般に、.NET Framework XAML サービスと WPF の両方に関連します。 これらの動作を実際に見るには、何かの WPF XAML マークアップを使用し、オブジェクト グラフでその結果を確認し、再度マークアップにシリアル化してください。  
  
 コンテンツ モデルの場合でも文字列がかかることができます、残っているすべての空白文字が大きな扱われませんが、これらのコンテンツ モデル内の既定の動作は、します。 たとえば、<xref:System.Windows.Controls.ListBox>は、 <xref:System.Collections.IList>、空白文字が、(各間の改行など<xref:System.Windows.Controls.ListBoxItem>) は保存されず、レンダリングされません。 改行文字を <xref:System.Windows.Controls.ListBoxItem> 項目の文字列間の区切り記号として使用しても、まったく機能しません。改行文字で区切られた文字列は、1 つの文字列および 1 つの項目として扱われます。  
  
 空白文字として扱うこれらのコレクションは、通常、フロー ドキュメント モデルの一部です。 空白文字保存の動作をサポートする主なコレクションは<xref:System.Windows.Documents.InlineCollection>します。 このコレクション クラスが宣言された、<xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>この属性が検出されると、[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]プロセッサでは、コレクション内の空白は重要なとして扱います。 組み合わせた`xml:space="preserve"`内および空白を<xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>コレクションは、すべての空白は保持され、表示されることが示されます。 組み合わせ`xml:space="default"`内および空白を<xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>前に説明した最初の空白文字の正規化原因で、これが特定の位置に 1 つの領域とそのスペースは保持され、レンダリングします。 どちらの動作が望ましいかは、開発者の意図によって異なります。そのため、 `xml:space` は、必要な動作が有効となるように、選択的に使用する必要があります。  
  
 また、フロー ドキュメント モデルで改行を意味する特定のインライン要素では、空白が有意なコレクションであっても、余分なスペースが生じるは意図的にする必要があります。 など、<xref:System.Windows.Documents.LineBreak>要素と同じ目的には、 \<BR/> にタグを付ける[!INCLUDE[TLA2#tla_html](../../../includes/tla2sharptla-html-md.md)]、マークアップでは、読みやすくするため、通常、<xref:System.Windows.Documents.LineBreak>は改行を入れてで後続のテキストから区切られます。 その改行は、正規化されて後続の行の先頭のスペースになってはなりません。 クラス定義は、その動作を有効にする、<xref:System.Windows.Documents.LineBreak>要素が適用される、 <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>、によって解釈されるし、[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]空白文字を囲むことを意味するプロセッサ<xref:System.Windows.Documents.LineBreak>は常に切り捨てられます。  
  
## <a name="see-also"></a>関連項目

- [XAML の概要 (WPF)](../wpf/advanced/xaml-overview-wpf.md)
- [XML 文字エンティティと XAML](xml-character-entities-and-xaml.md)
- [xml:space の XAML での処理](xml-space-handling-in-xaml.md)
