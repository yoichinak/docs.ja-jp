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
ms.openlocfilehash: 0a8d95ffbabf03a0e6c9d88edb28c248b60f3252
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783878"
---
# <a name="set-statement-visual-basic"></a>Set ステートメント (Visual Basic)
宣言を`Set`プロパティ プロシージャのプロパティに値を代入するために使用します。  
  
## <a name="syntax"></a>構文  
  
```  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## <a name="parts"></a>指定項目  
 `attributelist`  
 省略可能です。 参照してください[属性リスト](../../../visual-basic/language-reference/statements/attribute-list.md)します。  
  
 `accessmodifier`  
 1 つだけでは省略可能、`Get`と`Set`このプロパティ内のステートメント。 次のいずれかの値を指定します。  
  
- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
- [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
- `Protected Friend`  
  
 「 [Visual Basic でのアクセス レベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。  
  
 `value`  
 必須。 プロパティの新しい値を含むパラメーターです。  
  
 `datatype`  
 場合に、必ず`Option Strict`は`On`します。 データ型、`value`パラメーター。 指定されたデータ型は、プロパティのデータ型と同じである必要があります、これ`Set`ステートメントが宣言されます。  
  
 `statements`  
 省略可能です。 場合に実行する 1 つまたは複数のステートメント、`Set`プロパティ プロシージャが呼び出されます。  
  
 `End Set`  
 必須。 定義を終了、`Set`プロパティ プロシージャ。  
  
## <a name="remarks"></a>Remarks  
 すべてのプロパティがあります、`Set`プロパティ プロシージャ、プロパティが指定されていない限り`ReadOnly`します。 `Set`プロパティの値を設定する手順を使用します。  
  
 Visual Basic がプロパティを自動的に呼び出します`Set`手順、代入ステートメントは、プロパティに格納される値を提供する場合。  
  
 Visual Basic のパラメーターを渡す、`Set`プロパティ割り当て中にプロシージャ。 パラメーターを指定しない場合`Set`、統合開発環境 (IDE) という名前の暗黙のパラメーターを使用して`value`します。 パラメーターは、プロパティに割り当てられる値を保持します。 通常プライベート ローカル変数にこの値を格納して返すたびに、`Get`プロシージャが呼び出されます。  
  
 プロパティ宣言の本体でのみ、プロパティを含めることができます`Get`と`Set`間で、プロシージャ、 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)と`End Property`ステートメント。 これらのプロシージャ以外のものを格納できません。 具体的には、プロパティの現在の値を格納できません。 に、プロパティ プロシージャのいずれかの内部で保存する場合、その他のプロパティ プロシージャ アクセスできないために、プロパティの外部には、この値を格納する必要があります。 値を格納する通常の方法も、[プライベート](../../../visual-basic/language-reference/modifiers/private.md)プロパティと同じレベルで宣言された変数。 定義する必要があります、`Set`適用されるプロパティ内のプロシージャです。  
  
 `Set`プロシージャの既定値はその包含するプロパティのアクセス レベルを使用しない限り`accessmodifier`で、`Set`ステートメント。  
  
## <a name="rules"></a>ルール  
  
- **混合アクセス レベル。** 必要に応じていずれかの異なるアクセス レベルを指定することができます、読み取り/書き込みプロパティを定義する場合、`Get`または`Set`両方ではなく、プロシージャ。 これを行うと、プロシージャのアクセス レベル、プロパティのアクセス レベルよりもより制限の厳しい場合があります。 例では、プロパティが宣言されている場合、 `Friend`、宣言することができます、`Set`プロシージャ`Private`、なく`Public`します。  
  
     定義する場合、`WriteOnly`プロパティ、`Set`プロシージャは、全体のプロパティを表します。 レベル別のアクセスを宣言することはできません`Set`プロパティの 2 つのアクセス レベルを設定することがあるため、します。  
  
## <a name="behavior"></a>動作  
  
- **プロパティ プロシージャから取得します。** ときに、`Set`実行はプロシージャは、呼び出し元のコードに返す、次の格納される値を提供するステートメントが続行されます。  
  
     `Set` プロパティ プロシージャは、いずれかを使用して返すことができます、 [Return ステートメント](../../../visual-basic/language-reference/statements/return-statement.md)または[Exit ステートメント](../../../visual-basic/language-reference/statements/exit-statement.md)します。  
  
     `Exit Property`と`Return`ステートメントでは、プロパティ プロシージャからすぐに終了します。 任意の数の`Exit Property`と`Return`ステートメントは、手順では、どこでも表示でき、組み合わせることができます`Exit Property`と`Return`ステートメント。  
  
## <a name="example"></a>例  
 次の例では、`Set`プロパティの値を設定するステートメント。  
  
 [!code-vb[VbVbalrStatements#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#55)]  
  
## <a name="see-also"></a>関連項目

- [Get ステートメント](../../../visual-basic/language-reference/statements/get-statement.md)
- [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)
- [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Property プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
