---
title: '方法: 定数 (Visual Basic) の宣言します。'
ms.date: 07/20/2015
f1_keywords:
- vb.constant
helpviewer_keywords:
- Integer data type [Visual Basic], declaring constants
- Single data type [Visual Basic], declaring constants
- Const statement [Visual Basic], declaring constants
- procedures [Visual Basic], declaration
- data types [Visual Basic], constants
- Long data type [Visual Basic], declaring constants
- Visual Basic code, declaring variables and constants
- Double data type [Visual Basic], declaring constants
- Boolean data type [Visual Basic], declaring constants
- modules, declaring constants
- Byte data type [Visual Basic], declaring constants
- constants [Visual Basic], declaring
- Date data type [Visual Basic], declaring constants
- String data type [Visual Basic], declaring constants
- declaring constants [Visual Basic], const keyword
- Currency data type [Visual Basic], declaring constants and variants
- module-level constants and variables
- Object data type [Visual Basic], declaring constants
ms.assetid: f901b4fa-481f-4621-822e-427060577ad1
ms.openlocfilehash: 95bfa3da5499c518dad0c235b539784fee2bb522
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58843410"
---
# <a name="how-to-declare-a-constant-visual-basic"></a>方法: 定数 (Visual Basic) の宣言します。
使用する、`Const`定数を宣言し、その値を設定するステートメント。 定数を宣言すると、値に意味のある名前を割り当てます。 定数が宣言されると、変更または新しい値を代入することはできません。  
  
 または、モジュール、クラスまたは構造体の宣言セクションに、プロシージャ内で定数を宣言するとします。 クラスまたは構造のレベルの定数は、`Private`既定では、としても宣言されている可能性がありますが、 `Public`、 `Friend`、 `Protected`、または`Protected Friend`コードへのアクセスのレベルの適切な場合。  
  
 定数は、(、規則は、同じ変数名を作成するためのものと)、有効なシンボリック名と式で構成される数値または文字列定数、演算子、(関数呼び出しはありません) が必要です。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-declare-a-constant"></a>定数を宣言するには  
  
-   アクセス指定子を含む宣言を記述、`Const`キーワード、および次の例のように、式。  
  
     [!code-vb[VbEnumsTask#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#8)]  
  
     ときに[Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md)は`Off`と[Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)は`On`、データ型を指定することで、定数を明示的に宣言する必要があります (`Boolean`、 `Byte`、 `Char`、 `DateTime`、 `Decimal`、 `Double`、 `Integer`、 `Long`、 `Short`、 `Single`、または`String`)。  
  
     ときに`Option Infer`は`On`または`Option Strict`は`Off`、定数を宣言するにはデータ型を指定せず、`As`句。 コンパイラは、定数式の型からの種類を決定します。 詳細については、次を参照してください。[定数とリテラルのデータ型](constant-and-literal-data-types.md)します。  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a>明示的な型を持つ定数を宣言するのには  
  
-   含む宣言を記述、`As`次の例のように、キーワードと、明示的なデータを入力します。  
  
     [!code-vb[VbEnumsTask#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#9)]  
  
     コードは 1 行につき 1 つの定数のみを宣言する場合より読みやすい 1 つの行に複数の定数を宣言できます。 1 行に複数の定数を宣言する場合、すべて必要があります、同じアクセス レベル (`Public`、 `Private`、 `Friend`、 `Protected`、または`Protected Friend`)。  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a>1 行に複数の定数を宣言するには  
  
-   宣言をコンマと次の例のように、スペースで区切ります。  
  
    ```  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a>関連項目

- [Const ステートメント](../../../../visual-basic/language-reference/statements/const-statement.md)
- [定数とリテラルのデータ型](constant-and-literal-data-types.md)
- [定数の概要](constants-overview.md)
- [方法: 定数を宣言します。](how-to-declare-a-constant.md)
- [ユーザー定義定数](user-defined-constants.md)
- [定数とリテラルのデータ型](constant-and-literal-data-types.md)
- [方法: 関連する定数値をまとめてグループ](how-to-group-related-constant-values-together.md)
- [列挙型の概要](enumerations-overview.md)
- [方法: 列挙体を宣言します。](how-to-declare-enumerations.md)
- [方法: 列挙体のメンバーを参照してください。](how-to-refer-to-an-enumeration-member.md)
- [列挙型と名前の修飾](enumerations-and-name-qualification.md)
- [方法: 列挙体を反復処理します。](how-to-iterate-through-an-enumeration.md)
- [方法: 列挙値に関連付けられている文字列を確認します。](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [列挙型を使用する状況](when-to-use-an-enumeration.md)

- [列挙型の概要](enumerations-overview.md)
- [定数の概要](constants-overview.md)
- [方法: 列挙体を宣言します。](how-to-declare-enumerations.md)
- [列挙型と名前の修飾](enumerations-and-name-qualification.md)
- [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [定数と列挙体](../../../../visual-basic/language-reference/constants-and-enumerations.md)
