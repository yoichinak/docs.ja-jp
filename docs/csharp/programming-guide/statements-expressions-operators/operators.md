---
title: 演算子 - C# プログラミング ガイド
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- operators [C#]
- C# language, operators
- operators [C#], about operators
ms.assetid: 214e7b83-1a41-4f7c-9867-64e9c0bab39f
ms.openlocfilehash: 0b2af8c41bc6411d2665d2cf37bd48040fc8d8dc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59307474"
---
# <a name="operators-c-programming-guide"></a>演算子 (C# プログラミング ガイド)

C# では、 *演算子* は式またはステートメントの中で 1 つ以上の *オペランド* に適用されるプログラム要素です。 インクリメント演算子 (`++`) や `new`など、1 つのオペランドを受け取る演算子を *単項* 演算子と言います。 算術演算子 (`+`、`-`、`*`、`/`) など、2 つのオペランドを受け取る演算子を *二項* 演算子と言います。 条件演算子 (`?:`) は、3 つのオペランドを受け取る、C# でただ 1 つの三項演算子です。  
  
 次の C# ステートメントには、1 つの単項演算子と 1 つのオペランドがあります。 インクリメント演算子 `++`は、オペランド `y`の値を変更します。  
  
 [!code-csharp[csProgGuideStatements#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#5)]  
  
 次の C# ステートメントには、それぞれ 2 つのオペランドを持つ 2 つの二項演算子があります。 代入演算子 `=`には、オペランドとして整数の変数 `y` と式 `2 + 3` が含まれています。 式 `2 + 3` 自体も、加算演算子と、2 つのオペランド ( `2` と `3`) で構成されています。  
  
 [!code-csharp[csProgGuideStatements#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#6)]  
  
## <a name="operators-evaluation-and-operator-precedence"></a>演算子、評価、演算子の優先順位

 オペランドは、任意の長さのコードで構成される有効な式で、任意の数の副次式を含むことができます。 複数の演算子を含む式の場合、演算子が適用される順序は *演算子の優先順位*、 *結合規則*、およびかっこによって決定されます。  
  
 各演算子には優先順位が定義されています。 優先順位のレベルが異なる複数の演算子を含む式の場合、演算子の優先順位によって演算子が評価される順序が決定されます。 たとえば、次のステートメントでは `n1`に 3 が代入されます。  
  
 `n1 = 11 - 2 * 4;`  
  
 乗算は減算よりも優先順位が高いため、最初に乗算が実行されます。  
  
 以下の表では、実行する演算の種類を基にして演算子を分類しています。 各カテゴリは、優先順位に従って配列されています。  
  
 **主な演算子**  
  
|正規表現|説明|  
|----------------|-----------------|  
|x[.](../../../csharp/language-reference/operators/member-access-operator.md)y<br /><br /> x?.y|メンバー アクセス。<br /><br /> 条件付きのメンバー アクセス。|  
|f[(x)](../../../csharp/language-reference/operators/invocation-operator.md)|メソッドおよびデリゲートの呼び出し。|  
|a[&#91;x&#93;](../../../csharp/language-reference/operators/index-operator.md)<br /><br /> a?[x]|配列アクセスおよびインデクサー アクセス。<br /><br /> 条件付きの配列アクセスおよびインデクサー アクセス。|  
|x[++](../../../csharp/language-reference/operators/arithmetic-operators.md#increment-operator-)|後置インクリメント。|  
|x[--](../../../csharp/language-reference/operators/arithmetic-operators.md#decrement-operator---)|後置デクリメント。|  
|[new](../../../csharp/language-reference/keywords/new-operator.md) T(...)|オブジェクトおよびデリゲートの作成。|  
|`new` T(...){...}|初期化子を使用したオブジェクトの作成。 「[オブジェクト初期化子とコレクション初期化子](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)」を参照してください。|  
|`new` {...}|匿名オブジェクト初期化子。 「[匿名型](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)」を参照してください。|  
|`new` T[...]|配列の作成。 「[配列](../../../csharp/programming-guide/arrays/index.md)」を参照してください。|  
|[typeof](../../../csharp/language-reference/keywords/typeof.md)(T)|T 型の System.Type オブジェクトを取得します。|  
|[checked](../../../csharp/language-reference/keywords/checked.md)(x)|checked コンテキストで式を評価します。|  
|[unchecked](../../../csharp/language-reference/keywords/unchecked.md)(x)|unchecked コンテキストで式を評価します。|  
|[default](../../../csharp/language-reference/keywords/default.md) (T)|T 型の既定値を取得します。|  
|[delegate](../../../csharp/language-reference/keywords/delegate.md) {}|匿名関数 (匿名メソッド)。|  
  
 **単項演算子**  
  
|正規表現|説明|  
|----------------|-----------------|  
|[+](../../../csharp/language-reference/operators/addition-operator.md)x|同一。|  
|[-](../../../csharp/language-reference/operators/subtraction-operator.md)x|否定。|  
|[\!](../../../csharp/language-reference/operators/boolean-logical-operators.md#logical-negation-operator-)x|論理否定。|  
|[~](../../../csharp/language-reference/operators/bitwise-complement-operator.md)x|ビットごとの否定。|  
|[++](../../../csharp/language-reference/operators/arithmetic-operators.md#increment-operator-)x|前置インクリメント。|  
|[--](../../../csharp/language-reference/operators/arithmetic-operators.md#decrement-operator---)x|前置デクリメント。|  
|[(T)](../../../csharp/language-reference/operators/invocation-operator.md)x|x を明示的に T 型に変換します。|  
  
 **乗算演算子**  
  
|正規表現|説明|  
|----------------|-----------------|  
|[*](../../../csharp/language-reference/operators/arithmetic-operators.md#multiplication-operator-)|乗算|  
|[/](../../../csharp/language-reference/operators/arithmetic-operators.md#division-operator-)|除算記号|  
|[%](../../../csharp/language-reference/operators/arithmetic-operators.md#remainder-operator-)|剰余。|  
  
 **加算演算子**  
  
|正規表現|説明|  
|----------------|-----------------|  
|x [+](../../../csharp/language-reference/operators/addition-operator.md) y|加算、文字列の連結、デリゲートの組み合わせ。|  
|x [-](../../../csharp/language-reference/operators/subtraction-operator.md) y|減算、デリゲートの削除。|  
  
 **シフト演算子**  
  
|正規表現|説明|  
|----------------|-----------------|  
|x [<\<](../../../csharp/language-reference/operators/left-shift-operator.md) y|左シフト。|  
|x [>>](../../../csharp/language-reference/operators/right-shift-operator.md) y|右シフト。|  
  
 **関係演算子と型演算子**  
  
|正規表現|説明|  
|----------------|-----------------|  
|x [\<](../../../csharp/language-reference/operators/less-than-operator.md) y|より小さい|  
|x [>](../../../csharp/language-reference/operators/greater-than-operator.md) y|次の値より大きい|  
|x [\<=](../../../csharp/language-reference/operators/less-than-equal-operator.md) y|以下|  
|x [>=](../../../csharp/language-reference/operators/greater-than-equal-operator.md) y|以上|  
|x [is](../../../csharp/language-reference/keywords/is.md) T|x が T の場合は true を返します。それ以外の場合は false を返します。|  
|x [as](../../../csharp/language-reference/keywords/as.md) T|T として型指定された x を返します。x が T でない場合は null を返します。|  
  
 **等値演算子**  
  
|正規表現|説明|  
|----------------|-----------------|  
|x [==](../../../csharp/language-reference/operators/equality-operators.md#equality-operator-) y|等しい|  
|x [!=](../../../csharp/language-reference/operators/equality-operators.md#inequality-operator-) y|等しくない|  
  
 **論理演算子、条件演算子、Null 演算子**  
  
|カテゴリ|正規表現|説明|  
|--------------|----------------|-----------------|  
|論理 AND|x [&](../../../csharp/language-reference/operators/and-operator.md) y|整数のビットごとの AND、ブール型の論理 AND。|  
|論理 XOR|x [^](../../../csharp/language-reference/operators/xor-operator.md) y|整数のビットごとの XOR、ブール型の論理 XOR|  
|論理 OR|x [&#124;](../../../csharp/language-reference/operators/or-operator.md) y|整数のビットごとの OR、ブール型の論理 OR|  
|条件 AND|x [&&](../../../csharp/language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-) y|x が true の場合にのみ y を評価します。|  
|条件 OR|x [&#124;&#124;](../../../csharp/language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-) y|x が false の場合にのみ y を評価します。|  
|Null 合体演算子|x [??](../../../csharp/language-reference/operators/null-coalescing-operator.md) Y|x が null の場合は y と評価され、それ以外の場合は x と評価されます。|  
|条件|x [?](../../../csharp/language-reference/operators/conditional-operator.md) y : z|x が true の場合は y と評価され、x が false の場合は z と評価されます。|  
  
 **代入演算子と匿名演算子**  
  
|正規表現|説明|  
|----------------|-----------------|  
|[=](../../../csharp/language-reference/operators/assignment-operator.md)|代入|  
|x op= y|複合代入。 サポートされる演算子: [+=](../../../csharp/language-reference/operators/addition-assignment-operator.md)、[-=](../../../csharp/language-reference/operators/subtraction-assignment-operator.md)、[*=](../../../csharp/language-reference/operators/arithmetic-operators.md#compound-assignment)、[/=](../../../csharp/language-reference/operators/arithmetic-operators.md#compound-assignment)、[%=](../../../csharp/language-reference/operators/arithmetic-operators.md#compound-assignment)、[&=](../../../csharp/language-reference/operators/and-assignment-operator.md)、[&#124;=](../../../csharp/language-reference/operators/or-assignment-operator.md)、[^=](../../../csharp/language-reference/operators/xor-assignment-operator.md)、[<\<=](../../../csharp/language-reference/operators/left-shift-assignment-operator.md)、[>>=](../../../csharp/language-reference/operators/right-shift-assignment-operator.md)|  
|(T x) [=>](../../../csharp/language-reference/operators/lambda-operator.md) y|匿名関数 (ラムダ式)|  
  
## <a name="associativity"></a>結合規則

 1 つの式に同じ優先順位の演算子が複数個含まれている場合、それらの演算子は結合規則に基づいて評価されます。 結合規則が左から右の演算子は、左から右に評価されます。 たとえば、 `x * y / z` は `(x * y) / z`と評価されます。 結合規則が右から左の演算子は、右から左に評価されます。 たとえば、代入演算子は結合規則が右から左です。 そうでない場合、次のコードはエラーになります。  
  
```csharp  
int a, b, c;  
c = 1;  
// The following two lines are equivalent.  
a = b = c;  
a = (b = c);  
  
// The following line, which forces left associativity, causes an error.  
//(a = b) = c;  
```  
  
 別の例として、三項演算子 ([?:](../../../csharp/language-reference/operators/conditional-operator.md)) は、結合規則が右から左です。 ほとんどの二項演算子は結合関係が左から右です。  
  
 式に含まれる演算子の結合規則が左から右であっても、右から左であっても、各式のオペランドは初めに左から右に評価されます。 次の例では、演算子とオペランドの評価の順序について示します。  
  
|ステートメント|評価の順序|  
|---------------|-------------------------|  
|`a = b`|a、b、=|  
|`a = b + c`|a、b、c、+、=|  
|`a = b + c * d`|a、b、c、d、*、+、=|  
|`a = b * c + d`|a、b、c、*、d、+、=|  
|`a = b - c + d`|a、b、c、-、d、+、=|  
|`a += b -= c`|a、b、c、-=、+=|  
  
## <a name="adding-parentheses"></a>かっこの追加

 かっこを使用すると、演算子の優先順位と結合規則によって定められた順序を変更できます。 たとえば、 `2 + 3 * 2` は通常、8 と評価されます。乗算演算子の方が加法演算子よりも優先順位が高いからです。 しかし、この式を `(2 + 3) * 2`と記述すると、加算の方が乗算よりも先に評価され、結果は 10 になります。 次の例では、かっこを使用した式での評価の順序について示します。 前の例では、演算子が適用される前にオペランドが評価されていました。  
  
|ステートメント|評価の順序|  
|---------------|-------------------------|  
|`a = (b + c) * d`|a、b、c、+、d、*、=|  
|`a = b - (c + d)`|a、b、c、d、+、-、=|  
|`a = (b + c) * (d - e)`|a、b、c、+、d、e、-、*、=|  
  
## <a name="operator-overloading"></a>演算子のオーバーロード

 カスタム クラスやカスタム構造体では、演算子の動作を変更できます。 このプロセスは *演算子のオーバーロード*と呼ばれます。 詳細については、[オーバーロード可能な演算子](../../../csharp/language-reference/keywords/operator.md)に関する記事および [operator](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md) キーワードに関する記事を参照してください。  
  
## <a name="related-sections"></a>関連項目

 詳細については、「[演算子のキーワード](../../../csharp/language-reference/keywords/operator-keywords.md)」および「[C# 演算子](../../../csharp/language-reference/operators/index.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)
- [ステートメント、式、および演算子](../../../csharp/programming-guide/statements-expressions-operators/index.md)
