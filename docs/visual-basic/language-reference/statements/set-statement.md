---
title: Set ステートメント
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
ms.openlocfilehash: 75ad6d87f1785fea13a282d953f117c9c234e203
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349566"
---
# <a name="set-statement-visual-basic"></a>Set ステートメント (Visual Basic)
値をプロパティに割り当てるのに使用する `Set` プロパティ プロシージャを宣言します。  
  
## <a name="syntax"></a>構文  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## <a name="parts"></a>指定項目  
 `attributelist`  
 任意。 「[属性リスト](../../../visual-basic/language-reference/statements/attribute-list.md)」を参照してください。  
  
 `accessmodifier`  
 このプロパティの `Get` および `Set` ステートメントのいずれかで、省略可能です。 次のいずれかの値を指定します。  
  
- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
- [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
- `Protected Friend`  
  
 「 [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。  
  
 `value`  
 必須です。 プロパティの新しい値を含むパラメーターです。  
  
 `datatype`  
 `Option Strict` が `On` の場合は必ず指定します。 `value` パラメーターのデータ型。 指定するデータ型は、この `Set` ステートメントが宣言されているプロパティのデータ型と同じである必要があります。  
  
 `statements`  
 任意。 `Set` プロパティ プロシージャが呼び出されたときに実行される 1 つ以上のステートメント。  
  
 `End Set`  
 必須です。 `Set` プロパティ プロシージャの定義を終了します。  
  
## <a name="remarks"></a>Remarks  
 プロパティが `ReadOnly` とマークされている場合を除き、すべてのプロパティには `Set` プロパティ プロシージャが必要です。 `Set` プロシージャは、プロパティの値を設定するために使用します。  
  
 Visual Basic は、プロパティに格納される値が代入ステートメントによって提供されるときに、プロパティの `Set` プロシージャを自動的に呼び出します。  
  
 Visual Basic は、プロパティの割り当て時に `Set` プロシージャにパラメーターを渡します。 `Set` のパラメーターを指定しない場合、統合開発環境 (IDE) では `value` という名前の暗黙的なパラメーターが使用されます。 このパラメーターは、プロパティに割り当てられる値を保持します。 通常はこの値をプライベート ローカル変数に格納し、これは `Get` プロシージャが呼び出されるたびに返されます。  
  
 プロパティ宣言の本体には、[Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)と `End Property` ステートメントの間に、プロパティの `Get` と `Set` のプロシージャのみを含めることができます。 これらのプロシージャ以外のものを格納することはできません。 特に、プロパティの現在の値を格納することはできません。 この値は、プロパティの外部に格納する必要があります。それをいずれかのプロパティ プロシージャの内部に格納した場合、他のプロパティ プロシージャからアクセスできなくなるためです。 通常の方法は、プロパティと同じレベルで宣言された [Private](../../../visual-basic/language-reference/modifiers/private.md) 変数に値を格納することです。 `Set` プロシージャは、適用先のプロパティの内部で定義する必要があります。  
  
 `Set` ステートメントで `accessmodifier` を使用しない限り、`Set` プロシージャは既定で、それを含んでいるプロパティのアクセス レベルに設定されます。  
  
## <a name="rules"></a>ルール  
  
- **混合アクセス レベル。** 読み取り/書き込みプロパティを定義する場合は、必要に応じて、`Get` または `Set` のいずれかのプロシージャに対して異なるアクセス レベルを指定できますが、両方に対して指定することはできません。 この場合、プロシージャのアクセス レベルは、プロパティのアクセス レベルよりも制限されている必要があります。 たとえば、プロパティが `Friend` として宣言されている場合は、`Set` プロシージャを、`Public` ではなく `Private` として宣言できます。  
  
     `WriteOnly` プロパティを定義する場合、`Set` プロシージャはプロパティ全体を表します。 `Set` に対して異なるアクセス レベルを宣言することはできません。それによって、プロパティに 2 つのアクセス レベルが設定されるためです。  
  
## <a name="behavior"></a>動作  
  
- **プロパティ プロシージャからの復帰。** `Set` プロシージャから呼び出し元のコードに返されると、実行は、格納される値を指定したステートメントの後のステートメントから続行されます。  
  
     `Set` プロパティ プロシージャは、[Return ステートメント](../../../visual-basic/language-reference/statements/return-statement.md)または [Exit ステートメント](../../../visual-basic/language-reference/statements/exit-statement.md)のいずれかを使用して返すことができます。  
  
     `Exit Property` および `Return` ステートメントでは、プロパティ プロシージャがすぐに終了します。 任意の数の `Exit Property` および `Return` ステートメントをプロシージャ内の任意の場所に記述でき、`Exit Property` ステートメントと `Return` ステートメントを混在させることができます。  
  
## <a name="example"></a>例  
 次の例では、`Set` ステートメントを使用してプロパティの値を設定します。  
  
 [!code-vb[VbVbalrStatements#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#55)]  
  
## <a name="see-also"></a>関連項目

- [Get ステートメント](../../../visual-basic/language-reference/statements/get-statement.md)
- [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)
- [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Property プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
