---
title: 演算子プロシージャ (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- overloaded operators [Visual Basic]
- operator overloading
- operator procedures
ms.assetid: 8c513d38-246b-4fb7-8b75-29e1364e555b
ms.openlocfilehash: 80c9a77494be95365899c6a25435fcfc5d2a7293
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791977"
---
# <a name="operator-procedures-visual-basic"></a>演算子プロシージャ (Visual Basic)
演算子プロシージャは、一連の標準の演算子の動作を定義する Visual Basic ステートメント (など`*`、 `<>`、または`And`) クラスまたは定義した構造にします。 これもと呼ばれる*演算子のオーバー ロード*します。  
  
## <a name="when-to-define-operator-procedures"></a>演算子プロシージャを定義する場合  
 クラスまたは構造体を定義した場合は、そのクラスまたは構造体の型の変数を宣言できます。 このような変数は、式の一部として操作に参加する必要があります。 これを行うには、演算子のオペランドがあります。  
  
 Visual Basic では、その基本データ型でのみ演算子を定義します。 両方のオペランドは、クラスまたは構造体の型または 1 つの場合、演算子の動作を定義できます。  
  
 詳細については、次を参照してください。 [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)します。  
  
## <a name="types-of-operator-procedure"></a>演算子プロシージャの種類  
 演算子プロシージャには、次の種類のいずれかを指定できます。  
  
- 引数が、クラスまたは構造体の型の単項演算子の定義。  
  
- クラスまたは構造体の型の引数の少なくとも 1 つが二項演算子の定義。  
  
- 引数が、クラスまたは構造体の型の変換演算子の定義。  
  
- クラスまたは構造体の型を返す変換演算子の定義。  
  
 変換演算子は、単項では常に、常に使用して`CType`として定義する演算子。  
  
## <a name="declaration-syntax"></a>宣言の構文  
 演算子プロシージャを宣言する構文は次のとおりです。  
  
 `Public Shared`   `[Widening | Narrowing]`   `Operator`  *operatorsymbol*  `(` *operand1*  `[,`  *operand2* `]) As`  *datatype*  
  
 `' Statements of the operator procedure.`  
  
 `End Operator`  
  
 使用する、`Widening`または`Narrowing`型変換演算子でのみキーワード。 演算子記号は常に[CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)型変換演算子。  
  
 二項の演算子を定義する 2 つのオペランドを宣言して、型変換演算子を含む、単項演算子を定義する 1 つのオペランドを宣言します。 すべてのオペランドを宣言する必要があります`ByVal`します。  
  
 各オペランドを宣言すると、同様のパラメーターを宣言する[Sub プロシージャ](./sub-procedures.md)します。  
  
### <a name="data-type"></a>データの種類  
 クラスまたは定義した構造体で演算子を定義しているため、そのクラスまたは構造体のデータ型のオペランドの少なくとも 1 つがあります。 型の変換演算子のオペランドまたは戻り値の型がクラスまたは構造体のデータ型でなければなりません。  
  
 詳細については、次を参照してください。 [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)します。  
  
## <a name="calling-syntax"></a>呼び出し構文  
 演算子プロシージャは、式の中で演算子記号を使用して暗黙的を呼び出します。 定義済みの演算子のと同じ方法で、オペランドを指定します。  
  
 演算子プロシージャへの暗黙の呼び出しの構文は次のとおりです。  
  
 `Dim testStruct As`  *structurename*  
  
 `Dim testNewStruct As`  *structurename*  `= testStruct`  *operatorsymbol*  `10`  
  
### <a name="illustration-of-declaration-and-call"></a>宣言と呼び出しの図  
 次の構造は、構成の上位と下位の要素として 128 ビットの符号付き整数値を格納します。 定義、`+`演算子を 2 つ`veryLong`値し、その結果を生成`veryLong`値。  
  
 [!code-vb[VbVbcnProcedures#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#23)]  
  
 次の例では、一般的な呼び出しを`+`で定義されたオペレーター`veryLong`します。  
  
 [!code-vb[VbVbcnProcedures#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#24)]  

## <a name="see-also"></a>関連項目

- [プロシージャ](./index.md)
- [Sub プロシージャ](./sub-procedures.md)
- [Function プロシージャ](./function-procedures.md)
- [Property プロシージャ](./property-procedures.md)
- [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)
- [Operator ステートメント](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [方法: 演算子を定義します。](./how-to-define-an-operator.md)
- [方法: 変換演算子を定義します。](./how-to-define-a-conversion-operator.md)
- [方法: 演算子プロシージャを呼び出す](./how-to-call-an-operator-procedure.md)
- [方法: 演算子を定義するクラスを使用して、](./how-to-use-a-class-that-defines-operators.md)
