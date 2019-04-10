---
title: XML 文字エンティティと XAML
ms.date: 03/30/2017
f1_keywords:
- '&'
- '&amp'
- '&gt'
- '&lt'
helpviewer_keywords:
- XAML [XAML Services], special characters
- ampersand (&) [XAML Services]
- special characters [XAML Services]
- apostrophe (') [XAML Services]
- greater-than (>) character [XAML Services]
- XAML [XAML Services], quotation mark (")
- XAML [XAML Services], apostrophe (')
- '& (ampersand) [XAML Services]'
- XAML [XAML Services], & (ampersand)
- XAML [XAML Services], escape sequence
- quotation mark (") [XAML Services]
- less-than (<) character [XAML Services]
ms.assetid: 6896d0ce-74f7-420a-9ab4-de9bbf390e8d
ms.openlocfilehash: b4621da21200e6c9e2b174a0e2ba508a4f6bab92
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228199"
---
# <a name="xml-character-entities-and-xaml"></a>XML 文字エンティティと XAML
XAML は、特殊文字に、XML で定義される文字エンティティを使用します。 ここでは、いくつかの特定の文字エンティティ、および XAML における他の XML の概念に関する一般的な考慮事項について説明します。  
  
<a name="character_entities_and_escaping_issues_that_are_unique_to_xaml"></a>   
## <a name="character-entities-and-escaping-issues-that-are-unique-to-xaml"></a>XAML に固有の文字のエンティティとエスケープの問題  
 XAML マークアップでは、一般に、XML で定義されているものと同じ文字エンティティおよびエスケープ シーケンスを使用します。  
  
 大きな違いは、XAML では中かっこ ({ と }) が意味を持つ点です。中かっこで囲まれた文字シーケンスは、マークアップ拡張機能として解釈する必要があることを XAML プロセッサに通知します。 マークアップ拡張機能について詳しくは、「 [Markup Extensions for XAML Overview](markup-extensions-for-xaml-overview.md)」をご覧ください。  
  
 ただし、XML ではなく XAML に固有のエスケープ シーケンスを使用すると、中かっこをリテラル文字として表示できます。 詳細については、次を参照してください。 [ {}エスケープ シーケンス/マークアップ拡張](escape-sequence-markup-extension.md)します。  
  
 なお、円記号 (\\) を文字列として処理されるときに、エスケープ シーケンスは必要ありません。  
  
<a name="xml_character_entities"></a>   
## <a name="xml-character-entities"></a>XML 文字エンティティ  
 前に述べたように、XAML マークアップを記述するときに一般的に使用する文字エンティティおよびエスケープ シーケンスの大半は、XML で定義されています。 このトピックでは、こうしたエンティティの一覧は示しません。エンティティの詳細なリファレンスについては、XML 仕様などの外部ドキュメントを参照してください。 ただし、このトピックでは、便宜を考えて、XAML マークアップでよく使用する XML 文字エンティティを抜粋した一覧を示します。  
  
|文字|エンティティ|メモ|  
|---------------|------------|-----------|  
|& (アンパサンド)|\&amp;|属性値および要素の内容の両方に対して使用する必要があります。|  
|> (大きい-より文字)|\&gt;|属性値に対して使用する必要がありますが、> が同じくらい要素のコンテンツとして許容される < 前しません。|  
|< (以下の文字よりも)|\&lt;|属性値に対して使用する必要がありますが、\<が同じくらい要素のコンテンツとして許容される > それに従っていません。|  
|" (二重引用符)|\&quot;|属性値に対しては使用する必要があります。要素の内容としては、二重引用符 (") も受け入れられます、 属性値は、単一引用符 (') と二重引用符 (") のどちらかで囲むことができます。最初に使用したほうの引用符が、属性値を囲む文字になり、もう一方の引用符は値の中でリテラルとして使用できます。|  
|' (単一引用符)|\&apos;|属性値に対しては使用する必要があります。要素の内容としては、単一引用符 (') も受け入れられます、 属性値は、単一引用符 (') と二重引用符 (") のどちらかで囲むことができます。最初に使用したほうの引用符が、属性値を囲む文字になり、もう一方の引用符は値の中でリテラルとして使用できます。|  
|(数値と文字の対応付け)|&#*[整数]*; または &#x *[進数]*;|XAML では、アクティブなエンコーディングに応じた数値と文字の対応付けがサポートされています。|  
|(改行しないスペース)|&\#160;(utf-8 エンコードを想定)|フロー ドキュメントの要素、または WPF の <xref:System.Windows.Controls.TextBox> などのテキストを受け取る要素では、マークアップからの改行しないスペースの正規化は行われません。これには、`xml:space="default"` の場合も含まれます。 (詳細については、次を参照してください[空白 XAML 処理](whitespace-processing-in-xaml.md)。)。|  
  
<a name="xml_comment_format"></a>   
## <a name="xml-comment-format"></a>XML のコメントの書式  
 XAML では、XML のコメントの書式を使用します。つまり、コメントの先頭は `<!--` で表し、コメントの末尾は `-->,` で表します。コメントの中に `--` というシーケンスを含めることはできません。  
  
<a name="xml_processing_instructions"></a>   
## <a name="xml-processing-instructions"></a>XML 処理命令  
 XAML では、XML 仕様に従って XML 処理命令が処理されます。つまり、命令は必ず素通しされます。 .NET Framework XAML サービスで処理する XAML では、ある処理命令は使用しません。 XAML を使用する他の既存のフレームワークでも、XAML の処理命令は使用されません。  
  
## <a name="see-also"></a>関連項目

- [XAML の概要 (WPF)](../wpf/advanced/xaml-overview-wpf.md)
- [マークアップ拡張機能と WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
- [XamlName の文法](xamlname-grammar.md)
- [XAML での空白の処理](whitespace-processing-in-xaml.md)
