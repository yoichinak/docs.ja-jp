---
title: '方法: ラベル ステートメント (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
ms.openlocfilehash: 69ec8c7625410f140c59ba8dd492dca76857eb96
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58828642"
---
# <a name="how-to-label-statements-visual-basic"></a>方法: ラベル ステートメント (Visual Basic)
ステートメント ブロックはコロンで区切られたコードの行で構成をされます。 行の識別文字列または整数に続くコードがあると言われますは*というラベルの付いた*します。 ステートメント ラベルは識別するために、使用するためのステートメントでなどのコード行をマークするために使用`On Error Goto`します。  
  
 ラベルとして使用できるは、有効な Visual Basic 識別子、プログラミング要素を識別するようなまたは整数リテラル。 ラベルは、ソース コードの行の先頭に表示する必要があり、かどうかに続くステートメントで同じ行に関係なく、コロンの後にする必要があります。  
  
 コンパイラは、行の先頭に任意に定義済みの識別子が一致するかどうかをチェックして、ラベルを識別します。 そうでない場合、コンパイラでは、ラベルが前提としています。  
  
 ラベルは、独自の宣言領域があるし、他の識別子に干渉することはできません。 ラベルのスコープは、メソッドの本体です。 ラベルの宣言は、あいまいな場合でも優先されます。  
  
> [!NOTE]
>  ラベルは、メソッド内で実行可能ステートメントでのみ使用できます。  
  
### <a name="to-label-a-line-of-code"></a>ラベルのコード行に  
  
-   識別子の後にソース コードの行の先頭のコロンを配置します。  
  
     たとえば、次のコード行ラベルが付けられます`Jump`と`120`、それぞれします。  
  
     [!code-vb[VbVbalrStatements#708](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#708)]  
  
## <a name="see-also"></a>関連項目

- [ステートメント](../../../visual-basic/programming-guide/language-features/statements.md)
- [宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [プログラム構造とコード規則](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
