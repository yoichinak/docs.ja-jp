---
title: 列挙型と名前修飾 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- Imports statement [Visual Basic], namespace declarations
- declaring namespaces [Visual Basic], enumerations
- name collisions
- ambiguous names [Visual Basic], enumerations
- enumerations [Visual Basic], name qualification
- names [Visual Basic], avoiding conflicts
- namespaces [Visual Basic], declaring
- naming conflicts, enumerations
- naming conflicts, qualifying names
- declaring enumerations
- references [Visual Basic], enumeration members
- naming conventions [Visual Basic], naming conflicts
- declarations [Visual Basic], namespaces
ms.assetid: 08ba2738-df52-4140-bc55-f57c871c9b73
ms.openlocfilehash: f0a806b040720cf6682f8a72025a0590dd4d91f7
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58818437"
---
# <a name="enumerations-and-name-qualification-visual-basic"></a>列挙型と名前修飾 (Visual Basic)
通常、列挙体のメンバーを指す場合は、列挙名でメンバー名を修飾する必要があります。 たとえばを参照する、`Sunday`のメンバー、`Days`列挙型では、次の構文を使用します。  
  
 [!code-vb[VbEnumsTask#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#18)]  
  
## <a name="using-the-imports-statement"></a>Imports ステートメントを使用します。  
 完全修飾名を使用して追加することで回避できます、`Imports`ステートメントを次の例のように、コードの名前空間の宣言セクション。  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 `Imports`と内から参照されたプロジェクトおよびアセンブリから、ステートメントが名前空間をインポート、ステートメントが表示されるモジュールと同じプロジェクト。 このステートメントを追加すると、次の例のように、修飾なしの列挙型メンバーを参照できます。  
  
 [!code-vb[VbEnumsTask#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#24)]  
  
 列挙型に関連する定数のセットを整理することによって、別のコンテキストで同じ定数名を使用できます。 曜日の定数に同じ名前を使用するなど、`Days`と`WorkDays`列挙体。 使用する場合、`Imports`ステートメントで列挙型では、する必要がありますあいまいな参照を回避するように注意してください。 次に例を示します。  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 [!code-vb[VbEnumsTask#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#25)]  
  
 仮定`Monday`両方のメンバーである、`Days`列挙と`Workdays`列挙型でこのコードはコンパイラ エラーを生成します。 あいまいな参照を避けるためには、個々 の定数を参照するときには、その列挙型の定数名を修飾します。 次のコードを指す、`Saturday`内の定数、`Days`と`WorkDays`列挙体。  
  
 [!code-vb[VbEnumsTask#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#32)]  
  
## <a name="see-also"></a>関連項目

- [定数と列挙体](../../../../visual-basic/language-reference/constants-and-enumerations.md)
- [方法: 列挙体を宣言します。](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [方法: 列挙体のメンバーを参照してください。](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [方法: Visual Basic で列挙型を反復処理します。](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [方法: 列挙値に関連付けられている文字列を確認します。](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [列挙型を使用する状況](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [定数とリテラルのデータ型](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [Enum ステートメント](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [Imports ステートメント (.NET 名前空間および型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [データの種類](../../../../visual-basic/language-reference/data-types/index.md)
