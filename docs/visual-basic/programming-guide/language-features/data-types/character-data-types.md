---
title: 文字データ型 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], character
- String data type [Visual Basic], character data types
- character data types [Visual Basic]
- Char data type [Visual Basic], character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
ms.openlocfilehash: 14085172a8f9f9d60af0495a36dd4ba7592213fa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58840979"
---
# <a name="character-data-types-visual-basic"></a>文字データ型 (Visual Basic)
Visual Basic では*文字データ型*文字や表示可能な文字を処理します。 Unicode 文字の場合は、どちらも、処理中に`Char`は単一の文字を保持`String`不特定数文字にはが含まれています。  
  
 Visual Basic のデータ型のサイド バイ サイドで比較を表示するテーブルを参照してください[データ型](../../../../visual-basic/language-reference/data-types/index.md)します。  
  
## <a name="char-type"></a>Char 型  
 `Char`データ型が 1 つ 2 バイト (16 ビット) の Unicode 文字。 変数は、常に正確に 1 つの文字を保存する場合の宣言として`Char`します。 例:  
  
 [!code-vb[VbVbalrCharTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#1)]
  
 使用可能な各値を`Char`または`String`変数は、*コード ポイント*、または Unicode 文字セット内の文字コード。 Unicode 文字には、基本的な ASCII 文字セット、さまざまな他のアルファベット文字、アクセント記号、通貨記号、分数、分音記号、および数学的、技術的な記号が含まれます。  
  
> [!NOTE]
>  Unicode 文字セットは、コード ポイント D800 ~ DFFF (55296 55551 経由) の*サロゲート ペア*、1 つのコード ポイントを表す 2 つの 16 ビット値を必要とします。 A`Char`変数は、サロゲート ペアを保持できない、 `String` 2 つの位置を使用して、このようなペアを保持します。  
  
 詳細については、次を参照してください。 [Char データ型](../../../../visual-basic/language-reference/data-types/char-data-type.md)します。  
  
## <a name="string-type"></a>文字列型  
 `String`データ型は 0 個以上の 2 バイト (16 ビット) の Unicode 文字のシーケンスです。 場合は、変数には、不特定数の文字を含めることができます、宣言として`String`します。 例:  
  
 [!code-vb[VbVbalrCharTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#2)]
  
 詳細については、次を参照してください。[文字列データ型](../../../../visual-basic/language-reference/data-types/string-data-type.md)します。  
  
## <a name="see-also"></a>関連項目

- [基本データ型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [複合データ型](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Visual Basic におけるジェネリック型](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Visual Basic における型変換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [トラブルシューティング (データ型)](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [型文字](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
