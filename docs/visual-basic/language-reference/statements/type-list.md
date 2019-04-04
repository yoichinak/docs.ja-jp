---
title: 型リスト (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- StructureConstraint
- vb.StructureConstraint
- ClassConstraint
- vb.ClassConstraint
helpviewer_keywords:
- class constraint
- constraints, Visual Basic generic types
- generic parameters
- generics [Visual Basic], constraints
- generics [Visual Basic], type list
- structure constraint
- constraints, in type parameters
- generics [Visual Basic], generic types
- parameters [Visual Basic], type
- constraints, Structure keyword
- type parameters [Visual Basic], constraints
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- generics [Visual Basic], type parameters
- type parameters
- constraints, Class keyword
ms.assetid: 56db947a-2ae8-40f2-a70a-960764e9d0db
ms.openlocfilehash: d071e59d94e51ca55167983d0ee3098bd5c7dd8f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843631"
---
# <a name="type-list-visual-basic"></a>型リスト (Visual Basic)
指定します、*パラメーター入力*の*ジェネリック*プログラミング要素です。 複数のパラメーターは、コンマで区切られます。 1 つの型パラメーターの構文を次に示します。  
  
## <a name="syntax"></a>構文  
  
```  
[genericmodifier] typename [ As constraintlist ]  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`genericmodifier`|省略可能です。 ジェネリック インターフェイスとデリゲートでのみ使用できます。 型を宣言した共変を使用して、[アウト](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)キーワードまたは反変を使用して、[で](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)キーワード。 「 [共変性と反変性](../../programming-guide/concepts/covariance-contravariance/index.md)を参照してください。|  
|`typename`|必須。 型パラメーターの名前です。 これは、対応する型引数によって提供される定義済みの型によって置き換えられるプレース ホルダーです。|  
|`constraintlist`|省略可能です。 指定できるデータ型を制約する要件の一覧`typename`します。 複数の制約があれば、中かっこで囲みます (`{ }`) をコンマで区切ります。 使用して、制約リストを導入する必要があります、[として](../../../visual-basic/language-reference/statements/as-clause.md)キーワード。 使用する`As`リストの先頭に一度だけです。|  
  
## <a name="remarks"></a>Remarks  
 すべて汎用のプログラミング要素には、少なくとも 1 つの型パラメーターを実行する必要があります。 型パラメーターは、特定の種類のプレース ホルダー (、*構築される要素*) クライアント コードは、ジェネリック型のインスタンスを作成するタイミングを指定します。 ジェネリック クラスを定義、構造体、インターフェイス、プロシージャを委任したりできます。  
  
 ジェネリック型を定義する場合の詳細については、[Visual Basic におけるジェネリック型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)を参照してください。 型パラメーター名の詳細については、[Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)を参照してください。  
  
## <a name="rules"></a>ルール  
  
-   **かっこです。** 型パラメーターのリストを指定する場合は、かっこで囲む必要がありますでリストを導入する必要があります、[の](../../../visual-basic/language-reference/statements/of-clause.md)キーワード。 使用する`Of`リストの先頭に一度だけです。  
  
-   **制約。** 一連の*制約*型のパラメーターは、任意の組み合わせで、次のものを含めることができます。  
  
    -   インターフェイスの任意の数。 指定された型は、この一覧にすべてのインターフェイスを実装する必要があります。  
  
    -   1 つのクラス。 指定された型は、そのクラスから継承する必要があります。  
  
    -   `New` キーワード。 指定された型には、ジェネリック型にアクセスできるパラメーターなしのコンス トラクターを公開する必要があります。 これは、1 つまたは複数のインターフェイスで型パラメーターを制限する場合に便利です。 インターフェイスを実装する型が必ずしも、コンス トラクターを公開し、コンス トラクターのアクセス レベルに応じて、ジェネリック型内のコード可能性へのアクセスします。  
  
    -   いずれか、`Class`キーワードまたは`Structure`キーワード。 `Class`キーワードは、すべての型引数が渡された文字列、配列、またはデリゲートでは、たとえば、参照型であること、またはクラスからオブジェクトが作成されたことを必要とするジェネリック型パラメーターを制約します。 `Structure`キーワードで制約などの構造体、列挙型、または基本データ型をジェネリック型パラメーターに渡されるすべての型引数の値の型である必要があります。 両方を含めることはできません`Class`と`Structure`同じ`constraintlist`します。  
  
     指定された型に含まれるすべての要件を満たす必要があります`constraintlist`します。  
  
     それぞれの型パラメーターの制約は、その他の型パラメーターの制約の依存しません。  
  
## <a name="behavior"></a>動作  
  
-   **コンパイル時の代入。** 汎用のプログラミング要素から構築された型を作成するときに型パラメーターごとに定義された型を指定します。 Visual Basic コンパイラがその指定された型ごとに出現する位置を置換`typename`ジェネリック要素内で。  
  
-   **制約が存在しない場合。** コードがオペレーション コンソールとでサポートされているメンバーに制限されていますが、型パラメーターに対する制約を指定しない場合、 [Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md)その型パラメーター。  
  
## <a name="example"></a>例  
 次の例では、ディクショナリに新しいエントリを追加する関数の骨組みをなど、汎用の dictionary クラスのスケルトン定義を示します。  
  
 [!code-vb[VbVbalrStatements#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#3)]  
  
## <a name="example"></a>例  
 `dictionary`は汎用的で、それを使用するコードから作成できますのさまざまなオブジェクト、同じ機能を持つが、別のデータ型で動作している各します。 次の例は、行のコードを作成する、`dictionary`オブジェクト`String`エントリと`Integer`キー。  
  
 [!code-vb[VbVbalrStatements#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#4)]  
  
## <a name="example"></a>例  
 次の例では、前の例によって生成された同等のスケルトン定義を示します。  
  
 [!code-vb[VbVbalrStatements#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#5)]  
  
## <a name="see-also"></a>関連項目

- [Of](../../../visual-basic/language-reference/statements/of-clause.md)
- [New 演算子](../../../visual-basic/language-reference/operators/new-operator.md)
- [Visual Basic でのアクセス レベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Object 型](../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)
- [Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)
- [方法: ジェネリック クラスを使用する](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [共変性と反変性](../../programming-guide/concepts/covariance-contravariance/index.md)
- [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
