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
ms.openlocfilehash: 111dba1316691b9c6c999b4c021ac06dac7c7a8d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64615103"
---
# <a name="using-statement-visual-basic"></a>Using ステートメント (Visual Basic)
宣言の先頭を`Using`をブロックし、必要に応じて、ブロックを制御するシステム リソースを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
Using { resourcelist | resourceexpression }  
    [ statements ]  
End Using  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`resourcelist`|指定しないかどうかに必要な`resourceexpression`します。 この 1 つまたは複数のシステム リソースの一覧表示`Using`コンマで区切られたコントロールをブロックします。|  
|`resourceexpression`|指定しないかどうかに必要な`resourcelist`します。 参照変数または式で制御するシステム リソースを参照する`Using`ブロックします。|  
|`statements`|省略可能です。 ステートメントのブロックを`Using`ブロックが実行されます。|  
|`End Using`|必須。 定義を終了、`Using`ブロックおよびそれによって制御されるすべてのリソースを破棄します。|  
  
 内の各リソース、`resourcelist`部分が次の構文と部分。  
  
 `resourcename As New resourcetype [ ( [ arglist ] ) ]`  
  
 - または -  
  
 `resourcename As resourcetype = resourceexpression`  
  
## <a name="resourcelist-parts"></a>resourcelist パーツ  
  
|用語|定義|  
|---|---|  
|`resourcename`|必須。 システム リソースを参照する参照変数を`Using`コントロールをブロックします。|  
|`New`|必要な場合、`Using`ステートメントがリソースを取得します。 既にリソースを取得する場合は、2 番目の構文を使用します。|  
|`resourcetype`|必須。 リソースのクラスです。 クラスを実装する必要があります、<xref:System.IDisposable>インターフェイス。|  
|`arglist`|省略可能です。 インスタンスを作成するコンス トラクターに渡す引数のリスト`resourcetype`します。 参照してください[パラメーター リスト](../../../visual-basic/language-reference/statements/parameter-list.md)します。|  
|`resourceexpression`|必須。 変数または式の要件を満たすシステム リソースを参照する`resourcetype`します。 2 番目の構文を使用する場合は、制御を渡す前に、リソースを取得する必要があります、`Using`ステートメント。|  
  
## <a name="remarks"></a>Remarks  
 場合によって、コードでは、ファイル ハンドル、COM ラッパーの場合は、SQL 接続など、アンマネージ リソースが必要です。 A`Using`られて、コードが完了すると、ブロックがそのような 1 つまたは複数のリソースの破棄を保証します。 これにより、使用するには、他のコードで使用可能なことです。  
  
 マネージ リソースは、ユーザー側で余分なコーディングなし、.NET Framework ガベージ コレクター (GC) によっての破棄されます。 必要はありません、`Using`マネージ リソースをブロックします。 ただし、引き続き使用できます、`Using`強制的にガベージ コレクターを待つのではなくマネージ リソースの破棄をブロックします。  
  
 A`Using`ブロックには 3 つの部分: 取得、使用状況、および破棄します。  
  
- *買収*変数を作成して、初期化、システムのリソースを参照することを意味します。 `Using`ステートメントが 1 つまたは複数のリソースを取得するか、ブロックに入る前に正確に 1 つのリソースを入手してに提供することができます、`Using`ステートメント。 指定した場合`resourceexpression`、制御を渡す前に、リソースを取得する必要があります、`Using`ステートメント。  
  
- *使用状況*リソースにアクセスし、それを使ってアクションを実行することを意味します。 間にあるステートメント`Using`と`End Using`リソースの使用量を表します。  
  
- *廃棄*を呼び出す方法、<xref:System.IDisposable.Dispose%2A>メソッド内のオブジェクトを`resourcename`します。 これにより、そのリソースを正常に終了するオブジェクト。 `End Using`ステートメントを下にあるリソースの破棄、`Using`ブロックのコントロール。  
  
## <a name="behavior"></a>動作  
 A`Using`ブロックのように動作する`Try`.`Finally`を構築、`Try`ブロックはリソースを使用し、`Finally`それらのブロックを破棄します。 このため、`Using`ブロックがブロックを終了する方法に関係なく、リソースの破棄を保証します。 これは、未処理の例外の場合にも当てはまりますを除き、<xref:System.StackOverflowException>します。  
  
 によって取得されたすべてのリソース変数のスコープ、`Using`ステートメントに制限されていますが、`Using`ブロックします。  
  
 1 つ以上のシステム リソースを指定する場合、`Using`を入れ子にする場合と同じステートメントでは、効果は`Using`互いをブロックします。  
  
 場合`resourcename`は`Nothing`への呼び出しがない<xref:System.IDisposable.Dispose%2A>が行われると例外はスローされません。  
  
## <a name="structured-exception-handling-within-a-using-block"></a>構造化例外処理を使用してブロック内で  
 内で発生する例外を処理する必要があるかどうか、`Using`ブロック、完全なを追加する`Try`.`Finally`を構築します。 ケースを処理する必要がある場合で、`Using`ステートメントがリソースの取得中に失敗した、かどうかをテストできます`resourcename`は`Nothing`します。  
  
## <a name="structured-exception-handling-instead-of-a-using-block"></a>構造化例外処理を使用してブロックではなく  
 場合は、リソースの取得をより細かく制御する必要がありますまたはでコードを追加する必要があります、`Finally`ブロック、書き直すことができます、`Using`としてブロック、 `Try`.`Finally`構築します。 次の例では、スケルトン`Try`と`Using`の取得と破棄に相当する構造`resource`します。  
  
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
>  内のコード、`Using`ブロック内のオブジェクトを割り当てないでください`resourcename`別の変数にします。 終了すると、`Using`ブロック、リソースが破棄され、その他の変数が指すリソースにアクセスできません。  
  
## <a name="example"></a>例  
 次の例では、log.txt という名前をファイルに 2 つの行のテキストを書き込むファイルを作成します。 例では、同じファイルを読み取るし、行のテキストが表示されます。  
  
 <xref:System.IO.TextWriter>と<xref:System.IO.TextReader>クラスの実装、<xref:System.IDisposable>インターフェイス、コードで使用できる`Using`ステートメントをファイルが正しく、書き込み後に終了し、読み取り操作ことを確認します。  
  
 [!code-vb[VbVbalrStatements#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#50)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.IDisposable>
- [Try...Catch...Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [方法: システム リソースを破棄します。](../../../visual-basic/programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md)
