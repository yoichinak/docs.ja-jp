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
ms.openlocfilehash: d29e8771d61c04cf35aa71b5ba7fbba0d308c730
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965677"
---
# <a name="character-data-types-visual-basic"></a>文字データ型 (Visual Basic)
Visual Basic には、印刷可能な文字と表示可能な文字を処理する*文字データ型*が用意されています。 どちらも Unicode 文字を処理します`Char`が、は1つ`String`の文字を保持しますが、には無限の文字数が含まれます。  
  
 Visual Basic のデータ型の並列比較を表示するテーブルについては、「[データ型](../../../../visual-basic/language-reference/data-types/index.md)」を参照してください。  
  
## <a name="char-type"></a>Char 型  
 `Char`データ型は、1つの2バイト (16 ビット) Unicode 文字です。 変数が常に1つの文字を正確に格納`Char`する場合は、として宣言します。 例:  
  
 [!code-vb[VbVbalrCharTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#1)]
  
 変数`Char`または`String`変数に指定できる値は、Unicode 文字セットの*コードポイント*(文字コード) です。 Unicode 文字には、基本的な ASCII 文字セット、その他のさまざまなアルファベット文字、アクセント、通貨記号、分数、分音記号、数学、およびテクニカルシンボルが含まれます。  
  
> [!NOTE]
> Unicode 文字セットでは、*サロゲートペア*の DFFF (55296 ~ 55551 decimal) を介してコードポイント D800 が予約されています。これには、1つのコードポイントを表す 2 16 ビット値が必要です。 変数`Char`はサロゲートペアを保持できず、は`String` 2 つの位置を使用してこのペアを保持します。  
  
 詳細については、「 [Char データ型](../../../../visual-basic/language-reference/data-types/char-data-type.md)」を参照してください。  
  
## <a name="string-type"></a>文字列型  
 データ`String`型は、0個以上の2バイト (16 ビット) Unicode 文字のシーケンスです。 変数に不特定数の文字を含めることができる場合は、 `String`として宣言します。 例:  
  
 [!code-vb[VbVbalrCharTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#2)]
  
 詳細については、「 [String データ型](../../../../visual-basic/language-reference/data-types/string-data-type.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [基本データ型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [複合データ型](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Visual Basic におけるジェネリック型](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Visual Basic での型変換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [トラブルシューティング (データ型)](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [型文字](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
