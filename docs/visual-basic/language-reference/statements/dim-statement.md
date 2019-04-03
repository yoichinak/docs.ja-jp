---
title: Dim ステートメント (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Dim
- Dim
helpviewer_keywords:
- Public keyword [Visual Basic], in Dim statement
- Dim statement [Visual Basic]
- fixed-length strings [Visual Basic], declaring
- variables [Visual Basic], declaring
- WithEvents keyword [Visual Basic], Dim statement
- dynamic arrays [Visual Basic], Dim statement
- variables [Visual Basic], initializing
- '{} braces'
- fields [Visual Basic], as member variables
- declarations [Visual Basic], dynamic arrays
- member variables [Visual Basic]
- default values [Visual Basic]
- data types [Visual Basic], assigning
- braces {}
- As keyword [Visual Basic], in Dim statement
- arrays [Visual Basic], declaring
- New keyword [Visual Basic], Dim statement
- To keyword [Visual Basic], in Dim statement
- storage [Visual Basic], allocating
- local variables [Visual Basic]
- declaration statements [Visual Basic]
- Dim statement [Visual Basic], syntax
- variables [Visual Basic], member and local
ms.assetid: fae3eca1-f0b2-4400-994b-7aa58a848448
ms.openlocfilehash: cab1cc07d23a44e57bdb0962a323b014308cb1e5
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58836559"
---
# <a name="dim-statement-visual-basic"></a>Dim ステートメント (Visual Basic)
宣言し、1 つまたは複数の変数の記憶域を割り当てます。  
  
## <a name="syntax"></a>構文  
  
```  
[ <attributelist> ] [ accessmodifier ] [[ Shared ] [ Shadows ] | [ Static ]] [ ReadOnly ]   
Dim [ WithEvents ] variablelist  
```  
  
## <a name="parts"></a>指定項目  
  
-   `attributelist`  
  
     省略可能です。 参照してください[属性リスト](../../../visual-basic/language-reference/statements/attribute-list.md)します。  
  
-   `accessmodifier`  
  
     任意。 次のいずれかの値を指定します。  
  
    -   [Public](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   [Protected Friend](../../language-reference/modifiers/protected-friend.md)
    
    - [Private Protected](../../language-reference/modifiers/private-protected.md)

     「 [Visual Basic でのアクセス レベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。  
  
-   `Shared`  
  
     省略可能です。 参照してください[共有](../../../visual-basic/language-reference/modifiers/shared.md)します。  
  
-   `Shadows`  
  
     省略可能です。 参照してください[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)します。  
  
-   `Static`  
  
     省略可能です。 参照してください[静的](../../../visual-basic/language-reference/modifiers/static.md)します。  
  
-   `ReadOnly`  
  
     省略可能です。 参照してください[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)します。  
  
-   `WithEvents`  
  
     省略可能です。 これらはイベントを発生させるクラスのインスタンスを参照するオブジェクト変数であることを指定します。 参照してください[WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)します。  
  
-   `variablelist`  
  
     必須。 このステートメントで宣言されている変数の一覧。  
  
     `variable [ , variable ... ]`  
  
     `variable` の構文と指定項目は次のとおりです。  
  
     `variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`  
  
    |パーツ|説明|  
    |---|---|  
    |`variablename`|必須。 変数名。 「 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。|  
    |`boundslist`|省略可能です。 配列変数の各次元の境界の一覧です。|  
    |`New`|省略可能です。 クラスの新しいインスタンスを作成時に、`Dim`ステートメントが実行されています。|  
    |`datatype`|省略可能です。 変数のデータ型。|  
    |`With`|省略可能です。 オブジェクト初期化子リストが導入されています。|  
    |`propertyname`|省略可能です。 クラスのプロパティの名前のインスタンスを行っています。|  
    |`propinitializer`|後に必要な`propertyname`=。 式が評価され、プロパティ名に割り当てられているです。|  
    |`initializer`|省略可能な場合`New`が指定されていません。 評価され、作成時にその変数に代入する式。|  
  
## <a name="remarks"></a>Remarks  
 Visual Basic コンパイラを使用して、`Dim`ステートメント、変数のデータ型と変数にアクセスできるコードなどの他の情報を決定します。 次の例を保持する変数の宣言、`Integer`値。  
  
```vb  
Dim numberOfStudents As Integer  
```  
  
 任意のデータ型または列挙型、構造体、クラス、インターフェイスの名前を指定することができます。  
  
```vb  
Dim finished As Boolean  
Dim monitorBox As System.Windows.Forms.Form  
```  
  
 使用する参照型の場合、`New`データ型で、クラスの新しいインスタンスを作成または構造体のキーワードを指定します。 使用する場合`New`、初期化子式を使用しません。 代わりに、変数の作成元となるクラスのコンス トラクターに必要な場合は、引数を指定します。  
  
```vb  
Dim bottomLabel As New System.Windows.Forms.Label  
```  
  
 プロシージャ、ブロック、クラス、構造体、またはモジュール内の変数を宣言することができます。 ソース ファイル、名前空間、またはインターフェイスの変数を宣言することはできません。 詳細については、「[宣言コンテキストと既定のアクセス レベル](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)」を参照してください。  
  
 プロシージャの外部のモジュール レベルで宣言されている変数は、*メンバー変数*または*フィールド*します。 メンバー変数は、そのクラス、構造体、またはモジュール全体にわたってスコープになります。 プロシージャ レベルで宣言されている変数は、*ローカル変数*します。 ローカル変数は、そのプロシージャまたはブロック内でのみスコープになります。  
  
 次のアクセス修飾子を使用して、プロシージャの外部変数の宣言: `Public`、 `Protected`、 `Friend`、 `Protected Friend`、および`Private`します。 詳細については、[ Visual Basic のアクセス レベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)を参照してください。  
  
 `Dim`キーワードが省略可能、通常、次の修飾子のいずれかを指定する場合を省略して: `Public`、 `Protected`、 `Friend`、 `Protected Friend`、 `Private`、 `Shared`、 `Shadows`、 `Static`、`ReadOnly`、または`WithEvents`します。  
  
```vb  
Public maximumAllowed As Double  
Protected Friend currentUserName As String  
Private salary As Decimal  
Static runningTotal As Integer  
```  
  
 場合`Option Explicit`はコンパイラ on (既定値) を使用するすべての変数の宣言が必要です。 詳細については、次を参照してください。 [Option Explicit ステートメント](../../../visual-basic/language-reference/statements/option-explicit-statement.md)します。  
  
## <a name="specifying-an-initial-value"></a>初期値を指定します。  
 作成時にその変数に値を割り当てることができます。 使用する値型の場合、*初期化子*変数に割り当てられる式を指定します。 式は、コンパイル時に計算できる定数に評価する必要があります。  
  
```vb  
Dim quantity As Integer = 10  
Dim message As String = "Just started"  
```  
  
 初期化子が指定され、データ型がで指定されていない場合、`As`句、*型推論*初期化子からのデータ型を推定するために使用します。 次の例では、どちらも`num1`と`num2`整数として厳密に型指定します。 2 番目の宣言では、型の推定は、値は 3 から型を推測します。  
  
```vb  
' Use explicit typing.  
Dim num1 As Integer = 3  
  
' Use local type inference.  
Dim num2 = 3  
```  
  
 型の推定は、プロシージャ レベルで適用されます。 クラス、構造体、モジュール、またはインターフェイスのプロシージャの外側は適用されません。 型の推定に関する詳細については、次を参照してください。 [Option Infer ステートメント](../../../visual-basic/language-reference/statements/option-infer-statement.md)と[ローカル型推論](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)します。  
  
 データ型または初期化子が指定されていないときの動作については、次を参照してください。[既定のデータ型と値](../../../visual-basic/language-reference/statements/dim-statement.md#default)このトピックで後述します。  
  
 使用することができます、*オブジェクト初期化子*を名前付きの匿名型のインスタンスを宣言します。 インスタンスを作成する次のコードを`Student`クラスし、プロパティを初期化するために、オブジェクト初期化子を使用します。  
  
```vb  
Dim student1 As New Student With {.First = "Michael",   
                                  .Last = "Tucker"}  
```  
  
 オブジェクト初期化子の詳細については、次を参照してください。[方法。オブジェクト初期化子を使用してオブジェクトを宣言](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)、[オブジェクト初期化子。名前付きの匿名型](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)、および[匿名型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)します。  
  
## <a name="declaring-multiple-variables"></a>複数の変数を宣言します。  
 かっこで囲んで、それぞれの次の各配列名の変数名を指定する 1 つの宣言ステートメントで複数の変数を宣言できます。 複数の変数を指定するときは、コンマで区切ります。  
  
```vb  
Dim lastTime, nextTime, allTimes() As Date  
```  
  
 いずれかで 1 つ以上の変数を宣言する場合`As`句では、そのグループの変数の初期化子を指定することはできません。  
  
 異なる変数に異なるデータ型を指定するには、個別を使用して`As`を宣言する変数ごとの句。 各変数は、最初に指定されたデータ型を受け取る`As`句の後に発生したその`variablename`部分。  
  
```vb  
Dim a, b, c As Single, x, y As Double, i As Integer  
' a, b, and c are all Single; x and y are both Double  
```  
  
## <a name="arrays"></a>配列  
 保持する変数を宣言することができます、*配列*、複数の値を保持することができます。 次の変数は配列を保持することを指定するその`variablename`かっこですぐにします。 配列の詳細については、「[配列](../../../visual-basic/programming-guide/language-features/arrays/index.md)」を参照してください。  
  
 配列の各次元の上限と下限を指定することができます。 これを行うには、`boundslist`かっこで囲んでいます。 各ディメンションに対して、`boundslist`上限と下限の境界、必要に応じてを指定します。 下限の境界は常に、0、ですか、指定するかどうか。 各インデックスは 0 ~ 上限値によって異なります。  
  
 次の 2 つのステートメントは同等です。 各ステートメントは、21 の配列を宣言します。`Integer`要素。 配列にアクセスするときに 0 ~ 20 のインデックスと異なることができます。  
  
```vb  
Dim totals(20) As Integer  
Dim totals(0 To 20) As Integer  
```  
  
 次のステートメントは、2 次元配列の型を宣言します`Double`します。 配列には、6 列 (5 + 1) 各の行 (3 + 1) 4 があります。 上限の次元の長さではなく、インデックスの最大値を表すことに注意してください。 次元の長さは、上限の境界と 1 つです。  
  
```vb  
Dim matrix2(3, 5) As Double  
```  
  
 配列は、1 から 32 次元ができます。  
  
 すべての境界に配列の宣言では空白にしておきます。 これを行う場合は、配列が指定すると、ディメンションの数が初期化されていません。 値を持つ、`Nothing`少なくとも初期化するまでの一部の要素。 `Dim`ステートメントは、すべてのディメンションまたはディメンションがありませんのいずれかの境界を指定する必要があります。  
  
```vb  
' Declare an array with blank array bounds.  
Dim messages() As String  
' Initialize the array.  
ReDim messages(4)  
```  
  
 配列に 1 つ以上のディメンションがある場合は、ディメンションの数を示すかっこ間にコンマを含める必要があります。  
  
```vb  
Dim oneDimension(), twoDimensions(,), threeDimensions(,,) As Byte  
```  
  
 宣言することができます、*長さ 0 の配列*を-1 と配列の次元のいずれかを宣言することで。 長さ 0 の配列を保持する変数は、値を持たない`Nothing`します。 長さ 0 の配列には、共通言語ランタイムの一部の関数が必要です。 このような配列にアクセスしようとすると、ランタイム例外が発生します。 詳細については、次を参照してください。[配列](../../../visual-basic/programming-guide/language-features/arrays/index.md)します。  
  
 配列の値を初期化するには、配列リテラルを使用します。 これを行うには、初期化値を中かっこで囲みます (`{}`)。  
  
```vb  
Dim longArray() As Long = {0, 1, 2, 3}  
```  
  
 多次元配列は、各次元の初期化は、外側のディメンションの中かっこで囲まれます。 要素は、行優先順で指定されます。  
  
```vb  
Dim twoDimensions(,) As Integer = {{0, 1, 2}, {10, 11, 12}}  
```  
  
 配列リテラルの詳細については、次を参照してください。[配列](../../../visual-basic/programming-guide/language-features/arrays/index.md)します。  
  
## <a name="default"></a> 既定のデータ型し、値  
 次の表では、`Dim` ステートメントのデータ型と初期化子を指定するさまざまな組み合わせの結果を示します。  
  
|データ型が指定されているか|初期化子が指定されているか|例|結果|  
|---|---|---|---|  
|いいえ|いいえ|`Dim qty`|場合[Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)に設定されている変数 off (既定)、`Nothing`します。<br /><br /> `Option Strict` がオンの場合、コンパイル時エラーが発生します。|  
|Ｘ|[はい]|`Dim qty = 5`|場合[Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md) (既定値) では、変数は、データが初期化子の型します。 参照してください[ローカル型推論](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)します。<br /><br /> `Option Infer` がオフで、`Option Strict` がオフの場合、変数は `Object` のデータ型になります。<br /><br /> `Option Infer` がオフで、`Option Strict` がオンの場合、コンパイル時エラーが発生します。|  
|[はい]|いいえ|`Dim qty As Integer`|変数は、データ型の既定値に初期化されます。 このセクションの後半の表を参照してください。|  
|[はい]|[はい]|`Dim qty  As Integer = 5`|初期化子のデータ型を指定したデータ型に変換できない場合は、コンパイル時エラーが発生します。|  
  
 データ型を指定して、初期化子を指定しない場合、Visual Basic には、データ型の既定値に変数を初期化します。 次の表は、既定の初期値を示します。  
  
|データの種類|既定値|  
|---|---|  
|すべての数値型 (など`Byte`と`SByte`)|0|  
|`Char`|バイナリ 0|  
|すべての参照型 (など`Object`、`String`とすべての配列)|`Nothing`|  
|`Boolean`|`False`|  
|`Date`|1 年 1 月 1 日の 12時 00分 AM (01/01/0001 12時 00分: 00 AM)|  
  
 構造体の各要素は、個別の変数として初期化されます。 配列の長さを宣言する場合は、その要素を初期化できません、各要素は、別個の変数の場合と同様に初期化されます。  
  
## <a name="static-local-variable-lifetime"></a>静的ローカル変数有効期間  
 A`Static`ローカル変数が宣言されているプロシージャの場合よりも有効期間が長くなります。 変数の有効期間の境界は、プロシージャが宣言されていると、かどうかによって異なります。`Shared`します。  
  
|プロシージャの宣言|初期化された変数|既存の変数を停止します|  
|---|---|---|  
|モジュールで|最初に、プロシージャを呼び出す|プログラムが実行を停止します|  
|手順は、クラスまたは構造体では、します。 `Shared`|最初に特定のインスタンスまたはクラスまたは構造体自体のプロシージャが呼び出されます|プログラムが実行を停止します|  
|クラスまたは構造体では、プロシージャがないです。 `Shared`|最初に、プロシージャは特定のインスタンスで呼び出されます。|ガベージ コレクション (GC) のインスタンスを解放する場合|  
  
## <a name="attributes-and-modifiers"></a>属性と修飾子  
 ローカル変数ではなく、メンバー変数にのみ、属性を適用することができます。 属性は、ローカル変数などの一時的なストレージの意味はないアセンブリのメタデータに情報を提供します。  
  
 モジュール レベルで使用することはできません、`Static`メンバー変数を宣言する修飾子。 プロシージャ レベルで使用することはできません`Shared`、 `Shadows`、 `ReadOnly`、 `WithEvents`、またはのいずれかのアクセス修飾子をローカル変数を宣言します。  
  
 指定することによって、変数にアクセスできるコードを指定することができます、`accessmodifier`します。 プライベート アクセスは、クラスとモジュールのメンバー (プロシージャ) の外部変数既定と構造体メンバー変数の既定のパブリック アクセスにします。 アクセス修飾子を使用してこれらのアクセス レベルを調整できます。 (プロシージャ) 内のローカル変数にアクセス修飾子を使用することはできません。  
  
 指定できる`WithEvents`メンバー変数でのみ、プロシージャ内のローカル変数ではなく。 指定した場合`WithEvents`、変数のデータ型がない、特定のクラス型をある必要があります`Object`します。 配列を宣言することはできません`WithEvents`します。 イベントの詳細については、次を参照してください。[イベント](../../../visual-basic/programming-guide/language-features/events/index.md)します。  
  
> [!NOTE]
>  コード、クラスの外部で構造体、またはモジュール修飾する必要があります、クラス、構造体、モジュールの名前を持つメンバー変数の名前。 コードの外部プロシージャまたはブロックは、そのプロシージャまたはブロック内のローカル変数を参照できません。  
  
## <a name="releasing-managed-resources"></a>マネージ リソースを解放します。  
 ユーザー側で余分なコーディングなしに、.NET Framework のガベージ コレクターがマネージ リソースを破棄します。 ただし、ガベージ コレクターを待つのではなくマネージ リソースの破棄を強制できます。  
  
 クラスは、特に役に立つと不足しているリソース (データベース接続やファイル ハンドル) などの上に保持している場合、次のガベージ コレクションで使用できなくなったクラスのインスタンスをクリーンアップするまでお待ちたくないです。 クラスを実装、<xref:System.IDisposable>ガベージ コレクションの前にリソースを解放する手段を提供するインターフェイス。 そのインターフェイスを実装するクラスは、公開、`Dispose`メソッドをすぐに解放するためのリソースの強制的に呼び出すことができます。  
  
 `Using`ステートメントは、リソースの取得、一連のステートメントを実行して、リソースを破棄し、プロセスを自動化します。 ただし、リソースを実装する必要があります、<xref:System.IDisposable>インターフェイス。 詳細については、[Using ステートメント](../../../visual-basic/language-reference/statements/using-statement.md)を参照してください。  
  
## <a name="example"></a>例  
 次の例では、変数を宣言を使用して、`Dim`さまざまなオプションを使用してステートメントです。  
  
 [!code-vb[VbVbalrStatements#141](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#141)]  
  
## <a name="example"></a>例  
 次の例は、1 ~ 30 の素数を一覧表示します。 コードのコメントは、ローカル変数のスコープを説明します。  
  
 [!code-vb[VbVbalrStatements#142](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#142)]  
  
## <a name="example"></a>例  
 次の例では、`speedValue`クラス レベルの変数を宣言します。 `Private`キーワードの使用を変数を宣言します。 変数の任意のプロシージャからアクセスできる、`Car`クラス。  
  
 [!code-vb[VbVbalrStatements#144](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#144)]  
  
 [!code-vb[VbVbalrStatements#145](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#145)]  
  
## <a name="see-also"></a>関連項目

- [Const ステートメント](../../../visual-basic/language-reference/statements/const-statement.md)
- [ReDim ステートメント](../../../visual-basic/language-reference/statements/redim-statement.md)
- [Option Explicit ステートメント](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Option Infer ステートメント](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [[コンパイル] ページ、プロジェクト デザイナー (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [変数宣言](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [配列](../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [オブジェクト初期化子:名前付きの匿名型](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [匿名型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [オブジェクト初期化子:名前付きの匿名型](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [方法: オブジェクト初期化子を使用してオブジェクトを宣言します。](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
- [ローカル型の推論](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
