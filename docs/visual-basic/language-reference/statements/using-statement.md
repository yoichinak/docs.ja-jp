---
title: Using ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.using
helpviewer_keywords:
- resource disposal
- Try...Catch...Finally statements, equivalent to Using statement
- resources [Visual Basic], disposing
- Using statement [Visual Basic]
ms.assetid: 665d1580-dd54-4e96-a9a9-6be2a68948f1
ms.openlocfilehash: 819af63acb6a1f038300bcb999dcfb904eb8a457
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592083"
---
# <a name="using-statement-visual-basic"></a>Using ステートメント (Visual Basic)

@No__t 0 ブロックの先頭を宣言し、必要に応じて、ブロックが制御するシステムリソースを取得します。

## <a name="syntax"></a>構文

```vb
Using { resourcelist | resourceexpression }
    [ statements ]
End Using
```

## <a name="parts"></a>指定項目

|項目|定義|  
|---|---|  
|`resourcelist`|@No__t-0 を指定しない場合は必須です。 この @no__t によって制御される1つ以上のシステムリソースのリスト (コンマ区切り)。|  
|`resourceexpression`|@No__t-0 を指定しない場合は必須です。 この `Using` ブロックによって制御されるシステムリソースを参照する、参照変数または式。|  
|`statements`|任意。 @No__t 0 ブロックによって実行されるステートメントのブロック。|  
|`End Using`|必須。 @No__t 0 ブロックの定義を終了し、制御しているすべてのリソースを破棄します。|  

 @No__t-0 部分の各リソースには、次の構文と部分があります。

 `resourcename As New resourcetype [ ( [ arglist ] ) ]`

 \- または -

 `resourcename As resourcetype = resourceexpression`

## <a name="resourcelist-parts"></a>resourcelist パーツ

|項目|定義|  
|---|---|  
|`resourcename`|必須。 @No__t 0 ブロックで制御されるシステムリソースを参照する参照変数。|  
|`New`|@No__t-0 ステートメントでリソースが取得される場合は必須です。 リソースを既に取得している場合は、2番目の構文を使用します。|  
|`resourcetype`|必須。 リソースのクラス。 クラスは <xref:System.IDisposable> インターフェイスを実装する必要があります。|  
|`arglist`|任意。 のインスタンスを作成するためにコンストラクターに渡す引数のリスト `resourcetype`。 「[パラメーターリスト](parameter-list.md)」を参照してください。|  
|`resourceexpression`|必須。 @No__t-0 の要件を満たすシステムリソースを参照する変数または式。 2番目の構文を使用する場合は、`Using` ステートメントに制御を渡す前にリソースを取得する必要があります。|  
  
## <a name="remarks"></a>コメント

 コードには、ファイルハンドル、COM ラッパー、SQL 接続などのアンマネージリソースが必要な場合があります。 @No__t-0 ブロックを使用すると、コードが終了したときに、そのようなリソースが確実に破棄されます。 これにより、他のコードで使用できるようになります。

 マネージリソースは、.NET Framework ガベージコレクター (GC) によって破棄されます。その際、追加のコーディングは必要ありません。 マネージリソースに `Using` ブロックは必要ありません。 ただし、`Using` のブロックを使用して、ガベージコレクターを待機するのではなく、マネージリソースを強制的に破棄することもできます。

 @No__t 0 のブロックには、取得、使用、および破棄という3つの部分があります。

- *取得*とは、変数を作成して初期化し、システムリソースを参照することを意味します。 @No__t 0 のステートメントは1つ以上のリソースを取得できます。また、ブロックを入力する前に1つのリソースだけを取得し、それを `Using` ステートメントに指定することもできます。 @No__t-0 を指定する場合は、`Using` ステートメントに制御を渡す前にリソースを取得する必要があります。

- *使用状況*とは、リソースにアクセスし、それらのリソースでアクションを実行することを意味します。 @No__t-0 と `End Using` の間のステートメントは、リソースの使用状況を表します。

- *破棄*とは、`resourcename` でオブジェクトの <xref:System.IDisposable.Dispose%2A> メソッドを呼び出すことを意味します。 これにより、オブジェクトはリソースを完全に終了できます。 @No__t-0 ステートメントは、`Using` ブロックのコントロールの下にあるリソースを破棄します。

## <a name="behavior"></a>動作

 @No__t 0 のブロックは、`Try`... `Finally` の構造のように動作します。この構築では、@no__t 3 ブロックがリソースを使用し、@no__t 4 ブロックがそれらを破棄します。 このため、`Using` ブロックは、ブロックを終了する方法に関係なく、リソースの破棄を保証します。 これは、ハンドルされない例外が発生した場合でも、<xref:System.StackOverflowException> 以外の場合にも当てはまります。

 @No__t-0 ステートメントで取得したすべてのリソース変数のスコープは、`Using` ブロックに制限されます。

 @No__t-0 ステートメントで複数のシステムリソースを指定した場合、その効果は、`Using` ブロックを入れ子にした場合と同じになります。

 @No__t-0 が `Nothing` の場合、<xref:System.IDisposable.Dispose%2A> の呼び出しは行われず、例外はスローされません。

## <a name="structured-exception-handling-within-a-using-block"></a>Using ブロック内での構造化例外処理

 @No__t-0 ブロック内で発生する可能性のある例外を処理する必要がある場合は、完全な `Try`... `Finally` の構築をそれに追加することができます。 @No__t-0 ステートメントがリソースの取得に失敗した場合に対処する必要がある場合は、`resourcename` が @no__t かどうかをテストして確認できます。

## <a name="structured-exception-handling-instead-of-a-using-block"></a>Using ブロックの代わりに構造化例外処理

 リソースの取得をより細かく制御する必要がある場合、または `Finally` ブロックに追加のコードが必要な場合は、`Using` ブロックを `Try`... `Finally` の構築として書き換えることができます。 次の例は、`resource` の取得と破棄に相当するスケルトン `Try` および @no__t の構造を示しています。

```vb
Using resource As New resourceType
    ' Insert code to work with resource.
End Using

' For the acquisition and disposal of resource, the following  
' Try construction is equivalent to the Using block.
Dim resource As New resourceType
Try
    ' Insert code to work with resource.
Finally
    If resource IsNot Nothing Then
        resource.Dispose()
    End If
End Try
```

> [!NOTE]
> @No__t-0 ブロック内のコードでは、`resourcename` のオブジェクトを別の変数に割り当てることはできません。 @No__t-0 ブロックを終了すると、リソースが破棄され、他の変数はそのリソースが指しているリソースにアクセスできなくなります。

## <a name="example"></a>例

 次の例では、test.txt という名前のファイルを作成し、ファイルに2行のテキストを書き込みます。 この例でも同じファイルが読み取られ、テキスト行が表示されます。

 @No__t-0 および <xref:System.IO.TextReader> クラスは <xref:System.IDisposable> インターフェイスを実装するため、コードでは `Using` ステートメントを使用して、書き込み操作と読み取り操作の後でファイルが正しく閉じられるようにすることができます。

 [!code-vb[VbVbalrStatements#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#50)]

## <a name="see-also"></a>関連項目

- <xref:System.IDisposable>
- [Try...Catch...Finally ステートメント](try-catch-finally-statement.md)
- [2 つのオブジェクトが等しいかどうかをテストする方法システムリソースの破棄 @ no__t-0
