---
title: Structure ステートメント
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
ms.openlocfilehash: 120f836b9d49c00e9c53af0d1fc832e22c8cbbb8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346458"
---
# <a name="structure-statement"></a>Structure ステートメント

構造体の名前を宣言し、構造体を構成する変数、プロパティ、イベント、およびプロシージャの定義を提供します。

## <a name="syntax"></a>構文

```vb
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
|`attributelist`|省略可能です。 See [Attribute List](attribute-list.md).|
|`accessmodifier`|省略可能です。 次のいずれかの値を指定します。<br /><br /> -   [Public](../modifiers/public.md)<br />-   [Protected](../modifiers/protected.md)<br />-   [Friend](../modifiers/friend.md)<br />-   [Private](../modifiers/private.md)<br />- [Protected Friend](../modifiers/protected-friend.md)<br/>- [Private Protected](../modifiers/private-protected.md) <br /><br /> 「 [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。|
|`Shadows`|省略可能です。 See [Shadows](../modifiers/shadows.md).|
|`Partial`|省略可能です。 構造体の部分定義を示します。 See [Partial](../modifiers/partial.md).|
|`name`|必須です。 この構造体の名前です。 「 [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。|
|`Of`|省略可能です。 これがジェネリックな構造体であることを指定します。|
|`typelist`|Required if you use the [Of](of-clause.md) keyword. この構造体の型パラメーター リストを指定します。 See [Type List](type-list.md).|
|`Implements`|省略可能です。 この構造体が、複数のインターフェイスのメンバーを実装していることを示します。 See [Implements Statement](implements-statement.md).|
|`interfacenames`|`Implements` ステートメントを使用する場合は必ず指定します。 この構造体が実装するインターフェイスの名前を指定します。|
|`datamemberdeclarations`|必須です。 Zero or more `Const`, `Dim`, `Enum`, or `Event` statements declaring *data members* of the structure.|
|`methodmemberdeclarations`|省略可能です。 Zero or more declarations of `Function`, `Operator`, `Property`, or `Sub` procedures, which serve as *method members* of the structure.|
|`End Structure`|必須です。 `Structure` の定義を終了します。|

## <a name="remarks"></a>Remarks

`Structure` ステートメントは、カスタマイズできる複合値型を定義します。 A *structure* is a generalization of the user-defined type (UDT) of previous versions of Visual Basic. For more information, see [Structures](../../programming-guide/language-features/data-types/structures.md).

構造体は、クラスと同じ機能の多くをサポートします。 たとえば、構造体は、プロパティやプロシージャを持つことができ、インターフェイスを実装でき、パラメーター化されたコンストラクターを持つことができます。 ただし、継承、宣言、および使用方法に関しては、構造体とクラスの間には大きな違いがあります。 また、クラスは参照型ですが、構造体は値型です。 For more information, see [Structures and Classes](../../programming-guide/language-features/data-types/structures-and-classes.md).

`Structure` は、名前空間またはモジュール レベルでのみ使用できます。 This means the *declaration context* for a structure must be a source file, namespace, class, structure, module, or interface, and cannot be a procedure or block. 詳細については、「[宣言コンテキストと既定のアクセス レベル](declaration-contexts-and-default-access-levels.md)」を参照してください。

Structures default to [Friend](../modifiers/friend.md) access. アクセス修飾子を使用してこれらのアクセス レベルを調整できます。 For more information, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).

## <a name="rules"></a>ルール

- **Nesting.** 構造体の内部に別の構造体を定義できます。 The outer structure is called the *containing structure*, and the inner structure is called a *nested structure*. ただし、包含構造体をとおして入れ子構造体のメンバーにアクセスすることはできません。 入れ子構造体のメンバーにアクセスするには、入れ子構造体のデータ型の変数を宣言する必要があります。

- **Member Declaration.** 構造体のすべてのメンバーを宣言する必要があります。 A structure member cannot be [Protected](../modifiers/protected.md) or `Protected Friend` because nothing can inherit from a structure. ただし、構造体そのものを`Protected` または `Protected Friend` にすることはできます。
  
     0 個または 1 つ以上の非共有変数または非共有の非カスタム イベントを構造体内で宣言することができます。 非共有ではあっても、定数、プロパティ、およびプロシージャだけを宣言することはできません。

- **Initialization.** 構造体の非共有データ メンバーの値を宣言の一部として初期化することはできません。 構造体のパラメーター化されたコンストラクターを使ってそのようなデータ メンバーを初期化するか、または構造体のインスタンスを作成した後にメンバーに値を割り当てる必要があります。

- **継承。** 構造体は、<xref:System.ValueType> 以外の型を継承できません。すべての構造体が、この型を継承します。 特に、構造体は別の構造体を継承できません。

     You cannot use the [Inherits Statement](inherits-statement.md) in a structure definition, even to specify <xref:System.ValueType>.

- **Implementation.** If the structure uses the [Implements Statement](implements-statement.md), you must implement every member defined by every interface you specify in `interfacenames`.

- **Default Property.** A structure can specify at most one property as its *default property*, using the [Default](../modifiers/default.md) modifier. For more information, see [Default](../modifiers/default.md).

## <a name="behavior"></a>動作

- **Access Level.** 構造体の内部では、各メンバーを独自のアクセス レベルで宣言できます。 All structure members default to [Public](../modifiers/public.md) access. 構造体そのものにこれより厳しいアクセス レベルを指定した場合は、たとえアクセス修飾子を使ってメンバーのアクセス レベルを調整していても、メンバーへのアクセスが自動的に制限されることに注意してください。

- **Scope.** 構造体は、そこに含まれる名前空間、クラス、構造体、またはモジュールをスコープとします。

     すべての構造体メンバーのスコープは、構造体全体になります。

- **Lifetime.** 構造体に有効期間はありません。 ただし、構造体の各インスタンスには、他のインスタンスに依存しない独自の有効期間があります。

     The lifetime of an instance begins when it is created by a [New Operator](../operators/new-operator.md) clause. インスタンスに含まれる変数の有効期間が終わった時点で、そのインスタンスの有効期間は終わります。

     構造体インスタンスの有効期間を延長することはできません。 静的構造体に相当する機能は、モジュールに用意されています。 For more information, see [Module Statement](module-statement.md).

     構造体メンバーの有効期間は、それを宣言する方法と場所で決まります。 For more information, see "Lifetime" in [Class Statement](class-statement.md).

- **Qualification.** 構造体の外部にあるコードでは、メンバーの名前をその構造体の名前で修飾する必要があります。

     入れ子構造体の内部のコードでプログラミング要素を修飾なしで参照した場合、Visual Basic はその要素をまず入れ子構造体の内部で探し、その次にコンテナー構造体の内部で探します。この手順が、最も外側のコンテナー要素にまで繰り返されます。 詳細については、「 [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)」を参照してください。

- **Memory Consumption.** 他のすべての複合データ型と同様に、構造体の総メモリ使用量を計算する場合、各メンバーのストレージ割り当ての公称サイズを単に合計しただけでは安全ではありません。 さらに、メモリ内に格納される順序が宣言の順序と同じであると仮定するのも安全ではありません。 構造体のストレージ レイアウトを制御する必要がある場合は、<xref:System.Runtime.InteropServices.StructLayoutAttribute> 属性を `Structure` ステートメントに適用します。

## <a name="example"></a>例

次の例では、`Structure` ステートメントを使って、従業員に関連のある複数のデータを定義しています。 データ項目の機密性に応じて `Public`、`Friend`、`Private` の各メンバーを使用する方法が示されています。 プロシージャ、プロパティ、およびイベント メンバーも示されています。

[!code-vb[VbVbalrStatements#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#57)]

For more information on how to use `Structure`s, see [Structure Variable](../../programming-guide/language-features/data-types/structure-variables.md).

## <a name="see-also"></a>関連項目

- [Class ステートメント](class-statement.md)
- [Interface ステートメント](interface-statement.md)
- [Module ステートメント](module-statement.md)
- [Dim ステートメント](dim-statement.md)
- [Const ステートメント](const-statement.md)
- [Enum ステートメント](enum-statement.md)
- [Event ステートメント](event-statement.md)
- [Operator ステートメント](operator-statement.md)
- [Property ステートメント](property-statement.md)
- [構造体とクラス](../../programming-guide/language-features/data-types/structures-and-classes.md)
