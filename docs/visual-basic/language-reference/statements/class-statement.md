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
ms.openlocfilehash: 2e4514686afcbbe0e9ff0b3326c1be212db4f9f8
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005157"
---
# <a name="class-statement-visual-basic"></a>Class ステートメント (Visual Basic)
クラスの名前を宣言し、クラスが構成されている変数、プロパティ、イベント、およびプロシージャの定義を紹介します。  
  
## <a name="syntax"></a>構文  
  
```vb  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] [ Partial ] _  
Class name [ ( Of typelist ) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ statements ]  
End Class  
```  
  
## <a name="parts"></a>指定項目  
  
|項目|定義|  
|---|---|  
|`attributelist`|任意。 参照してください[属性リスト](../../../visual-basic/language-reference/statements/attribute-list.md)します。|  
|`accessmodifier`|任意。 次のいずれかになります。<br /><br /> -   [Public](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)<br />-    の[フレンド](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Private](../../../visual-basic/language-reference/modifiers/private.md)<br />-   [Protected Friend](../../language-reference/modifiers/protected-friend.md)<br />- [プライベート保護](../../language-reference/modifiers/private-protected.md)<br/><br/> 「 [Visual Basic でのアクセス レベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。|  
|`Shadows`|任意。 「[シャドウ](../../../visual-basic/language-reference/modifiers/shadows.md)」を参照してください。|  
|`MustInherit`|任意。 「 [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)」を参照してください。|  
|`NotInheritable`|任意。 「 [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)」を参照してください。|  
|`Partial`|任意。 クラスの部分定義を示します。 「[部分](../../../visual-basic/language-reference/modifiers/partial.md)」を参照してください。|  
|`name`|必須。 このクラスの名前。 「 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。|  
|`Of`|任意。 これがジェネリッククラスであることを指定します。|  
|`typelist`|[Of](../../../visual-basic/language-reference/statements/of-clause.md)キーワードを使用する場合は必須です。 このクラスの型パラメーターのリスト。 [型リスト](../../../visual-basic/language-reference/statements/type-list.md)を参照してください。|  
|`Inherits`|任意。 このクラスが別のクラスのメンバーを継承することを示します。 「 [Inherits ステートメント](../../../visual-basic/language-reference/statements/inherits-statement.md)」を参照してください。|  
|`classname`|`Inherits` ステートメントを使用する場合は必ず指定します。 このクラスの派生元であるクラスの名前。|  
|`Implements`|任意。 このクラスが1つ以上のインターフェイスのメンバーを実装することを示します。 「 [Implements ステートメント](../../../visual-basic/language-reference/statements/implements-statement.md)」を参照してください。|  
|`interfacenames`|`Implements` ステートメントを使用する場合は必ず指定します。 このクラスが実装するインターフェイスの名前。|  
|`statements`|任意。 このクラスのメンバーを定義するステートメント。|  
|`End Class`|必須。 `Class` の定義を終了します。|  
  
## <a name="remarks"></a>コメント  
 @No__t-0 ステートメントでは、新しいデータ型を定義します。 *クラス*は、オブジェクト指向プログラミング (OOP) の基本的な構成要素です。 詳細については、「[オブジェクトとクラス](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)」を参照してください。  
  
 `Class` は、名前空間またはモジュール レベルでのみ使用できます。 つまり、クラスの*宣言コンテキスト*は、ソースファイル、名前空間、クラス、構造体、モジュール、またはインターフェイスである必要があり、プロシージャまたはブロックにすることはできません。 詳細については、「[宣言コンテキストと既定のアクセス レベル](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)」を参照してください。  
  
 クラスの各インスタンスは、他のすべてのインスタンスとは独立した有効期間を持ちます。 この有効期間は、[新しい Operator](../../../visual-basic/language-reference/operators/new-operator.md)句または <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A> などの関数によって作成されたときに開始されます。 インスタンスを指すすべての変数が[Nothing](../../../visual-basic/language-reference/nothing.md)または他のクラスのインスタンスに設定されている場合に終了します。  
  
 クラスは既定で[フレンド](../../../visual-basic/language-reference/modifiers/friend.md)アクセスになります。 アクセス修飾子を使用してこれらのアクセス レベルを調整できます。 詳細については、[ Visual Basic のアクセス レベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)を参照してください。  
  
## <a name="rules"></a>ルール  
  
- **巣.** 1つのクラスを別のクラス内で定義できます。 外側のクラスは、含んでいる*クラス*と呼ばれ、内側のクラスは*入れ子になったクラス*と呼ばれます。  
  
- **継承。** クラスが[Inherits ステートメント](../../../visual-basic/language-reference/statements/inherits-statement.md)を使用する場合、指定できる基底クラスまたはインターフェイスは1つだけです。 クラスは、複数の要素から継承することはできません。  
  
     クラスは、より制限の厳しいアクセスレベルを持つ別のクラスから継承することはできません。 たとえば、`Public` クラスは、`Friend` クラスから継承することはできません。  
  
     クラスは、入れ子にされたクラスから継承することはできません。  
  
- **ション.** クラスで[Implements ステートメント](../../../visual-basic/language-reference/statements/implements-statement.md)を使用する場合は、`interfacenames` で指定したすべてのインターフェイスで定義されているすべてのメンバーを実装する必要があります。 この例外は、基底クラスのメンバーの再実装です。 詳細については、「 [Implements](../../../visual-basic/language-reference/statements/implements-clause.md)」の「再実装」を参照してください。  
  
- **既定のプロパティ。** クラスは、*既定のプロパティ*として最大で1つのプロパティを指定できます。 詳細については、「 [Default](../../../visual-basic/language-reference/modifiers/default.md)」を参照してください。  
  
## <a name="behavior"></a>動作  
  
- **アクセス レベル。** クラス内では、各メンバーを独自のアクセスレベルで宣言できます。 クラスメンバーの既定の[パブリック](../../../visual-basic/language-reference/modifiers/public.md)アクセスは、変数と定数を除き、既定で[プライベート](../../../visual-basic/language-reference/modifiers/private.md)アクセスになります。 クラスのメンバーの1つよりもアクセスが制限されている場合は、クラスのアクセスレベルが優先されます。  
  
- **検索.** クラスは、名前空間、クラス、構造体、またはモジュールを含んでいる範囲内にあります。  
  
     すべてのクラスメンバーのスコープは、クラス全体です。  
  
     **最短.** Visual Basic は、静的クラスをサポートしていません。 静的クラスに相当する機能は、モジュールによって提供されます。 詳細については、「 [Module ステートメント](../../../visual-basic/language-reference/statements/module-statement.md)」を参照してください。  
  
     クラスメンバーの有効期間は、どのように宣言されているかによって異なります。 詳細については、「 [Visual Basic の有効期間](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)」を参照してください。  
  
- **修飾。** クラスの外部のコードでは、メンバーの名前をそのクラスの名前で修飾する必要があります。  
  
     入れ子になったクラス内のコードがプログラミング要素への修飾されていない参照を作成する場合、Visual Basic は、入れ子になったクラスで最初に要素を検索し、次にそれを含んでいるクラスの要素を検索します。  
  
## <a name="classes-and-modules"></a>クラスとモジュール  
 これらの要素には多くの類似点がありますが、重要な相違点もいくつかあります。  
  
- **関する.** 以前のバージョンの Visual Basic では、*クラスモジュール*(cls ファイル) と*標準モジュール*(.bas ファイル) という2種類のモジュールが認識されています。 現在のバージョンは、これらの*クラス*と*モジュール*をそれぞれ呼び出します。  
  
- **共有メンバー。** クラスのメンバーが共有メンバーまたはインスタンスメンバーであるかどうかを制御できます。  
  
- **オブジェクトの向き。** クラスはオブジェクト指向ですが、モジュールはそうではありません。 クラスの1つ以上のインスタンスを作成できます。 詳細については、「[オブジェクトとクラス](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例では、@no__t 0 のステートメントを使用して、クラスと複数のメンバーを定義しています。  
  
 [!code-vb[VbVbalrStatements#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#62)]  
  
## <a name="see-also"></a>関連項目

- [クラスとオブジェクト](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [構造体とクラス](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [Interface ステートメント](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Module ステートメント](../../../visual-basic/language-reference/statements/module-statement.md)
- [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)
- [ オブジェクトの有効期間:オブジェクトの作成と破棄の方法 @ no__t-0
- [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [2 つのオブジェクトが等しいかどうかをテストする方法ジェネリック クラスを使用する](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
