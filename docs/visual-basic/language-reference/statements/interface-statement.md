---
title: Interface ステートメント (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Interface
helpviewer_keywords:
- interface statement [Visual Basic]
- interfaces [Visual Basic], interface definition
ms.assetid: 8997af73-bda3-4f79-bd41-ca396b610260
ms.openlocfilehash: f65875caa16bfe00866cc3cd6fd0c0b22b034576
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970533"
---
# <a name="interface-statement-visual-basic"></a>Interface ステートメント (Visual Basic)
インターフェイスの名前を宣言し、インターフェイスに含まれるメンバーの定義を紹介します。  
  
## <a name="syntax"></a>構文  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] _  
Interface name [ ( Of typelist ) ]  
    [ Inherits interfacenames ]  
    [ [ modifiers ] Property membername ]  
    [ [ modifiers ] Function membername ]  
    [ [ modifiers ] Sub membername ]  
    [ [ modifiers ] Event membername ]  
    [ [ modifiers ] Interface membername ]  
    [ [ modifiers ] Class membername ]  
    [ [ modifiers ] Structure membername ]  
End Interface  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`attributelist`|任意。 参照してください[属性リスト](../../../visual-basic/language-reference/statements/attribute-list.md)します。|  
|`accessmodifier`|任意。 次のいずれかの値を指定します。<br /><br /> -   [Public](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Private](../../../visual-basic/language-reference/modifiers/private.md)<br />-  [Protected Friend](../../language-reference/modifiers/protected-friend.md)<br/>- [Private Protected](../../language-reference/modifiers/private-protected.md)<br /><br /> 「 [Visual Basic でのアクセス レベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。|  
|`Shadows`|任意。 参照してください[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)します。|  
|`name`|必須。 このインターフェイスの名前です。 「 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。|  
|`Of`|省略可能です。 これはジェネリック インターフェイスであることを指定します。|  
|`typelist`|使用するかどうかは必ず、[の](../../../visual-basic/language-reference/statements/of-clause.md)キーワード。 このインターフェイスの型パラメーターの一覧。 必要に応じて、型パラメーターごとに宣言できますバリアントを使用して`In`と`Out`ジェネリック修飾子。 参照してください[一覧を入力する](../../../visual-basic/language-reference/statements/type-list.md)します。|  
|`Inherits`|省略可能です。 このインターフェイスが別のインターフェイスまたはインターフェイスのメンバーと属性を継承することを示します。 参照してください[Inherits ステートメント](../../../visual-basic/language-reference/statements/inherits-statement.md)します。|  
|`interfacenames`|`Inherits` ステートメントを使用する場合は必ず指定します。 このインターフェイスの派生元のインターフェイスの名前。|  
|`modifiers`|省略可能です。 定義するインターフェイス メンバーの適切な修飾子。|  
|`Property`|省略可能です。 インターフェイスのメンバーであるプロパティを定義します。|  
|`Function`|省略可能です。 定義、`Function`インターフェイスのメンバーであるプロシージャ。|  
|`Sub`|省略可能です。 定義、`Sub`インターフェイスのメンバーであるプロシージャ。|  
|`Event`|省略可能です。 インターフェイスのメンバーであるイベントを定義します。|  
|`Interface`|省略可能です。 このインターフェイス内で入れ子になったインターフェイスを定義します。 入れ子になったインターフェイスの定義が終了する必要があります、`End Interface`ステートメント。|  
|`Class`|省略可能です。 インターフェイスのメンバーであるクラスを定義します。 クラスの定義が終了する必要があります、`End Class`ステートメント。|  
|`Structure`|省略可能です。 インターフェイスのメンバーである構造を定義します。 構造体のメンバーの定義で終了する必要があります、`End Structure`ステートメント。|  
|`membername`|必要な各プロパティ、プロシージャ、イベント、インターフェイス、クラスまたは構造体、インターフェイスのメンバーとして定義します。 メンバーの名前。|  
|`End Interface`|`Interface` の定義を終了します。|  
  
## <a name="remarks"></a>Remarks  
 *インターフェイス*プロパティとクラスし、構造体にするには、プロシージャが実装できるように、メンバーのセットを定義します。 インターフェイスのメンバーとその内部処理ではない署名だけを定義します。  
  
 クラスまたは構造体、インターフェイスで定義されたすべてのメンバーのコードを指定することで、インターフェイスを実装します。 最後に、アプリケーションは、そのクラスまたは構造体のインスタンスを作成するときに、オブジェクトが存在し、メモリ内で実行します。 詳細については、次を参照してください。[オブジェクトとクラス](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)と[インターフェイス](../../../visual-basic/programming-guide/language-features/interfaces/index.md)します。  
  
 `Interface` は、名前空間またはモジュール レベルでのみ使用できます。 つまり、*宣言コンテキスト*インターフェイスは、ソース ファイル、名前空間、クラス、構造体、モジュール、またはインターフェイスである必要があります、プロシージャまたはブロックすることはできません。 詳細については、「[宣言コンテキストと既定のアクセス レベル](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)」を参照してください。  
  
 インターフェイスの既定値は[フレンド](../../../visual-basic/language-reference/modifiers/friend.md)アクセスします。 アクセス修飾子を使用してこれらのアクセス レベルを調整できます。 詳細については、[ Visual Basic のアクセス レベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)を参照してください。  
  
## <a name="rules"></a>ルール  
  
-   **インターフェイスの入れ子。** 別の 1 つのインターフェイスを定義できます。 外側のインターフェイス、*インターフェイスを含む*、内部インターフェイスを呼び出すと、*入れ子になったインターフェイス*します。  
  
-   **メンバーの宣言。** のみを定義するインターフェイスのメンバーとして、プロパティまたはプロシージャを宣言するときに、*署名*プロパティまたはプロシージャのです。 これには、要素の型 (プロパティまたはプロシージャ)、そのパラメーターとパラメーターの型、および戻り値の型が含まれます。 このため、メンバーの定義はコード、および終端ステートメントなどの 1 行のみを使用して`End Function`または`End Property`インターフェイスが無効です。  
  
     これに対し、列挙体または構造体、または入れ子になったクラスまたはインターフェイスを定義するときに、そのデータ メンバーを含める必要があります。  
  
-   **メンバー修飾子。** モジュールのメンバーを定義するときに、アクセス修飾子を使用することはできませんを指定することも[Shared](../../../visual-basic/language-reference/modifiers/shared.md)またはプロシージャ修飾子を除く[オーバー ロード](../../../visual-basic/language-reference/modifiers/overloads.md)します。 持つメンバーを宣言することができます[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)を使用できます[既定](../../../visual-basic/language-reference/modifiers/default.md)プロパティを定義するときにだけでなく[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)または[WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)します。  
  
-   **継承。** インターフェイスで使用する場合、 [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md)、1 つまたは複数の基底インターフェイスを指定することができます。 同じ名前のメンバーが定義されている場合でも、2 つのインターフェイスから継承できます。 これを行う場合、実装コードは、実装しています。 どのメンバーを指定する名前の修飾を使用する必要があります。  
  
     インターフェイスより制限の厳しいアクセス レベルを持つ別のインターフェイスから継承できません。 たとえば、`Public`インターフェイスから継承することはできません、`Friend`インターフェイス。  
  
     インターフェイスは、内部に入れ子になったインターフェイスから継承できません。  
  
-   **実装です。** クラスを使用する場合、[実装](../../../visual-basic/language-reference/statements/implements-clause.md)ステートメントは、このインターフェイスを実装するために、インターフェイス内で定義されたすべてのメンバーを実装する必要があります。 さらに、各署名実装コードでは、このインターフェイスで定義された対応するシグネチャを正確に一致する必要があります。 ただし、実装コードに含まれるメンバーの名前は、インターフェイスで定義されているメンバー名と一致する必要はありません。  
  
     としてプロシージャを指定できませんクラスは、プロシージャを実装するときに`Shared`します。  
  
-   **既定のプロパティ。** インターフェイスとして最大で 1 つのプロパティを指定できます、*プロパティの既定*プロパティ名を使用しない参照されていることができます。 宣言することでこのようなプロパティを指定する、[既定](../../../visual-basic/language-reference/modifiers/default.md)修飾子。  
  
     つまり、何も継承している場合にのみ、インターフェイスが既定のプロパティを定義できることに注意してください。  
  
## <a name="behavior"></a>動作  
  
-   **アクセス レベルです。** すべてのインターフェイス メンバーが暗黙的が[パブリック](../../../visual-basic/language-reference/modifiers/public.md)アクセスします。 メンバーを定義するときに、アクセス修飾子を使用することはできません。 ただし、インターフェイスを実装するクラスは実装されている各メンバーのアクセス レベルを宣言できます。  
  
     クラスのインスタンスを変数に代入する場合、そのメンバーのアクセス レベルは、変数のデータ型は、基になるインターフェイスまたはクラスを実装するかどうかに依存できます。 次に例を示します。  
  
     [!code-vb[VbVbalrStatements#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#39)]  
  
     を介して、クラス メンバーにアクセスする場合`varAsInterface`、パブリック アクセスを持つすべて。 ただし、を通じてメンバーにアクセスする場合`varAsClass`、`Sub`プロシージャ`doSomething`プライベート アクセスできます。  
  
-   **スコープ。** インターフェイスは、その名前空間、クラス、構造体、またはモジュール全体にわたってスコープ内で。  
  
     すべてのインターフェイス メンバーのスコープは、全体のインターフェイスです。  
  
-   **有効期間。** インターフェイス自体が、有効期間やそのメンバー。 ときに、クラス インターフェイスを実装し、オブジェクトが作成されますのインスタンスとして、クラス、オブジェクトにことが実行されているアプリケーション内で有効期間。 詳細については、「有効期間」を参照してください[クラス ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)します。  
  
## <a name="example"></a>例  
 次の例では、`Interface`という名前のインターフェイスを定義するステートメント`thisInterface`で実装されている必要があります、`Property`ステートメントと`Function`ステートメント。  
  
 [!code-vb[VbVbalrStatements#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#40)]  
  
 なお、`Property`と`Function`ステートメントで終わるブロックを持ち込んでいない`End Property`と`End Function`インターフェイス内で。 このインターフェイスは、そのメンバーのシグネチャのみを定義します。 完全な`Property`と`Function`を実装するクラスで表示されるブロック`thisInterface`します。  
  
## <a name="see-also"></a>関連項目
- [インターフェイス](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
- [Class ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)
- [Module ステートメント](../../../visual-basic/language-reference/statements/module-statement.md)
- [Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)
- [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Visual Basic におけるジェネリック型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [ジェネリック インターフェイスの分散](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
