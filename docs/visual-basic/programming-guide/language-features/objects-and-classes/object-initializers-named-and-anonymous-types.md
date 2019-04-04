---
title: オブジェクト初期化子:名前付きの匿名型 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ObjectInitializer
helpviewer_keywords:
- object initializers [Visual Basic]
- anonymous types [Visual Basic], object initializers
- initializing properties [Visual Basic]
- initializers [Visual Basic]
- named types [Visual Basic]
ms.assetid: e2df3807-a70f-49dd-ac94-f1e07f472b1b
ms.openlocfilehash: 6602a68555e37bf793ba41076ba8f484b4a0dbc3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821371"
---
# <a name="object-initializers-named-and-anonymous-types-visual-basic"></a>オブジェクト初期化子:名前付きの匿名型 (Visual Basic)
オブジェクト初期化子を使用すると、1 つの式を使用して複雑なオブジェクトのプロパティを指定できます。 これらは、匿名型の名前付きの型のインスタンスを作成する使用できます。  
  
## <a name="declarations"></a>宣言  
 名前付きの匿名型のインスタンスの宣言はほぼ同じで、確認できますが、その影響が同じではありません。 各カテゴリは、独自の機能と制限があります。 次の例は、宣言し、名前付きクラスのインスタンスを初期化するための便利な方法を示しています。 `Customer`、オブジェクト初期化子リストを使用しています。 キーワードの後に、クラスの名前が指定されていることを確認`New`します。  
  
 [!code-vb[VbVbalrObjectInit#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#1)]  
  
 匿名型には、使用可能な名前がありません。 そのため、匿名型のインスタンス化では、クラス名を含めることはできません。  
  
 [!code-vb[VbVbalrObjectInit#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#2)]  
  
 要件および 2 つの宣言の結果は同じです。 `namedCust`、`Customer`を持つクラス、`Name`プロパティは既に存在する必要があります、および宣言は、そのクラスのインスタンスを作成します。 `anonymousCust`、コンパイラは、1 つのプロパティと呼ばれる文字列が含まれる新しいクラスを定義します。 `Name`、し、そのクラスの新しいインスタンスを作成します。  
  
## <a name="named-types"></a>名前付きの型  
 オブジェクト初期化子は、型のコンス トラクターを呼び出すし、単一のステートメントでの一部またはすべてのプロパティの値を設定する簡単な方法を提供します。 コンパイラは、ステートメントの適切なコンス トラクターを呼び出します。 既定のコンス トラクターの引数が何も表示されない場合、または 1 つまたは複数の引数が送信される場合にパラメーター化されたコンス トラクター。 その後、指定したプロパティは、初期化子リストに記載された順序で初期化されます。  
  
 各初期化子リストの初期化は、クラスのメンバーに、初期値の割り当てで構成されます。 クラスが定義されている場合、名前とメンバーのデータ型が決定されます。 次の例では、`Customer`クラスが存在する必要があります、およびがメンバーという名前の必要があります`Name`と`City`文字列値を受け入れることができます。  
  
 [!code-vb[VbVbalrObjectInit#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#3)]  
  
 または、次のコードを使用して同じ結果を取得できます。  
  
 [!code-vb[VbVbalrObjectInit#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#4)]  
  
 これらの各宣言には、次の例は、作成に相当する`Customer`既定のコンス トラクターを使用して、オブジェクトし、の初期値を指定し、`Name`と`City`プロパティを使用して、 `With`ステートメント。  
  
 [!code-vb[VbVbalrObjectInit#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#5)]  
  
 場合、`Customer`クラスには、値を送信することができますをパラメーター化されたコンス トラクターが含まれています。 `Name`、なども宣言と初期化、`Customer`次の方法でオブジェクト。  
  
 [!code-vb[VbVbalrObjectInit#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#6)]  
  
 次のコードに示すように、すべてのプロパティを初期化する必要はありません。  
  
 [!code-vb[VbVbalrObjectInit#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#7)]  
  
 ただし、初期化リストを空にすることはできません。 初期化されていないプロパティは、既定値を保持します。  
  
### <a name="type-inference-with-named-types"></a>名前付きの型と型の推論  
 宣言のコードを短く`cust1`オブジェクト初期化子とローカル型推論を組み合わせることで。 これを使用すると、省略、`As`変数の宣言で句。 変数のデータ型は、割り当てによって作成されるオブジェクトの型から推論されます。 次の例では、型で`cust6`は`Customer`します。  
  
 [!code-vb[VbVbalrObjectInit#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#8)]  
  
### <a name="remarks-about-named-types"></a>名前付きの型についての解説  
  
-   クラス メンバーには、オブジェクト初期化子リスト内の 1 つ以上の時間を初期化できません。 宣言`cust7`エラーが発生します。  
  
     [!code-vb[VbVbalrObjectInit#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#9)]  
  
-   メンバーは、それ自体または別のフィールドを初期化するために使用できます。 次の宣言のように、初期化前に、メンバーがアクセスされる場合`cust8`既定値が使用されます。 オブジェクト初期化子を使用する宣言が処理されるときに最初に行われるが、適切なコンス トラクターが呼び出されることに注意してください。 その後、初期化子リスト内の各フィールドが初期化されます。 既定値を次の例で`Name`が割り当てられている`cust8`で初期化の値が割り当てられていると`cust9`します。  
  
     [!code-vb[VbVbalrObjectInit#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#10)]  
  
     次のコードの例では、パラメーター化されたコンス トラクターから`cust3`と`cust4`を宣言して初期化`cust10`と`cust11`します。  
  
     [!code-vb[VbVbalrObjectInit#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#11)]  
  
-   オブジェクト初期化子を入れ子にすることができます。 次の例では、`AddressClass`を 2 つのプロパティを持つクラスは、`City`と`State`、および`Customer`クラスには、`Address`プロパティのインスタンスである`AddressClass`。  
  
     [!code-vb[VbVbalrObjectInit#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#12)]  
  
-   初期化リストを空にすることはできません。  
  
-   初期化されているインスタンスは、Object 型のすることはできません。  
  
-   クラスのメンバーの初期化中には、共有メンバー、読み取り専用メンバー、定数、またはメソッドの呼び出しをすることはできません。  
  
-   クラス メンバーは初期化は、インデックス付きまたは修飾ことはできません。 次の例では、コンパイラ エラーが発生します。  
  
     `'' Not valid.`  
  
     `' Dim c1 = New Customer With {.OrderNumbers(0) = 148662}`  
  
     `' Dim c2 = New Customer with {.Address.City = "Springfield"}`  
  
## <a name="anonymous-types"></a>匿名型  
 匿名型では、オブジェクト初期化子を使用して、明示的に定義していない新しい型と名前のインスタンスを作成します。 代わりに、コンパイラは、オブジェクト初期化子リストにに従って指定するプロパティの型を生成します。 として参照には型の名前が指定されていないため、*匿名型*します。 たとえば、前に次の宣言を比較`cust6`します。  
  
 [!code-vb[VbVbalrObjectInit#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#13)]  
  
 唯一の違いが構文的に後に名前が指定されていないことは`New`データ型。 ただし、動作は大きく異なります。 コンパイラは、2 つのプロパティを持つ新しい匿名型を定義します。`Name`と`City`、値を指定して、そのインスタンスを作成します。 型の推定の種類を決定する`Name`と`City`文字列の例です。  
  
> [!CAUTION]
>  匿名型の名前は、コンパイラによって生成され、コンパイルするたびに異なる場合があります。 コードを使用して、または匿名型の名前に依存する必要がありますされません。  
  
 使用することはできません型の名前が使用できないため、`As`を宣言する句`cust13`します。 型を推論する必要があります。 遅延バインディングを使用しない場合は、ローカル変数に匿名型の使用を制限します。  
  
 匿名型の重大なサポートを提供する[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]クエリ。 クエリで匿名型の使用に関する詳細については、[匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)と[Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)を参照してください。  
  
### <a name="remarks-about-anonymous-types"></a>匿名型についての解説  
  
-   通常、匿名型の宣言内のプロパティのほとんどすべてできるが、キーのプロパティをキーワードを入力して示されている`Key`プロパティ名の前にします。  
  
     [!code-vb[VbVbalrObjectInit#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#14)]  
  
     キー プロパティの詳細については、[キー](../../../../visual-basic/language-reference/modifiers/key.md)を参照してください。  
  
-   このような名前付きの型、初期化子リスト匿名型の定義は、少なくとも 1 つのプロパティを宣言する必要があります。  
  
     [!code-vb[VbVbalrObjectInit#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#2)]  
  
-   匿名型のインスタンスが宣言されている場合、コンパイラは、一致する匿名型の定義を生成します。 名前とプロパティのデータ型はインスタンスの宣言からのものし、定義でコンパイラが含まれます。 プロパティがないという名前し、名前付きの型とは異なり、事前に定義されています。 その型が推論されます。 使用して、プロパティのデータ型を指定することはできません、`As`句。  
  
-   匿名型は、その他のいくつかの方法で、名前とそのプロパティの値を確立できますも。 たとえば、匿名型のプロパティには、名前と、変数、または名前の値と別のオブジェクトのプロパティの値の両方がかかります。  
  
     [!code-vb[VbVbalrObjectInit#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#15)]  
  
     匿名型のプロパティを定義するためのオプションの詳細については、次を参照してください。[方法。匿名型の宣言におけるプロパティ名と型を推論](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)します。  
  
## <a name="see-also"></a>関連項目

- [ローカル型の推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [方法: 匿名型の宣言におけるプロパティ名と型を推論します。](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [Key](../../../../visual-basic/language-reference/modifiers/key.md)
- [方法: オブジェクト初期化子を使用してオブジェクトを宣言します。](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
