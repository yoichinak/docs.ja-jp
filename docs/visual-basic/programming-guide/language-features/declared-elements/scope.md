---
title: Visual Basic におけるスコープ
ms.date: 07/20/2015
helpviewer_keywords:
- module scope [Visual Basic]
- scope [Visual Basic], levels
- module level
- procedures [Visual Basic], scope
- declared elements [Visual Basic], scope
- namespaces [Visual Basic], scope
- scope [Visual Basic], declared elements
- scope [Visual Basic], about scope
- levels of scope [Visual Basic]
- block scope [Visual Basic]
- scope [Visual Basic], Visual Basic
- procedure scope [Visual Basic]
ms.assetid: 208106fe-79c9-4eec-93c6-55f08548895f
ms.openlocfilehash: 806e4605411304f58d0428f2588454ba9652946e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64610369"
---
# <a name="scope-in-visual-basic"></a>Visual Basic におけるスコープ
*スコープ*一連の名前を修飾したり、を通じて利用できるようにせずに参照できるすべてのコードは、宣言された要素の[Imports ステートメント (.NET Namespace よぶ型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)します。 要素は、次のレベルのいずれかのスコープを設定できます。  
  
|レベル|説明|  
|-----------|-----------------|  
|ブロック スコープ|それが宣言されているブロック、コード内でのみ使用可能|  
|プロシージャ スコープ|宣言されているプロシージャ内のすべてのコードで使用可能|  
|モジュール スコープ|モジュール、クラス、または構造体が宣言されているすべてのコードで使用可能|  
|Namespace スコープ|名前空間が宣言されているすべてのコードで使用可能|  
  
 これらのレベルを最も幅の広い (名前空間)、最も狭い (ブロック) からスコープの進行状況の場所*最も狭いスコープ*修飾なしの要素を参照するコードの最小セットのことを意味します。 詳細については、このページで「レベルのスコープ」を参照してください。  
  
## <a name="specifying-scope-and-defining-variables"></a>スコープを指定して、変数を定義します。  
 宣言するときに、要素のスコープを指定します。 スコープは、次の要因によって異なります。  
  
- 要素を宣言するリージョン (ブロック、プロシージャ、モジュール、クラスまたは構造体)  
  
- 要素の宣言を含む名前空間  
  
- 要素の宣言するアクセス レベル  
  
 これを行うため、名前が同じで、異なるスコープを持つ変数を定義するときに、注意してについては、予期しない結果につながります。 詳細については、「 [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)」を参照してください。  
  
## <a name="levels-of-scope"></a>スコープのレベル  
 プログラミング要素は、その宣言領域全体で使用できます。 同じリージョン内のすべてのコードは、その名前を修飾しなくても、要素を参照できます。  
  
### <a name="block-scope"></a>ブロック スコープ  
 ブロックを開始して、次の宣言ステートメントの終了で囲まれたステートメントのセットを示します。  
  
- `Do` および `Loop`  
  
- `For` [`Each`] と `Next`  
  
- `If` および `End If`  
  
- `Select` および `End Select`  
  
- `SyncLock` および `End SyncLock`  
  
- `Try` および `End Try`  
  
- `While` および `End While`  
  
- `With` および `End With`  
  
 ブロック内で変数を宣言する場合は、そのブロック内でのみ使用できます。 次の例では、整数変数のスコープで`cube`間ブロック`If`と`End If`を参照することが不要になったと`cube`ブロックからの実行のパスとします。  
  
```  
If n < 1291 Then  
    Dim cube As Integer  
    cube = n ^ 3  
End If  
```  
  
> [!NOTE]
>  変数のスコープは、ブロックに制限されている場合でもその有効期間は引き続き手順全体の。 処理中に、ブロックを複数回入力した場合、各ブロック変数は、前の値を保持します。 このような場合に予期しない結果を回避するためには、ブロックの先頭ブロックの変数を初期化することをお勧めします。  
  
### <a name="procedure-scope"></a>プロシージャ スコープ  
 プロシージャ内で宣言された要素は、そのプロシージャの外にご利用いただけません。 宣言を含むプロシージャのみを使用できます。 このレベルの変数とも呼ばれます*ローカル変数*します。 宣言することで、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)、またはなし、[静的](../../../../visual-basic/language-reference/modifiers/static.md)キーワード。  
  
 プロシージャとブロックのスコープは密接に関連します。 プロシージャ内にあるが、そのプロシージャ内で任意のブロックの外部変数を宣言する場合、プロシージャ全体は、ブロック スコープを持つものとして変数を考えることができます。  
  
> [!NOTE]
>  いる場合でも、すべてのローカル要素`Static`変数は、出現するプロシージャ。 使用して、要素を宣言することはできません、[パブリック](../../../../visual-basic/language-reference/modifiers/public.md)プロシージャ内でキーワード。  
  
### <a name="module-scope"></a>モジュール スコープ  
 便宜上、1 つの用語*モジュール レベル*モジュール、クラス、および構造に当てはまります。 このレベルで要素を宣言するには、任意のプロシージャまたはブロックの外部では、モジュール、クラスまたは構造体の宣言ステートメントを配置します。  
  
 モジュール レベルで宣言すると、選択したアクセス レベルは、スコープを決定します。 モジュール、クラスまたは構造体を含む名前空間には、スコープも影響します。  
  
 要素を宣言する[プライベート](../../../../visual-basic/language-reference/modifiers/private.md)アクセス レベルは別のモジュール内のコードではなく、そのモジュールでは、すべてのプロシージャに使用できます。 `Dim`モジュール レベルでのステートメントは既定に`Private`アクセス レベル キーワードを使用しない場合。 ただし、行うことができます、スコープとアクセス レベルより明白なを使用して、`Private`キーワード、`Dim`ステートメント。  
  
 次の例では、モジュールで定義されているすべてのプロシージャが文字列変数を指すこと`strMsg`します。 2 番目のプロシージャが呼び出されたときに、文字列変数の内容を表示します。 `strMsg`  ダイアログ ボックス。  
  
```  
' Put the following declaration at module level (not in any procedure).  
Private strMsg As String  
' Put the following Sub procedure in the same module.  
Sub initializePrivateVariable()  
    strMsg = "This variable cannot be used outside this module."  
End Sub  
' Put the following Sub procedure in the same module.  
Sub usePrivateVariable()  
    MsgBox(strMsg)  
End Sub  
```  
  
### <a name="namespace-scope"></a>Namespace スコープ  
 モジュールを使用してレベルにある要素を宣言する場合、[フレンド](../../../../visual-basic/language-reference/modifiers/friend.md)または[パブリック](../../../../visual-basic/language-reference/modifiers/public.md)要素が宣言されている名前空間全体ですべてのプロシージャを使用可能になったキーワード。 上記の例では、文字列変数に次の変更と`strMsg`宣言の名前空間内のすべてのコードで参照できます。  
  
```  
' Include this declaration at module level (not inside any procedure).  
Public strMsg As String  
```  
  
 Namespace スコープには、入れ子になった名前空間が含まれています。 名前空間内で使用可能な要素もその名前空間内で入れ子になった名前空間の中から使用できます。  
  
 プロジェクトが含まれない場合[Namespace ステートメント](../../../../visual-basic/language-reference/statements/namespace-statement.md)s、同じ名前空間は、プロジェクト内のすべて。 この場合、名前空間のスコープは、プロジェクトのスコープとして考えることができます。 `Public` モジュール、クラスまたは構造内の要素は、プロジェクトを参照する任意のプロジェクトにも利用します。  
  
## <a name="choice-of-scope"></a>スコープの選択  
 変数を宣言するときにおく必要がありますに注意してください、次の点スコープを選択します。  
  
### <a name="advantages-of-local-variables"></a>ローカル変数の利点  
 ローカル変数では、任意の種類の一時的な計算は、適切な選択が、次の理由です。  
  
- **名前の競合を回避することです。** ローカルの変数名が競合を受けやすくなります。 たとえば、という名前の変数を含むいくつかの異なる手順を作成できます`intTemp`します。 それぞれ`intTemp`各プロシージャに独自のバージョンのみが認識されるローカル変数として宣言されての`intTemp`します。 任意の 1 つのプロシージャは、ローカルの値を変更できます`intTemp`影響を与えずに`intTemp`他のプロシージャでの変数。  
  
- **メモリ使用量。** ローカル変数は、そのプロシージャが実行中にのみ、メモリを消費します。 プロシージャが呼び出し元のコードに返されるときに、メモリは解放されます。 これに対し、 [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)と[静的](../../../../visual-basic/language-reference/modifiers/static.md)変数がメモリ リソースを消費するアプリケーションの実行が停止されるまで、そのために必要な場合にのみ使用します。 *インスタンス変数*間メモリを消費、インスタンスが存在しているローカル変数よりも効率的ですよりも非効率`Shared`または`Static`変数。  
  
### <a name="minimizing-scope"></a>スコープを最小限に抑える  
 一般に、任意の変数または定数を宣言するときをお勧めできるだけスコープを作成するプログラミング手法 (ブロック スコープでは、最も狭い)。 これにより、メモリを節約でき、不正な変数を誤って参照するコードの可能性を最小限に抑えられます。 同様に、ある変数を宣言する必要があります[静的](../../../../visual-basic/language-reference/modifiers/static.md)プロシージャ呼び出しの間には、その値を保持するために必要な場合のみです。  
  
## <a name="see-also"></a>関連項目

- [宣言された要素の特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [方法: コントロール変数のスコープ](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)
- [Visual Basic での有効期間](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Visual Basic でのアクセス レベル](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [宣言された要素の参照](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
