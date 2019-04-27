---
title: '方法: (Visual Basic) 列挙型を宣言します。'
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- enumerations [Visual Basic], declaring
- declaring enumerations [Visual Basic]
ms.assetid: db4ca1c3-f429-4c81-ae81-29e0157b29fd
ms.openlocfilehash: f168d6d9cd6970353e75fa35a7e52cc7156fda72
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61907648"
---
# <a name="how-to-declare-enumerations-visual-basic"></a>方法: (Visual Basic) 列挙型を宣言します。
持つ列挙体を作成する、`Enum`クラスまたはモジュールの宣言セクション内のステートメント。 メソッド内で列挙型を宣言することはできません。 適切なアクセス レベルを指定するには、使用`Private`、 `Protected`、 `Friend`、または`Public`します。  
  
 `Enum`型の名前、基になる型とに一連のフィールドでは、それぞれの定数を表します。 名前は、有効な Visual Basic .NET 修飾子にする必要があります。 基になる型が整数型のいずれかを指定する必要があります:`Byte`、 `Short`、`Long`または`Integer`します。 `Integer` が既定値です。 列挙型では、常に厳密に型指定し、整数の数値型で置き換えることはできません。  
  
 列挙体は、浮動小数点値を持つことはできません。 列挙には、浮動小数点値が割り当てられている場合`Option Strict On`、コンパイラ エラーが発生します。 場合`Option Strict`は`Off`に、値が自動的に変換、`Enum`型。  
  
 使用する方法と、名について、`Imports`ステートメント、不要な名前の修飾を参照してください[列挙型と名前修飾](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)します。  
  
### <a name="to-declare-an-enumeration"></a>列挙型を宣言するには  
  
1. コードのアクセス レベルを含む宣言を記述、`Enum`キーワード、および有効な名前を次の例のようにそれぞれの宣言を異なる`Enum`します。  
  
     [!code-vb[VbEnumsTask#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#3)]  
  
2. 列挙体の定数を定義します。 既定では、最初の定数、列挙型でに初期化`0`、され、それに続く定数よりも前の定数のいずれかの値に初期化します。 たとえば、次の列挙`Days`、という名前の定数が含まれています`Sunday`値を持つ`0`、という名前の定数`Monday`値を持つ`1`、という名前の定数`Tuesday`の値を持つ`2`など。  
  
     [!code-vb[VbEnumsTask#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#4)]  
  
3. 代入ステートメントを使用して、列挙型の定数に値を明示的に割り当てることができます。 負の数値を含む、任意の整数値を割り当てることができます。 たとえば、エラー条件を表す 0 より小さい値を持つ定数たい場合があります。 次の列挙型定数`Invalid`値を明示的に割り当てられて`–1`と定数`Sunday`値が割り当てられている`0`します。 最初の定数、列挙型である`Saturday`値にも初期化`0`します。 値`Monday`は`1`(いずれかの値よりも詳細`Sunday`); の値`Tuesday`は`2`など。  
  
     [!code-vb[VbEnumsTask#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#5)]  
  
### <a name="to-declare-an-enumeration-as-an-explicit-type"></a>明示的な型として列挙型を宣言するには  
  
-   使用して、列挙型の種類を指定、`As`句では、次の例に示すようにします。  
  
     [!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]  
  
## <a name="see-also"></a>関連項目

- [列挙型と名前の修飾](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [方法: 列挙体のメンバーを参照してください。](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [方法: Visual Basic で列挙型を反復処理します。](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [方法: 列挙値に関連付けられている文字列を確認します。](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [列挙型を使用する状況](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [定数の概要](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [定数とリテラルのデータ型](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [定数と列挙体](../../../../visual-basic/language-reference/constants-and-enumerations.md)
