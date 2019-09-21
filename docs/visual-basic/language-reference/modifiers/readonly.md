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
ms.openlocfilehash: 01c441576cb4247933c053f2043296733f99fdeb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965420"
---
# <a name="readonly-visual-basic"></a>ReadOnly (Visual Basic)
変数またはプロパティを読み取ることができても書き込まれないことを指定します。  
  
## <a name="remarks"></a>Remarks  
  
## <a name="rules"></a>ルール  
  
- **宣言コンテキスト。** `ReadOnly` は、モジュール レベルでのみ使用できます。 つまり、 `ReadOnly`要素の宣言コンテキストはクラス、構造体、またはモジュールである必要があり、ソースファイル、名前空間、またはプロシージャにすることはできません。  
  
- **結合された修飾子。** を同じ宣言`ReadOnly`内で`Static`と共に指定することはできません。  
  
- **値の割り当て。** プロパティを使用`ReadOnly`するコードで値を設定することはできません。 ただし、基になるストレージにアクセスできるコードは、いつでも値を割り当てたり、変更したりできます。  
  
     `ReadOnly`変数に値を割り当てることができるのは、その宣言または定義されているクラスまたは構造体のコンストラクター内の変数だけです。  
  
## <a name="when-to-use-a-readonly-variable"></a>ReadOnly 変数を使用する場合  
 [Const ステートメント](../../../visual-basic/language-reference/statements/const-statement.md)を使用して定数値を宣言し、割り当てることができない場合があります。 たとえば、割り当てたい`Const`データ型がステートメントで受け入れられない場合や、コンパイル時に定数式を使用して値を計算できない場合があります。 コンパイル時に値がわからない場合もあります。 このような場合は、変数を`ReadOnly`使用して定数値を保持できます。  
  
> [!IMPORTANT]
> 変数のデータ型が配列やクラスインスタンスなどの参照型である場合、変数自体が`ReadOnly`の場合でも、そのメンバーを変更できます。 次に例を示します。  
  
 `ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}`  
  
 `Sub changeArrayElement()`  
  
 `characterArray(1) = "M"c`  
  
 `End Sub`  
  
 初期化されると、が指す`characterArray()`配列は、"x"、"y"、および "z" を保持します。 変数`characterArray` は`ReadOnly`であるため、初期化後に値を変更することはできません。つまり、新しい配列を割り当てることはできません。 ただし、1つまたは複数の配列メンバーの値を変更できます。 プロシージャ`changeArrayElement`の呼び出しの後、が指す`characterArray()`配列は、"x"、"M"、および "z" を保持します。  
  
 これは、プロシージャパラメーターを[ByVal](../../../visual-basic/language-reference/modifiers/byval.md)に宣言するのと似ています。これにより、プロシージャが呼び出し元の引数自体を変更するのではなく、メンバーを変更することができます。  
  
## <a name="example"></a>例  
 次の例では`ReadOnly` 、従業員が雇用された日付のプロパティを定義します。 クラスは、プロパティ値を`Private`変数として内部に格納します。クラス内のコードだけがその値を変更できます。 ただし、プロパティは`Public`であり、クラスにアクセスできるすべてのコードでプロパティを読み取ることができます。  
  
 [!code-vb[VbVbalrKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#4)]  
  
 `ReadOnly` 修飾子は、次のコンテキストで使用できます。  
  
 [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>関連項目

- [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)
- [キーワード](../../../visual-basic/language-reference/keywords/index.md)
