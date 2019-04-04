---
title: 宣言された要素の名前 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic], case sensitivity
- names [Visual Basic], Visual Basic rules
- naming conventions [Visual Basic]
- element names [Visual Basic]
- declared elements [Visual Basic], identifiers
- declarations [Visual Basic], elements
- declared elements [Visual Basic], valid names
- '[] escape characters [Visual Basic]'
- names [Visual Basic], elements
- declaration statements [Visual Basic], declared elements
- declaring elements [Visual Basic]
- identifiers [Visual Basic], declared elements
- case sensitivity, declared element names
- escape characters [Visual Basic]
- names [Visual Basic], declared elements
- declared elements [Visual Basic], about declared elements
- escaped names [Visual Basic]
- declared elements [Visual Basic], names
- names [Visual Basic], naming conventions
- identifiers [Visual Basic], elements
ms.assetid: 09d8843b-c0dc-4afe-9dab-87c439a69e66
ms.openlocfilehash: 5b1f8ccc402f7f5928a33f434664b0f28d108e6d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814069"
---
# <a name="declared-element-names-visual-basic"></a>宣言された要素の名前 (Visual Basic)
宣言された各要素とも呼ばれる、名前を持つ、*識別子*、これは、コードを使用して、それを参照してください。  
  
## <a name="rules"></a>ルール  
 Visual Basic では、要素名は、次の規則に従う必要があります。  
  
-   文字は英字またはアンダー スコアで始まる必要がありますが (`_`)。  
  
-   アルファベット文字、10 進数字およびアンダー スコアのみでなければなりません。  
  
-   アンダー スコアで始まる場合、少なくとも 1 つのアルファベット文字または 10 進数字でなければなりません。  
  
-   長さが 1023 文字はできません。  
  
 1023 文字の長さの制限にも適用されます、完全修飾名では、文字列全体など`outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`します。  
  
 次の例では、有効な要素名を示します。  
  
 `aB123__45`  
  
 `_567`  
  
 次の例では、無効な要素名を示します。 最初にアンダー スコアのみが含まれています、10 進数字の場合は、始まり、2 つ目および 3 番目に無効な文字 ($) が含まれています。  
  
 `' Three INVALID element names`  
  
 `_`  
  
 `12ABC`  
  
 `xyz$wv`  
  
> [!CAUTION]
>  アンダー スコアで始まる要素名 (`_`) は含まれません、 [Language Independence and Language-independent Components](../../../../standard/language-independence-and-language-independent-components.md) (CLS) にため、CLS 準拠コードのような名前を定義するコンポーネントを使用することはできません。 ただし、要素名の他の任意の位置でアンダー スコアは CLS に準拠していません。  
  
### <a name="name-length-guidelines"></a>名前の長さのガイドライン  
 実際には、名前はできるだけ短く中の要素の特性を明確にします。 これは、コードの読みやすさが向上し、行の長さとソース ファイルのサイズを縮小します。  
  
 その一方で、自分の名前は、いない適切に記述できる要素が表す内容と、コードがそれを使用する方法長さである必要があります。 これは、コードの読みやすさにとって重要です。 それを理解しようとする他の人がいる場合、または自分で探している場合に作成した後、長い時間は、適切な要素名は、かなりの時間を保存できます。  
  
## <a name="escaped-names"></a>エスケープされた名前  
 一般に、要素名に一致しないなど、Visual Basic では、によって予約済みキーワードのいずれかの`Case`または`Friend`します。 ただし、定義することができます、*エスケープ名前*、角かっこで囲まれている (`[ ]`)。 エスケープされた名前は、角かっこは、任意のあいまいさをなくすために、Visual Basic のキーワードを照合できます。 後続のコードで名前を参照する場合は、角かっこを使用します。  
  
 一般に、エスケープされた名前を使用する必要がある場合にのみ。  
  
-   コードが名前として使用されているキーワードが確保されていない Visual Basic の以前のバージョンから移行します。または  
  
-   指定されたキーワードが予約されていない別の言語で記述されたコードを使用しています。  
  
 それ以外の場合、キーワードを使用してその名前が競合する場合、要素名の変更を検討してください。 統合開発環境 (IDE) では、これを行う簡単な方法を提供します。 詳細については、[リファクタリング](/visualstudio/vb-ide/refactoring-vb)を参照してください。  
  
## <a name="case-sensitivity-in-names"></a>名前に大文字小文字の区別  
 Visual Basic での要素名は大文字です。 これは、コンパイラは、英字の大文字小文字のみが異なる 2 つの名前を比較をする際を解釈するには同じ名前としてことを意味します。 たとえば、 `ABC` と `abc` は、宣言された同じ要素を参照していると見なされます。  
  
 ただし、共通言語ランタイム (CLR) は、大文字のバインドを使用します。 このため、アセンブリまたは DLL を作成し、他のアセンブリで使用できるようにすると、名前の大文字と小文字が区別されるようになります。 たとえば、 `ABC`という名前の要素を持つクラスを定義し、他のアセンブリから共通言語ランタイムを通じてこのクラスを使用する場合は、この要素を `ABC`として参照する必要があります。 かどうか、その後、クラスを再コンパイルして要素の名前を変更`abc`クラスを使用して、他のアセンブリがその要素にアクセスできなくします。 したがって、アセンブリを更新してリリースするときは、パブリックな要素の名前の大文字と小文字を変更しないでください。  
  
## <a name="names-and-locales"></a>名前とロケール  
 名前の比較ではロケールに依存しません。 1 つのロケールで 2 つの名前が同じ場合は、すべてのロケールに一致するように保証されます。  
  
## <a name="see-also"></a>関連項目

- [宣言された要素](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)
- [宣言された要素の特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [宣言された要素の参照](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [ステートメント](../../../../visual-basic/language-reference/statements/index.md)
