---
title: 演算子 - C# プログラミング ガイド
ms.custom: seodec18
ms.date: 04/30/2019
helpviewer_keywords:
- operators [C#]
- C# language, operators
- operators [C#], about operators
ms.assetid: 214e7b83-1a41-4f7c-9867-64e9c0bab39f
ms.openlocfilehash: fd10999066f599d819ef188e09028c64c6a5e9e6
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/06/2019
ms.locfileid: "65064053"
---
# <a name="operators-c-programming-guide"></a>演算子 (C# プログラミング ガイド)

C# では、 *演算子* は式またはステートメントの中で 1 つ以上の *オペランド* に適用されるプログラム要素です。 インクリメント演算子 (`++`) や `new`など、1 つのオペランドを受け取る演算子を *単項* 演算子と言います。 算術演算子 (`+`、`-`、`*`、`/`) など、2 つのオペランドを受け取る演算子を *二項* 演算子と言います。 条件演算子 (`?:`) は、3 つのオペランドを受け取る、C# でただ 1 つの三項演算子です。  
  
 次の C# ステートメントには、1 つの単項演算子と 1 つのオペランドがあります。 インクリメント演算子 `++`は、オペランド `y`の値を変更します。  
  
 [!code-csharp[csProgGuideStatements#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#5)]  
  
 次の C# ステートメントには、それぞれ 2 つのオペランドを持つ 2 つの二項演算子があります。 代入演算子 `=`には、オペランドとして整数の変数 `y` と式 `2 + 3` が含まれています。 式 `2 + 3` 自体も、加算演算子と、2 つのオペランド ( `2` と `3`) で構成されています。  
  
 [!code-csharp[csProgGuideStatements#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#6)]  
  
オペランドは、任意の長さのコードで構成される有効な式で、任意の数の副次式を含むことができます。 複数の演算子を含む式の場合、演算子が適用される順序は *演算子の優先順位*、 *結合規則*、およびかっこによって決定されます。  

## <a name="operator-precedence"></a>演算子の優先順位
  
各演算子には優先順位が定義されています。 優先順位のレベルが異なる複数の演算子を含む式の場合、演算子の優先順位によって演算子が評価される順序が決定されます。 たとえば、次のステートメントでは `n1` に 3 が代入されます。

```csharp
n1 = 11 - 2 * 4;
```

乗算は減算よりも優先順位が高いため、最初に乗算が実行されます。

優先度順に並べられた C# 演算子の完全な一覧については、「[C# 演算子](../../language-reference/operators/index.md)」を参照してください。
  
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

カスタム クラスやカスタム構造体では、特定の演算子の動作を定義できます。 このプロセスは *演算子のオーバーロード*と呼ばれます。 詳細については、[オーバーロード可能な演算子](../../language-reference/keywords/operator.md)に関する記事と [operator](overloadable-operators.md) キーワードに関する記事を参照してください。
  
## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../index.md)
- [ステートメント、式、および演算子](index.md)
- [C# 演算子](../../language-reference/operators/index.md)
- [演算子のキーワード](../../language-reference/keywords/operator-keywords.md)
