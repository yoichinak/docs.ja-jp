---
title: Module ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Module
- vb.Module
helpviewer_keywords:
- modules, classes
- modules
- Module statement [Visual Basic]
- modules, declaring
- standard modules
- classes [Visual Basic], vs. modules
- declarations [Visual Basic], modules
ms.assetid: a1243afc-14a5-45df-95d5-51118aeac362
ms.openlocfilehash: f546498e5282bcf58d07a06968bb4303e4e6d7b9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58838145"
---
# <a name="module-statement"></a>Module ステートメント
モジュールの名前を宣言し、変数、プロパティ、イベント、およびモジュールを構成するプロシージャの定義を紹介します。  
  
## <a name="syntax"></a>構文  
  
```vb 
[ <attributelist> ] [ accessmodifier ]  Module name  
    [ statements ]  
End Module  
```  
  
## <a name="parts"></a>指定項目  
 `attributelist`  
 省略可能です。 参照してください[属性リスト](../../../visual-basic/language-reference/statements/attribute-list.md)します。  
  
 `accessmodifier`  
 任意。 次のいずれかの値を指定します。  
  
-   [Public](../../../visual-basic/language-reference/modifiers/public.md)  
  
-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
 「 [Visual Basic でのアクセス レベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。  
  
 `name`  
 必須。 このモジュールの名前。 「 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。  
  
 `statements`  
 省略可能です。 変数、プロパティ、イベント、プロシージャ、およびこのモジュールの入れ子にされた型を定義するステートメントです。  
  
 `End Module`  
 `Module` の定義を終了します。  
  
## <a name="remarks"></a>Remarks  
 A`Module`ステートメントは、その名前空間全体で使用できる参照型を定義します。 A*モジュール*(とも呼ばれる、*標準モジュール*) のようなクラスがいくつか重要な違いがあります。 すべてのモジュールは、1 つのインスタンスを備え、作成または変数に代入する必要はありません。 モジュールは継承をサポートしていないまたはインターフェイスを実装します。 モジュールが通知を*型*クラスまたは構造体は、という意味で-モジュールのデータ型を持つプログラミング要素を宣言することはできません。  
  
 使用することができます`Module`名前空間レベルでのみです。 つまり、*宣言コンテキスト*モジュールのソース ファイルまたは名前空間にある必要があります、クラス、構造体、モジュール、インターフェイス、プロシージャ、またはブロックすることはできません。 文字列または任意の種類別のモジュール内のモジュールを入れ子にすることはできません。 詳細については、「[宣言コンテキストと既定のアクセス レベル](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)」を参照してください。  
  
 モジュールが、有効期間は、プログラムと同じです。 そのメンバーはすべてため`Shared`のプログラムの有効期間もあります。  
  
 既定で、モジュール[フレンド](../../../visual-basic/language-reference/modifiers/friend.md)アクセスします。 アクセス修飾子を使用してこれらのアクセス レベルを調整できます。 詳細については、[ Visual Basic のアクセス レベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)を参照してください。  
  
 モジュールのすべてのメンバーは、暗黙的に`Shared`します。  
  
## <a name="classes-and-modules"></a>クラスとモジュール  
 これらの要素がある多くの類似点がいくつかの重要な違いがあります。  
  
-   **用語集。** Visual Basic の以前のバージョンは 2 種類のモジュールを認識:*クラス モジュール*(.cls ファイル) と*標準モジュール*(.bas ファイル)。 現在のバージョンを呼び出す*クラス*と*モジュール*、それぞれします。  
  
-   **共有メンバー。** クラスのメンバーは、共有するかどうか、またはインスタンス メンバーを制御できます。  
  
-   **オブジェクト指向です。** クラスは、オブジェクト指向ですが、モジュールがないです。 したがって、クラスだけは、オブジェクトとしてインスタンス化できます。 詳細については、次を参照してください。[オブジェクトとクラス](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)します。  
  
## <a name="rules"></a>ルール  
  
-   **修飾子。** すべてのモジュールのメンバーは、暗黙的に[Shared](../../../visual-basic/language-reference/modifiers/shared.md)します。 使用することはできません、`Shared`キーワードと、任意のメンバーの共有状態を変更して、メンバーを宣言することはできません。  
  
-   **継承。** モジュールが以外の任意の型から継承できません<xref:System.Object>、どのすべてのモジュールから継承します。 具体的には、1 つのモジュールは、別の継承できません。  
  
     使用することはできません、 [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md)モジュールの定義を指定するも<xref:System.Object>します。  
  
-   **既定のプロパティ。** モジュールには、既定のプロパティを定義できません。 詳細については、次を参照してください。[既定](../../../visual-basic/language-reference/modifiers/default.md)します。  
  
## <a name="behavior"></a>動作  
  
-   **アクセス レベルです。** モジュール内には、アクセス レベルでは、各メンバーを宣言できます。 モジュール メンバー[パブリック](../../../visual-basic/language-reference/modifiers/public.md)変数および定数を除く、既定のアクセス[プライベート](../../../visual-basic/language-reference/modifiers/private.md)アクセスします。 モジュールがそのメンバーの 1 つ以上のアクセスが制限されてよりときに、指定されたモジュールへのアクセス レベルが優先されます。  
  
-   **スコープ。** モジュールとは、名前空間全体のスコープ内で。  
  
     すべてのモジュール メンバーのスコープは、モジュール全体です。 すべてのメンバーに注意してください*の上位変換*、これにより、モジュールを含む名前空間に昇格するには、そのスコープ。 詳細については、次を参照してください。[型の上位変換](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)します。  
  
-   **パス名です。** プロジェクトでは、複数のモジュールがあることができ、2 つまたは複数のモジュールで同じ名前を持つメンバーを宣言することができます。 ただし、モジュールの外部から参照がある場合は、このような適切なモジュール名を持つメンバーへの参照を修飾する必要があります。 詳細については、「 [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)」を参照してください。  
  
## <a name="example"></a>例  
 [!code-vb[VbVbalrStatements#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#69)]  
  
## <a name="see-also"></a>関連項目

- [Class ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)
- [Namespace ステートメント](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Interface ステートメント](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)
- [型の上位変換](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)
