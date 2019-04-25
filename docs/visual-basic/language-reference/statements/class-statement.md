---
title: Class ステートメント (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Class
helpviewer_keywords:
- class modules
- Class statement [Visual Basic]
- classes [Visual Basic], fields
- fields [Visual Basic], of classes
- class types [Visual Basic], class statements
- classes [Visual Basic], creating
- classes [Visual Basic], data members
- data members [Visual Basic], of classes
ms.assetid: f2664f38-eb5a-4d4b-a374-1d041521fb6c
ms.openlocfilehash: 68401571645d77a41b827c13b3cfc3674076e218
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58824573"
---
# <a name="class-statement-visual-basic"></a>Class ステートメント (Visual Basic)
クラスの名前を宣言し、変数、プロパティ、イベント、およびクラスを構成するプロシージャの定義を紹介します。  
  
## <a name="syntax"></a>構文  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] [ Partial ] _  
Class name [ ( Of typelist ) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ statements ]  
End Class  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`attributelist`|任意。 参照してください[属性リスト](../../../visual-basic/language-reference/statements/attribute-list.md)します。|  
|`accessmodifier`|任意。 次のいずれかの値を指定します。<br /><br /> -   [Public](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Private](../../../visual-basic/language-reference/modifiers/private.md)<br />-   [Protected Friend](../../language-reference/modifiers/protected-friend.md)<br />- [Private Protected](../../language-reference/modifiers/private-protected.md)<br/><br/> 「 [Visual Basic でのアクセス レベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。|  
|`Shadows`|任意。 参照してください[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)します。|  
|`MustInherit`|省略可能です。 参照してください[MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)します。|  
|`NotInheritable`|省略可能です。 参照してください[NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)します。|  
|`Partial`|省略可能です。 クラスの部分的な定義を示します。 参照してください[部分](../../../visual-basic/language-reference/modifiers/partial.md)します。|  
|`name`|必須。 このクラスの名前。 「 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。|  
|`Of`|省略可能です。 これは、ジェネリック クラスであることを指定します。|  
|`typelist`|使用するかどうかは必ず、[の](../../../visual-basic/language-reference/statements/of-clause.md)キーワード。 このクラスの型パラメーターの一覧。 参照してください[一覧を入力する](../../../visual-basic/language-reference/statements/type-list.md)します。|  
|`Inherits`|省略可能です。 このクラスが別のクラスのメンバーを継承することを示します。 参照してください[Inherits ステートメント](../../../visual-basic/language-reference/statements/inherits-statement.md)します。|  
|`classname`|`Inherits` ステートメントを使用する場合は必ず指定します。 このクラスの派生元クラスの名前。|  
|`Implements`|省略可能です。 このクラスで、1 つまたは複数のインターフェイスのメンバーを実装することを示します。 参照してください[ステートメントを実装](../../../visual-basic/language-reference/statements/implements-statement.md)します。|  
|`interfacenames`|`Implements` ステートメントを使用する場合は必ず指定します。 このクラスが実装するインターフェイスの名前。|  
|`statements`|省略可能です。 このクラスのメンバーを定義するステートメントです。|  
|`End Class`|必須。 `Class` の定義を終了します。|  
  
## <a name="remarks"></a>Remarks  
 A`Class`ステートメントは、新しいデータ型を定義します。 A*クラス*はオブジェクト指向プログラミング (OOP) の基本的な構成要素です。 詳細については、次を参照してください。[オブジェクトとクラス](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)します。  
  
 `Class` は、名前空間またはモジュール レベルでのみ使用できます。 つまり、*宣言コンテキスト*クラスのソース ファイル、名前空間、クラス、構造体、モジュール、またはインターフェイスである必要があります、プロシージャまたはブロックすることはできません。 詳細については、「[宣言コンテキストと既定のアクセス レベル](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)」を参照してください。  
  
 クラスの各インスタンスには、その他のすべてのインスタンスの独立した有効期間があります。 によって作成されるときに、この有効期間が開始されます、 [New 演算子](../../../visual-basic/language-reference/operators/new-operator.md)句またはなどの関数によって<xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>します。 インスタンスを指すすべての変数に設定されている時に終了[Nothing](../../../visual-basic/language-reference/nothing.md)または他のクラスのインスタンスにします。  
  
 クラスの既定値は[フレンド](../../../visual-basic/language-reference/modifiers/friend.md)アクセスします。 アクセス修飾子を使用してこれらのアクセス レベルを調整できます。 詳細については、[ Visual Basic のアクセス レベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)を参照してください。  
  
## <a name="rules"></a>ルール  
  
-   **入れ子にします。** 別の 1 つのクラスを定義できます。 外側のクラス、*クラスを含む*、内部クラスを呼び出すと、*入れ子になったクラス*します。  
  
-   **継承。** クラスを使用している場合、 [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md)、基底クラスまたはインターフェイスの 1 つだけ指定できます。 クラスは、1 つ以上の要素から継承できません。  
  
     クラスより制限の厳しいアクセス レベルを持つ別のクラスから継承できません。 たとえば、`Public`クラスから継承できません、`Friend`クラス。  
  
     クラスは、その中に入れ子になったクラスから継承できません。  
  
-   **実装です。** クラスを使用している場合、 [Implements ステートメント](../../../visual-basic/language-reference/statements/implements-statement.md)で指定したすべてのインターフェイスで定義されたすべてのメンバーを実装する必要があります`interfacenames`します。 この例外は、基底クラスのメンバーの再実装です。 詳細については、「再実装」を参照してください[実装](../../../visual-basic/language-reference/statements/implements-clause.md)します。  
  
-   **既定のプロパティ。** クラスとして最大で 1 つのプロパティを指定できます、*プロパティの既定*します。 詳細については、次を参照してください。[既定](../../../visual-basic/language-reference/modifiers/default.md)します。  
  
## <a name="behavior"></a>動作  
  
-   **アクセス レベルです。** クラス内には、各メンバーを独自のアクセス レベルを宣言できます。 クラス メンバーは既定[パブリック](../../../visual-basic/language-reference/modifiers/public.md)変数および定数を除く、既定のアクセス[プライベート](../../../visual-basic/language-reference/modifiers/private.md)アクセスします。 クラスがそのメンバーの 1 つ以上のアクセスが制限されてよりときに、クラスのアクセス レベルが優先されます。  
  
-   **スコープ。** クラスは、その親名前空間、クラス、構造体、またはモジュール全体にわたってスコープ内で。  
  
     すべてのクラス メンバーのスコープは、クラス全体です。  
  
     **有効期間。** Visual Basic は、静的クラスをサポートしていません。 静的クラスと同等の機能は、モジュールによって提供されます。 詳細については、次を参照してください。[モジュール ステートメント](../../../visual-basic/language-reference/statements/module-statement.md)します。  
  
     クラスのメンバーでは、によって宣言されている方法と場所の有効期間があります。 詳細については、次を参照してください。 [Visual Basic での有効期間](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)します。  
  
-   **パス名です。** クラスの外部のコードでは、そのクラスの名前を持つメンバーの名前を修飾する必要があります。  
  
     入れ子になったクラス内でコードがプログラミング要素に参照を修飾されていない場合、Visual Basic 要素を検索、最初に、含まれるクラスにし、入れ子になったクラスでこれ外側のコンテナー要素にします。  
  
## <a name="classes-and-modules"></a>クラスとモジュール  
 これらの要素がある多くの類似点がいくつかの重要な違いがあります。  
  
-   **用語集。** Visual Basic の以前のバージョンは 2 種類のモジュールを認識:*クラス モジュール*(.cls ファイル) と*標準モジュール*(.bas ファイル)。 現在のバージョンを呼び出す*クラス*と*モジュール*、それぞれします。  
  
-   **共有メンバー。** クラスのメンバーは、共有するかどうか、またはインスタンス メンバーを制御できます。  
  
-   **オブジェクト指向です。** クラスは、オブジェクト指向ですが、モジュールがないです。 クラスの 1 つまたは複数のインスタンスを作成することができます。 詳細については、次を参照してください。[オブジェクトとクラス](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)します。  
  
## <a name="example"></a>例  
 次の例では、`Class`クラスといくつかのメンバーを定義するステートメント。  
  
 [!code-vb[VbVbalrStatements#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#62)]  
  
## <a name="see-also"></a>関連項目

- [クラスとオブジェクト](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [構造体とクラス](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [Interface ステートメント](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Module ステートメント](../../../visual-basic/language-reference/statements/module-statement.md)
- [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)
- [オブジェクトの有効期間:オブジェクトを作成および破棄する方法](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [Visual Basic におけるジェネリック型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [方法: ジェネリック クラスを使用する](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
