---
title: Const ステートメント (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Const
helpviewer_keywords:
- Const statement [Visual Basic]
ms.assetid: 495b318d-b7c5-4198-94f8-0790a541b07a
ms.openlocfilehash: 089c2dca99373f379e1eff319cf8c41242e5f135
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58835311"
---
# <a name="const-statement-visual-basic"></a>Const ステートメント (Visual Basic)
宣言し、1 つまたは複数の定数を定義します。  
  
## <a name="syntax"></a>構文  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ]   
Const constantlist  
```  
  
## <a name="parts"></a>指定項目  
 `attributelist`  
 任意。 すべての定数に適用される属性の一覧は、このステートメントで宣言します。 参照してください[属性リスト](../../../visual-basic/language-reference/statements/attribute-list.md)山かっこ ("`<`「と」`>`")。  
  
 `accessmodifier`  
 任意。 これを使用して、どのようなコードがアクセスできるは、これらの定数を指定します。 [パブリック](../../../visual-basic/language-reference/modifiers/public.md)、 [Protected](../../../visual-basic/language-reference/modifiers/protected.md)、[フレンド](../../../visual-basic/language-reference/modifiers/friend.md)、 [Protected Friend](../modifiers/protected-friend.md)、[プライベート](../../../visual-basic/language-reference/modifiers/private.md)、または[Private Protected](../../language-reference/modifiers/private-protected.md)します。
  
 `Shadows`  
 省略可能です。 再宣言して、基底クラスでのプログラミング要素を非表示にするには、これを使用します。 参照してください[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)します。  
  
 `constantlist`  
 必須。 このステートメントで宣言されている定数の一覧です。  
  
 `constant` `[ ,` `constant` `... ]`  
  
 `constant` の構文と指定項目は次のとおりです。  
  
 `constantname` `[ As` `datatype` `] =` `initializer`  
  
|パーツ|説明|  
|----------|-----------------|  
|`constantname`|必須。 定数の名前。 「 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。|  
|`datatype`|場合に、必ず`Option Strict`は`On`します。 定数のデータ型。|  
|`initializer`|必須。 式がコンパイル時に評価され、定数に割り当てられているです。|  
  
## <a name="remarks"></a>Remarks  
 を、アプリケーションで変更されない値がある場合は、名前付き定数を定義し、リテラル値の代わりに使用します。 名前は、値よりも覚えやすい。 定数を 1 回だけ定義でき、コード内のさまざまな場所で使用できます。 以降のバージョンでは、値を再定義する必要がある場合、`Const`ステートメントは唯一の場所を変更する必要があります。  
  
 使用することができます`Const`モジュールまたはプロシージャ レベルでのみです。 つまり、*宣言コンテキスト*変数は、クラス、構造体、モジュール、プロシージャ、またはブロックする必要があり、ソース ファイル、名前空間、またはインターフェイスにすることはできません。 詳細については、「[宣言コンテキストと既定のアクセス レベル](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)」を参照してください。  
  
 ローカル定数 (プロシージャ) 内にある既定で、パブリック アクセスに、アクセス修飾子を使用できません。 プライベート アクセスは、クラスとモジュールのメンバー (プロシージャ) の外部定数既定、構造体メンバー定数既定でパブリック アクセスします。 アクセス修飾子を使用してこれらのアクセス レベルを調整できます。  
  
## <a name="rules"></a>ルール  
  
-   **宣言コンテキスト。** 定数宣言、プロシージャの外側のモジュール レベルでは、*メンバー定数*; クラス、構造体のメンバーであるか、宣言するモジュール。  
  
     プロシージャ レベルで宣言された定数は、*ローカル定数*; プロシージャまたは宣言ブロックに対してローカルです。  
  
-   **属性。** ローカル定数ではなく、メンバーの定数にのみ、属性を適用することができます。 属性は、ローカル定数などの一時的なストレージの意味はないアセンブリのメタデータに情報を提供します。  
  
-   **修飾子。** すべての定数は、既定では、 `Shared`、 `Static`、および`ReadOnly`します。 定数を宣言するときに、これらのキーワードのいずれかを使用することはできません。  
  
     プロシージャ レベルで使用することはできません`Shadows`またはのいずれかのアクセス修飾子をローカル定数を宣言します。  
  
-   **複数の定数。** 同じ宣言ステートメントで複数の定数を宣言することを指定する、`constantname`それぞれの一部です。 複数の定数は、コンマで区切られます。  
  
## <a name="data-type-rules"></a>データ型のルール  
  
-   **データ型。** `Const`ステートメントは、変数のデータ型を宣言できます。 任意のデータ型または列挙型の名前を指定することができます。  
  
-   **既定の型。** 指定しない場合`datatype`、定数のデータ型は、`initializer`します。 両方を指定する場合`datatype`と`initializer`のデータ型`initializer`に変換できる必要があります`datatype`します。 どちらの場合`datatype`も`initializer`が存在するデータ型の既定値は`Object`します。  
  
-   **さまざまな種類。** 異なる定数に異なるデータ型を指定するには、個別を使用して`As`を宣言する変数ごとの句。 ただし、一般的なを使用して、同じ型にするいくつかの定数を宣言することはできません`As`句。  
  
-   **初期化します。** 内のすべての定数の値を初期化する必要があります`constantlist`します。 使用する`initializer`定数に割り当てられる式を指定します。 式には、リテラル、既に定義されている他の定数と既に定義されている列挙型メンバーの任意の組み合わせを指定できます。 算術演算および論理演算子を使用すると、このような要素を結合します。  
  
     変数または関数で使用することはできません`initializer`します。 変換キーワードなどを使用するただし、`CByte`と`CShort`します。 使用することも`AscW`定数で呼び出す場合`String`または`Char`引数、コンパイル時に評価できるためです。  
  
## <a name="behavior"></a>動作  
  
-   **スコープ。** ローカル定数は、そのプロシージャまたはブロック内からのみアクセスできます。 メンバー定数には、クラス、構造体、またはモジュール内で任意の場所からアクセスできます。  
  
-   **パス名です。** コード、クラスの外部で構造体、またはモジュール修飾する必要があります、クラス、構造体、モジュールの名前を持つメンバー定数の名前。 コードの外部プロシージャまたはブロックは、そのプロシージャまたはブロック内の任意のローカル定数を参照できません。  
  
## <a name="example"></a>例  
 次の例では、`Const`リテラル値の代わりに使用するための定数を宣言するステートメント。  
  
 [!code-vb[VbVbalrStatements#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#13)]  
  
## <a name="example"></a>例  
 データ型の定数を定義した場合`Object`、Visual Basic コンパイラは、の型を提供、`initializer`の代わりに`Object`します。 次の例では、定数`naturalLogBase`実行時の型を持つ`Decimal`します。  
  
 [!code-vb[VbVbalrStatements#87](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#87)]  
  
 上記の例では、<xref:System.Type.ToString%2A>メソッドを<xref:System.Type>によって返されるオブジェクト、 [GetType 演算子](../../../visual-basic/language-reference/operators/gettype-operator.md)ため、<xref:System.Type>に変換できない`String`を使用して`CStr`します。  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- [Enum ステートメント](../../../visual-basic/language-reference/statements/enum-statement.md)
- [#Const ディレクティブ](../../../visual-basic/language-reference/directives/const-directive.md)
- [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)
- [ReDim ステートメント](../../../visual-basic/language-reference/statements/redim-statement.md)
- [暗黙の型変換と明示的な型変換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [定数と列挙体](../../../visual-basic/programming-guide/language-features/constants-enums/index.md)
- [定数と列挙体](../../../visual-basic/language-reference/constants-and-enumerations.md)
- [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
