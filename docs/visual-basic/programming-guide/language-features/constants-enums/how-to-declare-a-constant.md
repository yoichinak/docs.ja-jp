---
title: '方法: 定数を宣言する (Visual Basic)'
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
ms.openlocfilehash: 8b84ab5e8edebba3048c5cddf723198cf3f28858
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2019
ms.locfileid: "72579924"
---
# <a name="how-to-declare-a-constant-visual-basic"></a>方法: 定数を宣言する (Visual Basic)
@No__t_0 ステートメントを使用して定数を宣言し、その値を設定します。 定数を宣言すると、意味のある名前を値に代入します。 定数を宣言すると、変更したり、新しい値を割り当てたりすることはできません。  
  
 定数は、プロシージャ内で、またはモジュール、クラス、または構造体の宣言セクションで宣言します。 クラスまたは構造体レベルの定数は既定で `Private` されますが、適切なレベルのコードアクセスに対して `Public`、`Friend`、`Protected`、または `Protected Friend` として宣言することもできます。  
  
 定数には有効なシンボリック名 (規則は変数名を作成するための規則と同じです) と、数値または文字列の定数と演算子で構成される式 (ただし関数呼び出しは含まれません) が必要です。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-declare-a-constant"></a>定数を宣言するには  
  
- 次の例に示すように、アクセス指定子、`Const` キーワード、および式を含む宣言を記述します。  
  
     [!code-vb[VbEnumsTask#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#8)]  
  
     [オプションの推論](../../../../visual-basic/language-reference/statements/option-infer-statement.md)が `Off` で、 [option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)が `On` 場合、データ型 (`Boolean`、`Byte`、`Char`、`DateTime`、`Decimal`、`Double` を指定して、定数を明示的に宣言する必要があり 0、1、2、3、または 4)。  
  
     @No__t_0 が `On` または `Option Strict` が `Off` 場合は、`As` 句を使用してデータ型を指定せずに定数を宣言できます。 コンパイラは、式の型から定数の型を特定します。 詳細については、「[定数データ型とリテラルデータ型](constant-and-literal-data-types.md)」を参照してください。  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a>明示的に記述されたデータ型を持つ定数を宣言するには  
  
- 次の例に示すように、`As` キーワードと明示的なデータ型を含む宣言を記述します。  
  
     [!code-vb[VbEnumsTask#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#9)]  
  
     1行に複数の定数を宣言することはできますが、1行につき1つの定数のみを宣言すると、コードが読みやすくなります。 複数の定数を1つの行で宣言する場合は、すべてが同じアクセスレベル (`Public`、`Private`、`Friend`、`Protected`、または `Protected Friend`) である必要があります。  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a>1行で複数の定数を宣言するには  
  
- 次の例のように、宣言をコンマとスペースで区切ります。  
  
    ```vb  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a>関連項目

- [Const ステートメント](../../../../visual-basic/language-reference/statements/const-statement.md)
- [定数とリテラルのデータ型](constant-and-literal-data-types.md)
- [定数の概要](constants-overview.md)
- [方法 : 定数を宣言する](how-to-declare-a-constant.md)
- [ユーザー定義定数](user-defined-constants.md)
- [定数とリテラルのデータ型](constant-and-literal-data-types.md)
- [方法 : 関連する定数値をまとめてグループ化する](how-to-group-related-constant-values-together.md)
- [列挙型の概要](enumerations-overview.md)
- [方法 : 列挙型を宣言する](how-to-declare-enumerations.md)
- [方法 : 列挙型のメンバーを参照する](how-to-refer-to-an-enumeration-member.md)
- [列挙型と名前の修飾](enumerations-and-name-qualification.md)
- [方法 : 列挙型を反復処理する](how-to-iterate-through-an-enumeration.md)
- [方法 : 列挙値に関連付けられている文字列を確認する](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [列挙型を使用する状況](when-to-use-an-enumeration.md)

- [列挙型の概要](enumerations-overview.md)
- [定数の概要](constants-overview.md)
- [方法: 列挙型を宣言する](how-to-declare-enumerations.md)
- [列挙型と名前の修飾](enumerations-and-name-qualification.md)
- [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [定数と列挙体](../../../../visual-basic/language-reference/constants-and-enumerations.md)
