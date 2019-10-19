---
title: Set ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Set
helpviewer_keywords:
- property procedures [Visual Basic], Set statements
- Set statement [Visual Basic]
- Set statement [Visual Basic], syntax
- write-only properties
- properties [Visual Basic], write-only
ms.assetid: 9ecc27b4-df84-420d-9075-db25455fb3cd
ms.openlocfilehash: cb0dc76d110f3e6a3ea3e74cc0bfb5a669b35396
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583231"
---
# <a name="set-statement-visual-basic"></a>Set ステートメント (Visual Basic)
プロパティに値を割り当てるために使用される `Set` プロパティプロシージャを宣言します。  
  
## <a name="syntax"></a>構文  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## <a name="parts"></a>指定項目  
 `attributelist`  
 省略可能です。 「[属性リスト](../../../visual-basic/language-reference/statements/attribute-list.md)」を参照してください。  
  
 `accessmodifier`  
 このプロパティの `Get` および `Set` ステートメントのうちの1つで、省略可能です。 次のいずれかの値を指定します。  
  
- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
- [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
- `Protected Friend`  
  
 「 [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。  
  
 `value`  
 必須です。 プロパティの新しい値を格納しているパラメーター。  
  
 `datatype`  
 @No__t_0 が `On` の場合は必須です。 @No__t_0 パラメーターのデータ型。 指定するデータ型は、この `Set` ステートメントが宣言されているプロパティのデータ型と同じである必要があります。  
  
 `statements`  
 省略可能です。 @No__t_0 プロパティプロシージャが呼び出されたときに実行される1つ以上のステートメント。  
  
 `End Set`  
 必須です。 @No__t_0 property プロシージャの定義を終了します。  
  
## <a name="remarks"></a>Remarks  
 プロパティが `ReadOnly` としてマークされている場合を除き、すべてのプロパティには `Set` プロパティプロシージャが必要です。 @No__t_0 プロシージャは、プロパティの値を設定するために使用されます。  
  
 Visual Basic は、プロパティに格納される値が代入ステートメントによって提供されるときに、プロパティの `Set` プロシージャを自動的に呼び出します。  
  
 Visual Basic は、プロパティの割り当て時に `Set` プロシージャにパラメーターを渡します。 @No__t_0 のパラメーターを指定しない場合、統合開発環境 (IDE) は `value` という名前の暗黙的なパラメーターを使用します。 パラメーターは、プロパティに割り当てられる値を保持します。 通常、この値はプライベートローカル変数に格納し、`Get` プロシージャが呼び出されるたびに返されます。  
  
 プロパティ宣言の本体には、プロパティの `Get` と、[プロパティステートメント](../../../visual-basic/language-reference/statements/property-statement.md)と `End Property` ステートメントの間の `Set` プロシージャのみを含めることができます。 これらのプロシージャ以外を格納することはできません。 特に、プロパティの現在の値を格納することはできません。 この値はプロパティの外部に格納する必要があります。これは、プロパティプロシージャの内部に格納する場合、他のプロパティプロシージャがアクセスできないためです。 通常の方法では、プロパティと同じレベルで宣言された[プライベート](../../../visual-basic/language-reference/modifiers/private.md)変数に値を格納します。 @No__t_0 プロシージャは、適用先のプロパティ内で定義する必要があります。  
  
 @No__t_2 ステートメントで `accessmodifier` を使用しない限り、`Set` プロシージャの既定値は、それを含むプロパティのアクセスレベルです。  
  
## <a name="rules"></a>ルール  
  
- **混合アクセスレベル。** 読み取り/書き込みプロパティを定義する場合は、必要に応じて、`Get` または `Set` のいずれかのプロシージャに対して異なるアクセスレベルを指定できますが、両方を指定することはできません。 この場合、プロシージャのアクセスレベルは、プロパティのアクセスレベルよりも制限されている必要があります。 たとえば、プロパティが `Friend` として宣言されている場合は、`Set` プロシージャ `Private` を宣言できますが、`Public` は宣言できません。  
  
     @No__t_0 プロパティを定義する場合、`Set` プロシージャはプロパティ全体を表します。 @No__t_0 に対して異なるアクセスレベルを宣言することはできません。これは、プロパティに2つのアクセスレベルが設定されるためです。  
  
## <a name="behavior"></a>動作  
  
- **プロパティプロシージャからを返します。** @No__t_0 プロシージャが呼び出し元のコードに戻ると、格納される値が指定されたステートメントの後で実行が続行されます。  
  
     `Set` プロパティプロシージャは、 [Return ステートメント](../../../visual-basic/language-reference/statements/return-statement.md)または[Exit ステートメント](../../../visual-basic/language-reference/statements/exit-statement.md)のいずれかを使用してを返すことができます。  
  
     @No__t_0 ステートメントおよび `Return` ステートメントでは、プロパティプロシージャがすぐに終了します。 プロシージャ内の任意の場所で任意の数の `Exit Property` および `Return` ステートメントを使用できます。また、`Exit Property` と `Return` のステートメントを混在させることができます。  
  
## <a name="example"></a>例  
 次の例では、`Set` ステートメントを使用して、プロパティの値を設定します。  
  
 [!code-vb[VbVbalrStatements#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#55)]  
  
## <a name="see-also"></a>関連項目

- [Get ステートメント](../../../visual-basic/language-reference/statements/get-statement.md)
- [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)
- [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Property プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
