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
ms.openlocfilehash: 346a26ad5751599831d8b0d3e0497e4d488eb76c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957545"
---
# <a name="using-statement-visual-basic"></a>Using ステートメント (Visual Basic)
`Using`ブロックの先頭を宣言し、必要に応じて、ブロックが制御するシステムリソースを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
Using { resourcelist | resourceexpression }  
    [ statements ]  
End Using  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`resourcelist`|を指定`resourceexpression`しない場合は必須です。 この`Using`ブロックで制御される1つ以上のシステムリソースのリストをコンマで区切ります。|  
|`resourceexpression`|を指定`resourcelist`しない場合は必須です。 この`Using`ブロックによって制御されるシステムリソースを参照する、参照変数または式。|  
|`statements`|省略可能です。 `Using`ブロックによって実行されるステートメントのブロック。|  
|`End Using`|必須。 `Using`ブロックの定義を終了し、制御しているすべてのリソースを破棄します。|  
  
 `resourcelist`パートの各リソースには、次の構文と部分があります。  
  
 `resourcename As New resourcetype [ ( [ arglist ] ) ]`  
  
 \- または -  
  
 `resourcename As resourcetype = resourceexpression`  
  
## <a name="resourcelist-parts"></a>resourcelist パーツ  
  
|用語|定義|  
|---|---|  
|`resourcename`|必須。 `Using`ブロックが制御するシステムリソースを参照する参照変数。|  
|`New`|ステートメントがリソース`Using`を取得する場合は必須です。 リソースを既に取得している場合は、2番目の構文を使用します。|  
|`resourcetype`|必須。 リソースのクラス。 クラスは、インターフェイスを<xref:System.IDisposable>実装する必要があります。|  
|`arglist`|省略可能です。 インスタンスを作成するコンストラクターに渡す引数のリスト`resourcetype`。 「[パラメーターリスト](../../../visual-basic/language-reference/statements/parameter-list.md)」を参照してください。|  
|`resourceexpression`|必須。 の`resourcetype`要件を満たすシステムリソースを参照する変数または式。 2番目の構文を使用する場合は、 `Using`ステートメントに制御を渡す前にリソースを取得する必要があります。|  
  
## <a name="remarks"></a>Remarks  
 コードには、ファイルハンドル、COM ラッパー、SQL 接続などのアンマネージリソースが必要な場合があります。 ブロック`Using`は、コードが終了したときに、そのようなリソースの破棄を保証します。 これにより、他のコードで使用できるようになります。  
  
 マネージリソースは、.NET Framework ガベージコレクター (GC) によって破棄されます。その際、追加のコーディングは必要ありません。 マネージリソースのための`Using`ブロックは必要ありません。 ただし、ブロックを`Using`使用して、ガベージコレクターを待機するのではなく、マネージリソースを強制的に破棄することもできます。  
  
 ブロック`Using`には、取得、使用、および破棄という3つの部分があります。  
  
- *取得*とは、変数を作成して初期化し、システムリソースを参照することを意味します。 ステートメント`Using`では、1つまたは複数のリソースを取得できます。また、ブロックに入る前に1つ`Using`のリソースだけを取得して、ステートメントに指定することもできます。 を指定`resourceexpression`する場合は、 `Using`ステートメントに制御を渡す前にリソースを取得する必要があります。  
  
- *使用状況*とは、リソースにアクセスし、それらのリソースでアクションを実行することを意味します。 `Using` と`End Using`の間のステートメントは、リソースの使用状況を表します。  
  
- *破棄*とは、 <xref:System.IDisposable.Dispose%2A>で`resourcename`オブジェクトに対してメソッドを呼び出すことを意味します。 これにより、オブジェクトはリソースを完全に終了できます。 ステートメント`End Using`は、 `Using`ブロックのコントロールの下にあるリソースを破棄します。  
  
## <a name="behavior"></a>動作  
 ブロック`Using`は次のよう`Try`に動作します...ブロックがリソースを使用し、ブロックが`Finally`それらを破棄する構築。 `Finally` `Try` このため、ブロックを`Using`終了する方法に関係なく、ブロックはリソースの破棄を保証します。 これは、を除き<xref:System.StackOverflowException>、ハンドルされない例外が発生した場合にも当てはまります。  
  
 `Using`ステートメントによって取得されるすべてのリソース変数のスコープは`Using` 、ブロックに制限されます。  
  
 `Using`ステートメントで複数のシステムリソースを指定した場合、その効果は、入れ子になったブロックを別のブロック内に入れ子`Using`にした場合と同じになります。  
  
 が`resourcename` <xref:System.IDisposable.Dispose%2A>の場合、への呼び出しは行われず、例外はスローされません。 `Nothing`  
  
## <a name="structured-exception-handling-within-a-using-block"></a>Using ブロック内での構造化例外処理  
 `Using`ブロック内で発生する可能性のある例外を処理する必要がある場合は、完全`Try`な...`Finally`構築します。 `Using`ステートメントがリソースの取得に失敗した場合に対処する必要がある場合は、が`Nothing`かどうか`resourcename`をテストして確認できます。  
  
## <a name="structured-exception-handling-instead-of-a-using-block"></a>Using ブロックの代わりに構造化例外処理  
 リソースの取得をより細かく制御する必要がある場合、または`Finally`ブロック`Using`に追加のコードが必要な場合は、ブロック`Try`を...`Finally`構築。 次の例は、 `Try`の`Using` `resource`取得および破棄に相当するスケルトンと構造を示しています。  
  
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
> `Using`ブロック内のコードで`resourcename`は、オブジェクトを別の変数に割り当てることはできません。 `Using`ブロックを終了すると、リソースが破棄され、もう一方の変数は、それが指しているリソースにアクセスできなくなります。  
  
## <a name="example"></a>例  
 次の例では、test.txt という名前のファイルを作成し、ファイルに2行のテキストを書き込みます。 また、同じファイルを読み取り、テキストの行を表示します。  
  
 クラスと<xref:System.IO.TextWriter> <xref:System.IO.TextReader>クラスは<xref:System.IDisposable>インターフェイスを実装するため、コードで`Using`ステートメントを使用して、書き込み操作と読み取り操作の後でファイルが正しく閉じられるようにすることができます。  
  
 [!code-vb[VbVbalrStatements#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#50)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.IDisposable>
- [Try...Catch...Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [方法: システムリソースの破棄](../../../visual-basic/programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md)
