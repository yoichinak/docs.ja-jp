---
title: 宣言する XML 要素と属性の名前 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [XML in Visual Basic]
- element names [XML in Visual Basic]
- names in XML literals [Visual Basic]
- attribute names [XML in Visual Basic]
- XML literals [Visual Basic], element names
ms.assetid: cc110118-b6cf-4ff9-a4e4-6233c90c9fbf
ms.openlocfilehash: 2221f2677183cf360fa82a4d73a679a8b68927d1
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819685"
---
# <a name="names-of-declared-xml-elements-and-attributes-visual-basic"></a>宣言する XML 要素と属性の名前 (Visual Basic)
このトピックでは、XML リテラルの XML 要素と属性の名前付けの Visual Basic のガイドラインを提供します。  XML リテラルでは、ローカル名または修飾名を指定できます。 修飾名は、XML 名前空間プレフィックス、コロン、およびローカル名で構成されます。 XML 名前空間プレフィックスの詳細については、次を参照してください。 [XML 要素リテラル](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)します。  
  
## <a name="rules"></a>ルール  
 要素または Visual Basic での属性のローカル名は、次の規則に従う必要があります。  
  
-   名前空間がそれを開始できます。 先頭にアルファベットまたはアンダー スコア (`_`)。  
  
-   それだけアルファベット文字、10 進数字、アンダー スコア、ピリオド (.)、およびハイフンを含める必要があります (-)。  
  
-   1,024 を超える文字はできません。  
  
-   名前に含まれるコロンは、名前空間の区切りを示します。 そのため、特定の名前の XML 名前空間を指定するだけのコロンを使用することができます。  
  
 さらは、次のガイドラインに従う必要があります。  
  
-   XML 1.0 仕様では、任意の大文字と小文字のバリエーションの"xml"、文字列で始まるすべての名前を予約します。 したがって、これらの要素名および属性名は使用しないでください。  
  
### <a name="name-length-guidelines"></a>名前の長さのガイドライン  
 実際には、名前はできるだけ短く中の要素の特性を明確にします。 これは、コードの読みやすさが向上し、行の長さとソース ファイルのサイズを縮小します。  
  
 ただし、自分の名前は、長さいない適切に記述できる、要素またはコードがそれを使用する方法である必要があります。 これは、コードの読みやすさにとって重要です。 それを理解しようとする他の人がいる場合、または自分で探している場合に作成した後、長い時間は、適切な要素名は、時間を節約できます。  
  
## <a name="case-sensitivity-in-names"></a>名前に大文字小文字の区別  
 XML 要素名は大文字小文字を区別します。 つまり、Visual Basic コンパイラでは、アルファベットの大文字小文字のみが異なる 2 つの名前を比較をする際にいると解釈別の名前。 たとえば、解釈`ABC`と`abc`要素を区切るを指しています。  
  
## <a name="xml-namespaces"></a>XML 名前空間  
 XML 要素リテラルを作成する場合は、要素名の XML 名前空間プレフィックスを指定できます。 詳細については、次を参照してください。 [XML 要素リテラル](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)します。  
  
## <a name="see-also"></a>関連項目

- [Visual Basic での XML の作成](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML 要素リテラル](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
