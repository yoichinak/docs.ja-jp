---
title: Visual Basic での変数宣言
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], declaring
- member variables [Visual Basic], declarations
- Dim statement [Visual Basic], variable declaration
- declaring variables [Visual Basic]
- variables [Visual Basic], scope
- variables [Visual Basic], data types
- data types [Visual Basic], variable declarations
- lifetime [Visual Basic], variables
- variables [Visual Basic], lifetime
- access levels [Visual Basic], variables
- scope [Visual Basic], declaration statements
- variables [Visual Basic], access level
- local variables [Visual Basic], declarations
- scope [Visual Basic], variables
ms.assetid: d8f10226-92b1-480f-9f53-df377b2d7e15
ms.openlocfilehash: 699737ffbe0b136af8862931fadacec26772b928
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833283"
---
# <a name="variable-declaration-in-visual-basic"></a>Visual Basic での変数宣言
名前と特性を指定する変数を宣言するとします。 変数の宣言ステートメントは、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)します。 その場所や内容は、変数の特性を決定します。  
  
 変数の名前付け規則と考慮事項では、次を参照してください。 [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)します。  
  
## <a name="declaration-levels"></a>宣言レベル  
  
### <a name="local-and-member-variables"></a>ローカルとメンバー変数  
 *ローカル変数*はプロシージャ内で宣言されている 1 つです。 *メンバー変数* は、Visual Basic型のメンバーです。モジュール、クラス、構造体、またはモジュールの内部で宣言されていますが、そのクラス、構造体、またはモジュールの内部のプロシージャ内では宣言されていません。  
  
### <a name="shared-and-instance-variables"></a>共有し、インスタンス変数  
 クラスまたは構造体メンバー変数のカテゴリが共有されるかどうかに依存します。 宣言されている場合、 [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)キーワードは、*共有変数*、クラスまたは構造体のすべてのインスタンス間で共有される 1 つのコピーに存在するとします。  
  
 それ以外の場合は、*インスタンス変数*、クラスまたは構造体のインスタンスごとに個別のコピーが作成されたとします。 インスタンス変数のコピーは、クラスまたは構造体が作成されたインスタンスでのみ使用可能です。 これは、他のクラスまたは構造体のインスタンス、インスタンス変数のコピーを依存しません。  
  
## <a name="declaring-data-type"></a>データ型の宣言  
 [として](../../../../visual-basic/language-reference/statements/as-clause.md)宣言ステートメントの句では、データ型またはオブジェクトを宣言する変数の種類を定義できます。 変数の種類として次のいずれかを指定できます。  
  
-   などの基本のデータ入力`Boolean`、 `Long`、または `Decimal`  
  
-   配列や構造体などの複合データ型  
  
-   オブジェクトの種類、または、アプリケーションで、または別のアプリケーションで定義されているクラス  
  
-   A[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]クラスなど、<xref:System.Windows.Forms.Label>または <xref:System.Windows.Forms.TextBox>  
  
-   インターフェイス型など、<xref:System.IComparable>または <xref:System.IDisposable>  
  
 データ型を繰り返すことがなく、1 つのステートメントで複数の変数を宣言できます。 次のステートメントでは、変数で`i`、 `j`、および`k`型として宣言されている`Integer`、`l`と`m`として`Long`と`x`と`y`として`Single`:  
  
```  
Dim i, j, k As Integer  
' All three variables in the preceding statement are declared as Integer.  
Dim l, m As Long, x, y As Single  
' In the preceding statement, l and m are Long, x and y are Single.  
```  
  
 データ型の詳細については、次を参照してください。[データ型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)します。 オブジェクトの詳細については、次を参照してください。[オブジェクトとクラス](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)と[コンポーネントによるプログラミング](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0ffkdtkf(v=vs.120))します。  
  
## <a name="local-type-inference"></a>ローカル型の推論  
 *型の推論*なしで宣言されたローカル変数のデータの種類を決定するために使用する`As`句。 コンパイラでは、初期化式の型から変数の型を推測します。 これにより、型を明示的に指定せずに変数を宣言することができます。 次の例では、どちらも`num1`と`num2`整数として厳密に型指定します。  
  
 [!code-vb[VbVbalrTypeInference#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#1)]  
  
 ローカル型の推論を使用したい場合`Option Infer`に設定する必要があります`On`します。 詳細については、「[ローカル型の推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)」と「[Option Infer ステートメント](../../../../visual-basic/language-reference/statements/option-infer-statement.md)」を参照してください。  
  
## <a name="characteristics-of-declared-variables"></a>宣言された変数の特性  
 *有効期間*変数は、一定期間その中に、使用可能です。 一般に、変数は、(手順やクラスで) 宣言された要素が存在し続けます限り存在します。 変数がそのコンテナー要素の有効期間よりも長く必要がない場合は、宣言で特別な処理は必要はありません。 変数をそのコンテナー要素よりも長い場合は、含めることができます、`Static`または`Shared`キーワードでその`Dim`ステートメント。 詳細については、次を参照してください。 [Visual Basic での有効期間](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)します。  
  
 *スコープ*変数がその名前を修飾せずに参照できるすべてのコードのセット。 変数のスコープは、宣言されている場所によって決まります。 特定のリージョン内にあるコードでは、その名前を修飾することがなく、そのリージョンで定義されている変数を使用できます。 詳細については、「 [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)」を参照してください。  
  
 変数の*アクセス レベル*は、それへのアクセス許可があるコードの範囲です。 これは、`Dim`ステートメントで使用するアクセス修飾子([Public](../../../../visual-basic/language-reference/modifiers/public.md)または[Private](../../../../visual-basic/language-reference/modifiers/private.md)など)によって決まります。 詳細については、[ Visual Basic のアクセス レベル](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)を参照してください。  
  
## <a name="see-also"></a>関連項目

- [方法: 新しい変数を作成します。](../../../../visual-basic/programming-guide/language-features/variables/how-to-create-a-new-variable.md)
- [方法: および、変数からのデータを移動します。](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)
- [データの種類](../../../../visual-basic/language-reference/data-types/index.md)
- [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)
- [Static](../../../../visual-basic/language-reference/modifiers/static.md)
- [宣言された要素の特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [ローカル型の推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Infer ステートメント](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
