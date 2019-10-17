---
title: ReadOnly (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ReadOnly
helpviewer_keywords:
- ReadOnly keyword [Visual Basic]
- variables [Visual Basic], read-only
- ReadOnly property
- properties [Visual Basic], read-only
- read-only variables
ms.assetid: e868185d-6142-4359-a2fd-a7965cadfce8
ms.openlocfilehash: 748c38835cec83cefe54535f90d40ec3a030e4f4
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250389"
---
# <a name="readonly-visual-basic"></a>ReadOnly (Visual Basic)
変数またはプロパティを読み取ることができても書き込まれないことを指定します。  
  
## <a name="remarks"></a>コメント  
  
## <a name="rules"></a>ルール  
  
- **宣言コンテキスト。** `ReadOnly` は、モジュール レベルでのみ使用できます。 つまり、@no__t 0 要素の宣言コンテキストはクラス、構造体、またはモジュールである必要があり、ソースファイル、名前空間、またはプロシージャにすることはできません。  
  
- **結合された修飾子。** 同じ宣言で `Static` と共に @no__t 0 を指定することはできません。  
  
- **値の割り当て。** @No__t-0 プロパティを使用するコードでは、値を設定できません。 ただし、基になるストレージにアクセスできるコードは、いつでも値を割り当てたり、変更したりできます。  
  
     @No__t-0 変数に値を割り当てることができるのは、その宣言または定義されているクラスまたは構造体のコンストラクター内でのみです。  
  
## <a name="when-to-use-a-readonly-variable"></a>ReadOnly 変数を使用する場合  
 [Const ステートメント](../../../visual-basic/language-reference/statements/const-statement.md)を使用して定数値を宣言し、割り当てることができない場合があります。 たとえば、`Const` ステートメントが割り当てようとしているデータ型を受け入れない場合や、コンパイル時に定数式を使用して値を計算できない場合があります。 コンパイル時に値がわからない場合もあります。 このような場合は、定数値を保持するために @no__t 0 の変数を使用できます。  
  
> [!IMPORTANT]
> 変数のデータ型が配列やクラスインスタンスなどの参照型である場合、その変数自体が 0 @no__t であっても、そのメンバーを変更できます。 次に例を示します。  
  
 ```vb
 ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}
 Sub ChangeArrayElement()
     characterArray(1) = "M"c
 End Sub
 ```
  
 初期化されると、`characterArray()` が指す配列は、"x"、"y"、および "z" を保持します。 変数 `characterArray` は `ReadOnly` であるため、初期化後に値を変更することはできません。つまり、新しい配列を割り当てることはできません。 ただし、1つまたは複数の配列メンバーの値を変更できます。 プロシージャの呼び出しの後に `ChangeArrayElement` の場合、@no__t が指す配列は、"x"、"M"、および "z" を保持します。
  
 これは、プロシージャパラメーターを[ByVal](byval.md)に宣言するのと似ています。これにより、プロシージャが呼び出し元の引数自体を変更するのではなく、メンバーを変更することができます。  
  
## <a name="example"></a>例

次の例では、従業員が雇用された日付の `ReadOnly` プロパティを定義します。 クラスは、プロパティ値を @no__t 0 の変数として内部に格納します。クラス内のコードだけがその値を変更できます。 ただし、プロパティは 0 @no__t、クラスにアクセスできるすべてのコードでプロパティを読み取ることができます。
  
[!code-vb[VbVbalrKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#4)]
  
`ReadOnly` 修飾子は、次のコンテキストで使用できます。
  
- [Dim ステートメント](../statements/dim-statement.md) 
- [Property ステートメント](../statements/property-statement.md)  
  
## <a name="see-also"></a>関連項目

- [WriteOnly](writeonly.md)
- [キーワード](../keywords/index.md)
