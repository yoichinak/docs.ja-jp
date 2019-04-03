---
title: Operator ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.operator
helpviewer_keywords:
- operators [Visual Basic]
- procedures [Visual Basic], operator
- Narrowing keyword [Visual Basic], conversion operators
- Visual Basic code, operators
- Widening keyword [Visual Basic], conversion operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- overloaded operators [Visual Basic]
- operator overloading
- operator procedures
- Operator statement [Visual Basic]
- CType function [Visual Basic], Operator statement
ms.assetid: b12ec4af-1ad7-4a17-865b-c5ee96320ae5
ms.openlocfilehash: 184970d33aae4af135153f9d6f6755770bdf84f6
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58818593"
---
# <a name="operator-statement"></a>Operator Statement
演算子記号、オペランド、およびクラスまたは構造体に演算子プロシージャを定義するコードを宣言します。  
  
## <a name="syntax"></a>構文  
  
```  
[ <attrlist> ] Public [ Overloads ] Shared [ Shadows ] [ Widening | Narrowing ]   
Operator operatorsymbol ( operand1 [, operand2 ]) [ As [ <attrlist> ] type ]  
    [ statements ]  
    [ statements ]  
    Return returnvalue  
    [ statements ]  
End Operator  
```  
  
## <a name="parts"></a>指定項目  
 `attrlist`  
 省略可能です。 参照してください[属性リスト](../../../visual-basic/language-reference/statements/attribute-list.md)します。  
  
 `Public`  
 必須。 この演算子プロシージャがあることを示します[パブリック](../../../visual-basic/language-reference/modifiers/public.md)アクセスします。  
  
 `Overloads`  
 省略可能です。 参照してください[オーバー ロード](../../../visual-basic/language-reference/modifiers/overloads.md)します。  
  
 `Shared`  
 必須。 この演算子プロシージャがあることを示します、 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)プロシージャ。  
  
 `Shadows`  
 省略可能です。 参照してください[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)します。  
  
 `Widening`  
 指定しない限り、変換演算子に必要な`Narrowing`します。 この演算子プロシージャを定義することを示します、 [Widening](../../../visual-basic/language-reference/modifiers/widening.md)変換します。 このヘルプ ページでは、「拡大と縮小変換」を参照してください。  
  
 `Narrowing`  
 指定しない限り、変換演算子に必要な`Widening`します。 この演算子プロシージャを定義することを示します、 [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)変換します。 このヘルプ ページでは、「拡大と縮小変換」を参照してください。  
  
 `operatorsymbol`  
 必須。 シンボルまたはこの演算子プロシージャを定義する演算子の識別子。  
  
 `operand1`  
 必須。 名前と 1 つのオペランド (変換演算子を含む)、単項演算子または二項演算子の左側のオペランドの型。  
  
 `operand2`  
 2 項演算子が必要です。 名前と二項演算子の右辺オペランドの型。  
  
 `operand1` `operand2`次の構文と部分があります。  
  
 `[ ByVal ] operandname [ As operandtype ]`  
  
|パーツ|説明|  
|----------|-----------------|  
|`ByVal`|省略可能、ただし引き渡し方法があります[ByVal](../../../visual-basic/language-reference/modifiers/byval.md)します。|  
|`operandname`|必須。 このオペランドを表す変数の名前。 「 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。|  
|`operandtype`|省略可能な場合を除き、`Option Strict`は`On`します。 このオペランドのデータ型。|  
  
 `type`  
 省略可能な場合を除き、`Option Strict`は`On`します。 演算子プロシージャは、値のデータ型を返します。  
  
 `statements`  
 省略可能です。 演算子プロシージャを実行するステートメントのブロックです。  
  
 `returnvalue`  
 必須。 演算子プロシージャが呼び出し元のコードに返す値。  
  
 `End` `Operator`  
 必須。 この演算子プロシージャの定義を終了します。  
  
## <a name="remarks"></a>Remarks  
 使用することができます`Operator`クラスまたは構造体でのみです。 つまり、*宣言コンテキスト*の演算子はソース ファイル、名前空間、モジュール、インターフェイス、プロシージャ、またはブロックすることはできません。 詳細については、「[宣言コンテキストと既定のアクセス レベル](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)」を参照してください。  
  
 すべての演算子である必要があります`Public Shared`します。 指定することはできません`ByRef`、 `Optional`、または`ParamArray`のいずれかのオペランド。  
  
 演算子記号や識別子を使用して、戻り値を保持することはできません。 使用する必要があります、`Return`ステートメント、およびその値を指定する必要があります。 任意の数の`Return`の手順でステートメントは任意の場所が表示されます。  
  
 この方法で、演算子を定義すると呼びます*演算子のオーバー ロード*を使用するかどうかを`Overloads`キーワード。 定義可能な演算子を次の表に示します。  
  
|型|演算子|  
|----------|---------------|  
|単項|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|  
|2 項|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`|  
|変換 (単項)|`CType`|  
  
 なお、`=`バイナリの一覧で演算子は、比較演算子、代入演算子ではありません。  
  
 定義するときに`CType`、いずれかを指定する必要があります`Widening`または`Narrowing`します。  
  
## <a name="matched-pairs"></a>一致するペア  
 一致するペアとして、特定の演算子を定義する必要があります。 このようなペアのいずれかの演算子を定義する場合に、他にもを定義する必要があります。 一致するペア以下のとおりです。  
  
-   `=` および `<>`  
  
-   `>` および `<`  
  
-   `>=` および `<=`  
  
-   `IsTrue` および `IsFalse`  
  
## <a name="data-type-restrictions"></a>データの種類の制限  
 定義するすべてのオペレーターを定義するクラスまたは構造体が含まれる必要があります。 つまり、クラスまたは構造体は、次のデータ型として表示する必要があります。  
  
-   単項演算子のオペランド。  
  
-   少なくとも 1 つの二項演算子のオペランド。  
  
-   オペランドまたは変換演算子の戻り値の型。  
  
 特定の演算子がある追加のデータ型の制限を次のようにします。  
  
-   定義する場合、`IsTrue`と`IsFalse`演算子を返す必要がある両方の`Boolean`型。  
  
-   定義する場合、`<<`と`>>`演算子、それら両方を指定してください、`Integer`の入力、`operandtype`の`operand2`します。  
  
 戻り値の型をいずれかのオペランドの型に対応する必要はありません。 などの比較演算子など`=`または`<>`返せる`Boolean`場合でも、どちらのオペランドが`Boolean`。  
  
## <a name="logical-and-bitwise-operators"></a>論理演算子とビット処理演算子  
 `And`、 `Or`、 `Not`、および`Xor`演算子は、Visual Basic で論理またはビットごとのいずれかの操作を実行できます。 ただし、クラスまたは構造体でこれらの演算子のいずれかを定義する場合は、そのビットごとの演算のみを定義できます。  
  
 定義することはできません、`AndAlso`演算子と直接、`Operator`ステートメント。 ただし、使用することができます`AndAlso`次の条件を満たしている場合。  
  
-   定義した`And`に使用する同じオペランドの型で`AndAlso`します。  
  
-   定義`And`を定義したクラスまたは構造体と同じ型を返します。  
  
-   定義した、`IsFalse`演算子を定義したクラスまたは構造体に対して`And`します。  
  
 同様に、使用`OrElse`定義している場合`Or`同じのオペランドに対して、クラスや構造体の戻り値の型が定義されている`IsTrue`クラスまたは構造体にします。  
  
## <a name="widening-and-narrowing-conversions"></a>Widening and Narrowing Conversions  
 A*拡大変換*、実行時に常に成功したときに、*縮小変換*実行時に失敗することができます。 詳細については、「 [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)」を参照してください。  
  
 変換のプロシージャを宣言する場合`Widening`プロシージャのコードはエラーを生成する必要があります。 これは、次のことを意味します。  
  
-   型の有効な値を返す必要が常に`type`します。  
  
-   すべての例外とその他のエラー条件に対応する必要があります。  
  
-   これは、呼び出したプロシージャから返されたエラーを処理する必要があります。  
  
 変換の手順が成功しない可能性があります、ある可能性がある、またはその it ハンドルされない例外が発生する可能性がありますを宣言する必要があります`Narrowing`します。  
  
## <a name="example"></a>例  
 次のコード例では、`Operator`演算子する手順について説明する構造体のアウトラインを定義するステートメント、 `And`、 `Or`、 `IsFalse`、および`IsTrue`演算子。 `And` `Or`型の 2 つのオペランドを受け取る各`abc`型を返すと`abc`します。 `IsFalse` `IsTrue`それぞれ型の 1 つのオペランドを受け取ります`abc`戻って`Boolean`します。 これらの定義を使用して、呼び出し元のコードを許可する`And`、 `AndAlso`、 `Or`、および`OrElse`型のオペランドで`abc`します。  
  
 [!code-vb[VbVbalrStatements#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#44)]  
  
## <a name="see-also"></a>関連項目

- [IsFalse 演算子](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [IsTrue 演算子](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [Widening](../../../visual-basic/language-reference/modifiers/widening.md)
- [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)
- [拡大変換と縮小変換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [方法: 演算子を定義します。](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [方法: 変換演算子を定義します。](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [方法: 演算子プロシージャを呼び出す](../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-operator-procedure.md)
- [方法: 演算子を定義するクラスを使用して、](../../../visual-basic/programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)
