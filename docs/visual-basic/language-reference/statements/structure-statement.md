---
title: Structure ステートメント (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Structure
- Structure
helpviewer_keywords:
- user-defined types [Visual Basic], Structure statement
- compound data types [Visual Basic]
- Structure keyword [Visual Basic]
- Structure statement [Visual Basic]
- UDT (user-defined types)
- types [Visual Basic], user-defined
ms.assetid: 9bd1deea-2a89-4cdc-812c-6dcbb947c391
ms.openlocfilehash: ab446319a9e0ef295387d0d6768e813a158939c9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58828359"
---
# <a name="structure-statement"></a>Structure ステートメント
構造体の名前を宣言し、構造体を構成する変数、プロパティ、イベント、およびプロシージャの定義を提供します。  
  
## <a name="syntax"></a>構文  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Partial ] _  
Structure name [ ( Of typelist ) ]  
    [ Implements interfacenames ]  
    [ datamemberdeclarations ]  
    [ methodmemberdeclarations ]  
End Structure  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`attributelist`|任意。 参照してください[属性リスト](../../../visual-basic/language-reference/statements/attribute-list.md)します。|  
|`accessmodifier`|任意。 次のいずれかの値を指定します。<br /><br /> -   [Public](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Private](../../../visual-basic/language-reference/modifiers/private.md)<br />- [Protected Friend](../../language-reference/modifiers/protected-friend.md)<br/>- [Private Protected](../../language-reference/modifiers/private-protected.md) <br /><br /> 「 [Visual Basic でのアクセス レベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。|  
|`Shadows`|任意。 参照してください[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)します。|  
|`Partial`|省略可能です。 構造体の部分定義を示します。 参照してください[部分](../../../visual-basic/language-reference/modifiers/partial.md)します。|  
|`name`|必須。 この構造体の名前です。 「 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。|  
|`Of`|省略可能です。 これがジェネリックな構造体であることを指定します。|  
|`typelist`|使用するかどうかは必ず、[の](../../../visual-basic/language-reference/statements/of-clause.md)キーワード。 この構造体の型パラメーター リストを指定します。 参照してください[一覧を入力する](../../../visual-basic/language-reference/statements/type-list.md)します。|  
|`Implements`|省略可能です。 この構造体が、複数のインターフェイスのメンバーを実装していることを示します。 参照してください[ステートメントを実装](../../../visual-basic/language-reference/statements/implements-statement.md)します。|  
|`interfacenames`|`Implements` ステートメントを使用する場合は必ず指定します。 この構造体が実装するインターフェイスの名前を指定します。|  
|`datamemberdeclarations`|必須。 0 個以上`Const`、 `Dim`、 `Enum`、または`Event`宣言ステートメント*データ メンバー*構造体の。|  
|`methodmemberdeclarations`|省略可能です。 0 個以上の宣言の`Function`、 `Operator`、 `Property`、または`Sub`として機能する手順、*メソッド メンバー*構造体の。|  
|`End Structure`|必須。 `Structure` の定義を終了します。|  
  
## <a name="remarks"></a>Remarks  
 `Structure` ステートメントは、カスタマイズできる複合値型を定義します。 A*構造*以前のバージョンの Visual Basic のユーザー定義型 (UDT) を拡張します。 詳細については、次を参照してください。[構造](../../../visual-basic/programming-guide/language-features/data-types/structures.md)します。  
  
 構造体は、クラスと同じ機能の多くをサポートします。 たとえば、構造体は、プロパティやプロシージャを持つことができ、インターフェイスを実装でき、パラメーター化されたコンストラクターを持つことができます。 ただし、継承、宣言、および使用方法に関しては、構造体とクラスの間には大きな違いがあります。 また、クラスは参照型ですが、構造体は値型です。 詳細については、次を参照してください。[構造体とクラス](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)します。  
  
 `Structure` は、名前空間またはモジュール レベルでのみ使用できます。 つまり、*宣言コンテキスト*構造体は、ソース ファイル、名前空間、クラス、構造体、モジュール、またはインターフェイスである必要があります、プロシージャまたはブロックすることはできません。 詳細については、「[宣言コンテキストと既定のアクセス レベル](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)」を参照してください。  
  
 既定で構造[フレンド](../../../visual-basic/language-reference/modifiers/friend.md)アクセスします。 アクセス修飾子を使用してこれらのアクセス レベルを調整できます。 詳細については、[ Visual Basic のアクセス レベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)を参照してください。  
  
## <a name="rules"></a>ルール  
  
-   **入れ子にします。** 構造体の内部に別の構造体を定義できます。 外側の構造体が呼び出されます、*構造体を含む*、内部構造を呼び出すと、*構造を入れ子になった*。 ただし、包含構造体をとおして入れ子構造体のメンバーにアクセスすることはできません。 入れ子構造体のメンバーにアクセスするには、入れ子構造体のデータ型の変数を宣言する必要があります。  
  
-   **メンバーの宣言。** 構造体のすべてのメンバーを宣言する必要があります。 構造体のメンバーにすることはできません[Protected](../../../visual-basic/language-reference/modifiers/protected.md)または`Protected Friend`のため、構造体からは何も継承します。 ただし、構造体そのものを`Protected` または `Protected Friend` にすることはできます。  
  
     0 個または 1 つ以上の非共有変数または非共有の非カスタム イベントを構造体内で宣言することができます。 非共有ではあっても、定数、プロパティ、およびプロシージャだけを宣言することはできません。  
  
-   **初期化します。** 構造体の非共有データ メンバーの値を宣言の一部として初期化することはできません。 構造体のパラメーター化されたコンストラクターを使ってそのようなデータ メンバーを初期化するか、または構造体のインスタンスを作成した後にメンバーに値を割り当てる必要があります。  
  
-   **継承。** 構造体は、<xref:System.ValueType> 以外の型を継承できません。すべての構造体が、この型を継承します。 特に、構造体は別の構造体を継承できません。  
  
     使用することはできません、 [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md)構造体の定義を指定するも<xref:System.ValueType>します。  
  
-   **実装です。** 構造体で使用する場合、 [Implements ステートメント](../../../visual-basic/language-reference/statements/implements-statement.md)で指定したすべてのインターフェイスで定義されたすべてのメンバーを実装する必要があります`interfacenames`します。  
  
-   **既定のプロパティ。** 構造体として最大で 1 つのプロパティを指定できます、*プロパティの既定*を使用して、[既定](../../../visual-basic/language-reference/modifiers/default.md)修飾子。 詳細については、次を参照してください。[既定](../../../visual-basic/language-reference/modifiers/default.md)します。  
  
## <a name="behavior"></a>動作  
  
-   **アクセス レベルです。** 構造体の内部では、各メンバーを独自のアクセス レベルで宣言できます。 既定ですべての構造体メンバー[パブリック](../../../visual-basic/language-reference/modifiers/public.md)アクセスします。 構造体そのものにこれより厳しいアクセス レベルを指定した場合は、たとえアクセス修飾子を使ってメンバーのアクセス レベルを調整していても、メンバーへのアクセスが自動的に制限されることに注意してください。  
  
-   **スコープ。** 構造体は、そこに含まれる名前空間、クラス、構造体、またはモジュールをスコープとします。  
  
     すべての構造体メンバーのスコープは、構造体全体になります。  
  
-   **有効期間。** 構造体に有効期間はありません。 ただし、構造体の各インスタンスには、他のインスタンスに依存しない独自の有効期間があります。  
  
     インスタンスの有効期間の開始によって作成されるときに、 [New 演算子](../../../visual-basic/language-reference/operators/new-operator.md)句。 インスタンスに含まれる変数の有効期間が終わった時点で、そのインスタンスの有効期間は終わります。  
  
     構造体インスタンスの有効期間を延長することはできません。 静的構造体に相当する機能は、モジュールに用意されています。 詳細については、次を参照してください。[モジュール ステートメント](../../../visual-basic/language-reference/statements/module-statement.md)します。  
  
     構造体メンバーの有効期間は、それを宣言する方法と場所で決まります。 詳細については、「有効期間」を参照してください[クラス ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)します。  
  
-   **パス名です。** 構造体の外部にあるコードでは、メンバーの名前をその構造体の名前で修飾する必要があります。  
  
     入れ子構造体の内部のコードでプログラミング要素を修飾なしで参照した場合、Visual Basic はその要素をまず入れ子構造体の内部で探し、その次にコンテナー構造体の内部で探します。この手順が、最も外側のコンテナー要素にまで繰り返されます。 詳細については、「 [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)」を参照してください。  
  
-   **メモリ使用量。**  他のすべての複合データ型と同様に、構造体の総メモリ使用量を計算する場合、各メンバーのストレージ割り当ての公称サイズを単に合計しただけでは安全ではありません。 さらに、メモリ内に格納される順序が宣言の順序と同じであると仮定するのも安全ではありません。 構造体のストレージ レイアウトを制御する必要がある場合は、<xref:System.Runtime.InteropServices.StructLayoutAttribute> 属性を `Structure` ステートメントに適用します。  
  
## <a name="example"></a>例  
 次の例では、`Structure` ステートメントを使って、従業員に関連のある複数のデータを定義しています。 データ項目の機密性に応じて `Public`、`Friend`、`Private` の各メンバーを使用する方法が示されています。 プロシージャ、プロパティ、およびイベント メンバーも示されています。  
  
 [!code-vb[VbVbalrStatements#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#57)]  
  
## <a name="see-also"></a>関連項目

- [Class ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)
- [Interface ステートメント](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Module ステートメント](../../../visual-basic/language-reference/statements/module-statement.md)
- [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)
- [Const ステートメント](../../../visual-basic/language-reference/statements/const-statement.md)
- [Enum ステートメント](../../../visual-basic/language-reference/statements/enum-statement.md)
- [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)
- [Operator ステートメント](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)
- [構造体とクラス](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
