---
title: Property ステートメント (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.PropertySet
- vb.Property
- vb.PropertyGet
helpviewer_keywords:
- Property statement [Visual Basic]
- default modifier
- property procedures [Visual Basic], Property statements
- Property keyword [Visual Basic]
ms.assetid: 3155edaf-8ebd-45c6-9cef-11d5d2dc8d38
ms.openlocfilehash: 0b8bec965e5a149466863cde7a2646128469cbd0
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972171"
---
# <a name="property-statement"></a>Property Statement
プロパティ、および格納し、プロパティの値を取得するために使用するプロパティ プロシージャの名前を宣言します。  
  
## <a name="syntax"></a>構文  
  
```vb  
[ <attributelist> ] [ Default ] [ accessmodifier ]   
[ propertymodifiers ] [ Shared ] [ Shadows ] [ ReadOnly | WriteOnly ] [ Iterator ]  
Property name ( [ parameterlist ] ) [ As returntype ] [ Implements implementslist ]  
    [ <attributelist> ] [ accessmodifier ] Get  
        [ statements ]  
    End Get  
    [ <attributelist> ] [ accessmodifier ] Set ( ByVal value As returntype [, parameterlist ] )  
        [ statements ]  
    End Set  
End Property  
- or -  
[ <attributelist> ] [ Default ] [ accessmodifier ]   
[ propertymodifiers ] [ Shared ] [ Shadows ] [ ReadOnly | WriteOnly ]   
Property name ( [ parameterlist ] ) [ As returntype ] [ Implements implementslist ]  
```  
  
## <a name="parts"></a>指定項目  
  
-   `attributelist`  
  
     任意。 このプロパティに適用される属性の一覧または`Get`または`Set`プロシージャ。 参照してください[属性リスト](../../../visual-basic/language-reference/statements/attribute-list.md)します。  
  
-   `Default`  
  
     任意。 このプロパティは、クラスまたは構造体が定義されている既定のプロパティを指定します。 既定のプロパティのパラメーターを受け入れる必要がありますと設定し、取得できるプロパティの名前を指定せず。 としてプロパティを宣言する場合`Default`、使用することはできません`Private`プロパティまたはプロパティ プロシージャのいずれか。  
  
-   `accessmodifier`  
  
     省略可能な`Property`ステートメントの 1 つだけで、`Get`と`Set`ステートメント。 次のいずれかの値を指定します。  
  
    -   [Public](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
    - [Protected Friend](../../language-reference/modifiers/protected-friend.md) 

    - [Private Protected](../../language-reference/modifiers/private-protected.md)
  
     「 [Visual Basic でのアクセス レベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。  
  
-   `propertymodifiers`  
  
     任意。 次のいずれかの値を指定します。  
  
    -   [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
    -   [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)  
  
    -   [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)  
  
    -   [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
  
    -   [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     任意。 参照してください[共有](../../../visual-basic/language-reference/modifiers/shared.md)します。  
  
-   `Shadows`  
  
     任意。 参照してください[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)します。  
  
-   `ReadOnly`  
  
     任意。 参照してください[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)します。  
  
-   `WriteOnly`  
  
     任意。 参照してください[WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)します。  
  
-   `Iterator`  
  
     任意。 参照してください[反復子](../../../visual-basic/language-reference/modifiers/iterator.md)します。  
  
-   `name`  
  
     必須。 プロパティ名。 「 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。  
  
-   `parameterlist`  
  
     任意。 このプロパティのパラメーターとの可能な追加パラメーターを表すローカル変数名の一覧、`Set`プロシージャ。 参照してください[パラメーター リスト](../../../visual-basic/language-reference/statements/parameter-list.md)します。  
  
-   `returntype`  
  
     場合に、必ず`Option Strict`は`On`します。 このプロパティによって返される値のデータ型。  
  
-   `Implements`  
  
     任意。 このプロパティには、このプロパティの包含クラスまたは構造体によって実装されるインターフェイスで定義されているそれぞれの 1 つまたは複数のプロパティが実装していることを示します。 参照してください[ステートメントを実装](../../../visual-basic/language-reference/statements/implements-statement.md)します。  
  
-   `implementslist`  
  
     
  `Implements` を指定する場合は、必ず指定します。 実装されているプロパティの一覧です。  
  
     `implementedproperty [ , implementedproperty ... ]`  
  
     
  `implementedproperty` の構文と指定項目は次のとおりです。  
  
     `interface.definedname`  
  
    |パーツ|説明|  
    |---|---|  
    |`interface`|必須。 このプロパティによって実装されるインターフェイスの名前を含むクラスまたは構造体。|  
    |`definedname`|必須。 使用されるプロパティが定義されている名前`interface`します。|  
  
-   `Get`  
  
     任意。 プロパティがマークされているかどうかに必要な`WriteOnly`します。 開始、`Get`プロパティ プロシージャをプロパティの値を返すために使用します。  
  
-   `statements`  
  
     任意。 内で実行するステートメントのブロック、`Get`または`Set`プロシージャ。  
  
-   `End Get`  
  
     終了、`Get`プロパティ プロシージャ。  
  
-   `Set`  
  
     任意。 プロパティがマークされているかどうかに必要な`ReadOnly`します。 開始、`Set`プロパティ プロシージャ、プロパティの値を格納するために使用します。  
  
-   `End Set`  
  
     終了、`Set`プロパティ プロシージャ。  
  
-   `End Property`  
  
     このプロパティの定義を終了します。  
  
## <a name="remarks"></a>Remarks  
 `Property`ステートメントには、プロパティの宣言が導入されています。 プロパティを持つことができます、 `Get` (読み取り専用) の手順を`Set`プロシージャ (書き込み専用)、または両方 (読み取り/書き込み)。 省略することができます、`Get`と`Set`プロシージャの自動実装プロパティを使用する場合。 詳細については、「[自動実装プロパティ](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)」を参照してください。  
  
 使用することができます`Property`クラス レベルでのみです。 つまり、*宣言コンテキスト*プロパティは、クラス、構造体、モジュール、またはインターフェイスである必要があり、ソース ファイル、名前空間、プロシージャ、またはブロックすることはできません。 詳細については、「[宣言コンテキストと既定のアクセス レベル](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)」を参照してください。  
  
 既定では、プロパティは、パブリック アクセスを使用します。 アクセス修飾子を使ってプロパティのアクセス レベルを調整することができます、`Property`とステートメントでは、必要に応じて調整できますより制限の厳しいアクセス レベルは、プロパティ プロシージャのいずれか。  
  
 Visual Basic のパラメーターを渡す、`Set`プロパティ割り当て中にプロシージャ。 パラメーターを指定しない場合`Set`、統合開発環境 (IDE) という名前の暗黙のパラメーターを使用して`value`します。 このパラメーターは、プロパティに割り当てられる値を保持します。 通常プライベート ローカル変数にこの値を格納して返すたびに、`Get`プロシージャが呼び出されます。  
  
## <a name="rules"></a>ルール  
  
-   **混合アクセス レベル。** 必要に応じていずれかの異なるアクセス レベルを指定することができます、読み取り/書き込みプロパティを定義する場合、`Get`または`Set`両方ではなく、プロシージャ。 これを行うと、プロシージャのアクセス レベル、プロパティのアクセス レベルよりもより制限の厳しい場合があります。 例では、プロパティが宣言されている場合、 `Friend`、宣言することができます、`Set`プロシージャ`Private`、なく`Public`します。  
  
     定義する場合、`ReadOnly`または`WriteOnly`プロパティ、1 つのプロパティ プロシージャ (`Get`または`Set`、それぞれ) すべてのプロパティを表します。 プロパティの 2 つのアクセス レベルを設定することがあるために、このような手順は、異なるアクセス レベルを宣言できません。  
  
-   **型を返します。** `Property`ステートメントが返す値のデータ型を宣言できます。 任意のデータ型または列挙型、構造体、クラス、インターフェイスの名前を指定することができます。  
  
     指定しない場合`returntype`、プロパティを返します。`Object`します。  
  
-   **実装です。** このプロパティで使用する場合、`Implements`キーワードを含むクラスまたは構造体があります、`Implements`ステートメントの直後の`Class`または`Structure`ステートメント。 `Implements`ステートメントで指定された各インターフェイスを含める必要があります`implementslist`します。 ただし、インターフェイスを定義する名前、 `Property` (で`definedname`) すると、このプロパティの名前と同じである必要はありません (で`name`)。  
  
## <a name="behavior"></a>動作  
  
-   **プロパティ プロシージャから取得します。** ときに、`Get`または`Set`を呼び出したステートメントに続くステートメントを使用して、プロシージャは、呼び出し元のコードに返す、実行が続行します。  
  
     `Exit Property`と`Return`ステートメントでは、プロパティ プロシージャからすぐに終了します。 任意の数の`Exit Property`と`Return`ステートメントは、手順では、どこでも表示でき、組み合わせることができます`Exit Property`と`Return`ステートメント。  
  
-   **値を返します。** 値を返す、`Get`プロシージャ、プロパティ名に値を割り当てるか、含めることで、`Return`ステートメント。 次の例では、プロパティ名に戻り値を割り当てて`quoteForTheDay`しを使用して、`Exit Property`ステートメントに戻ります。  
  
     [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]  
  
     [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]  
  
     使用する場合`Exit Property`値を割り当てることがなく`name`、`Get`プロパティのデータ型の既定値を返します。  
  
     `Return`ステートメントと同時に割り当てます、`Get`プロシージャを返す値し、手順を終了します。 次の例に示します。  
  
     [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]  
  
     [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]  
  
## <a name="example"></a>例  
 次の例では、クラスのプロパティを宣言します。  
  
 [!code-vb[VbVbalrStatements#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#51)]  
  
## <a name="see-also"></a>関連項目
- [自動実装プロパティ](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)
- [クラスとオブジェクト](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Get ステートメント](../../../visual-basic/language-reference/statements/get-statement.md)
- [Set ステートメント](../../../visual-basic/language-reference/statements/set-statement.md)
- [パラメーター リスト](../../../visual-basic/language-reference/statements/parameter-list.md)
- [Default](../../../visual-basic/language-reference/modifiers/default.md)
