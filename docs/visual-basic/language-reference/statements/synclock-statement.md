---
title: SyncLock ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.SyncLock
- SyncLock
helpviewer_keywords:
- threading [Visual Basic], locks
- SyncLock statement [Visual Basic]
- locks, threads
ms.assetid: 14501703-298f-4d43-b139-c4b6366af176
ms.openlocfilehash: 3a12c3ac7250ee2904d571406d5008d451c9dc35
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979815"
---
# <a name="synclock-statement"></a>SyncLock ステートメント
ブロックを実行する前にステートメント ブロックの排他ロックを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
SyncLock lockobject  
    [ block ]  
End SyncLock  
```  
  
## <a name="parts"></a>指定項目  
 `lockobject`  
 必須。 オブジェクト参照に評価される式。  
  
 `block`  
 任意。 ロックが取得されるときに実行されるステートメントのブロックです。  
  
 `End SyncLock`  
 終了、`SyncLock`ブロックします。  
  
## <a name="remarks"></a>Remarks  
 `SyncLock`ステートメントが複数のスレッドが同時にステートメント ブロックを実行しないことを保証します。 `SyncLock` 各スレッドが実行している他のスレッドがなくなるまで、ブロックを入力するを防ぎます。  
  
 最も一般的な用途`SyncLock`から複数のスレッドによって同時に更新されたデータを保護することです。 場合は、データを操作するステートメントは、中断することがなく完了するまで移動する必要があります、配置内でそれらを`SyncLock`ブロックします。  
  
 排他ロックによって保護されているステートメント ブロックが呼び出される場合があります、*クリティカル セクション*します。  
  
## <a name="rules"></a>ルール  
  
-   分岐します。 分岐することはできません、`SyncLock`ブロックの外側からブロックされます。  
  
-   オブジェクトの値をロックします。 値`lockobject`することはできません`Nothing`します。 使用する前に、ロック オブジェクトを作成する必要があります、`SyncLock`ステートメント。  
  
     値を変更することはできません`lockobject`の実行中に、`SyncLock`ブロックします。 メカニズムは、ロック オブジェクトが変わらないことが必要です。  
  
-   使用することはできません、 [Await](../../../visual-basic/language-reference/operators/await-operator.md)で演算子を`SyncLock`ブロックします。  
  
## <a name="behavior"></a>動作  
  
-   メカニズムです。 スレッドが達したとき、`SyncLock`ステートメントでは、評価、`lockobject`式と式によって返されるオブジェクトの排他ロックを取得するまで実行を中断します。 別のスレッドが達したとき、`SyncLock`ステートメントでは、これはロックを取得、最初のスレッドが実行されるまで、`End SyncLock`ステートメント。  
  
-   保護されたデータ。 場合`lockobject`は、`Shared`変数、排他ロック クラスの任意のインスタンス内のスレッドが実行されないように、`SyncLock`他のスレッドが実行中にブロックします。 これは、すべてのインスタンス間で共有されるデータを保護します。  
  
     場合`lockobject`インスタンス変数は、(いない`Shared`)、ロックにより、スレッドの実行を現在のインスタンスで実行できなくなります、`SyncLock`同じインスタンス内の別のスレッドと同時にブロックします。 これは、個々 のインスタンスで保持されるデータを保護します。  
  
-   取得と解放します。 A`SyncLock`ブロックのように動作を`Try...Finally`を構築、`Try`ブロックで排他ロックを取得する`lockobject`と`Finally`ブロックでは、それを解放します。 このため、`SyncLock`ブロックがブロックを終了する方法に関係なく、ロックの解放を保証します。 これはハンドルされない例外の場合にも当てはまります。  
  
-   フレームワーク。 `SyncLock`ブロックを取得し、呼び出すことによって、排他ロックを解放、`Enter`と`Exit`のメソッド、`Monitor`クラス、<xref:System.Threading>名前空間。  
  
## <a name="programming-practices"></a>プログラミング手法  
 `lockobject`式は常をクラスにのみ属しているオブジェクトを評価する必要があります。 宣言する必要があります、`Private`オブジェクト変数を現在のインスタンスに属するデータを保護または`Private Shared`オブジェクト変数をすべてのインスタンスに共通のデータを保護します。  
  
 使用しないようにする、`Me`ロックを提供するキーワードはオブジェクトのインスタンス データ。 ロック オブジェクトとしてその参照を使用できます、クラスの外部のコードに、クラスのインスタンスへの参照がある場合、`SyncLock`ブロックから、まったく異なる別のデータを保護します。 この方法で、クラスとその他のクラスでした互いにブロックの実行が関連付けられていない`SyncLock`ブロックします。 同様に、文字列をロックも問題が、同じ文字列を使用して、プロセスの他のコードが同じロックを共有します。  
  
 使用しないようにする、`Me.GetType`のロック オブジェクトを提供するメソッドは、データを共有します。 これは、ため`GetType`常に、同じを返します`Type`オブジェクトの特定のクラス名。 外部コードを呼び出すことが`GetType`クラスを使用している同じロック オブジェクトを取得します。 結果から互いをブロックしている 2 つのクラスになり、`SyncLock`ブロックします。  
  
## <a name="examples"></a>使用例  
  
### <a name="description"></a>説明  
 次の例では、メッセージの単純なリストを保持するクラスを示します。 配列内のメッセージを保持し、最後は、変数にその配列の要素を使用します。 `addAnotherMessage`プロシージャが最後の要素をインクリメントし、新しいメッセージを格納します。 これら 2 つの操作がによって保護されている、`SyncLock`と`End SyncLock`ステートメント、他のスレッドはその最後の要素をインクリメントする前に、新しいメッセージを格納する必要があるしたら、最後の要素がインクリメントされていたためです。  
  
 場合、`simpleMessageList`クラスは、そのすべてのインスタンス、変数間のメッセージの 1 つのリストを共有`messagesList`と`messagesLast`宣言`Shared`します。 この場合は、変数`messagesLock`必要もあります`Shared`、すべてのインスタンスによって使用される 1 つのロック オブジェクトがあるようにします。  
  
### <a name="code"></a>コード  
 [!code-vb[VbVbalrThreading#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/Class1.vb#1)]  
  
### <a name="description"></a>説明  
 次のコードの例では、スレッドと`SyncLock`します。 限り、`SyncLock`ステートメントが存在する、ステートメント ブロックがクリティカル セクションと`balance`決して、負の数。 コメント アウトすることができます、`SyncLock`と`End SyncLock`隠れますの効果を確認するステートメント、`SyncLock`キーワード。  
  
### <a name="code"></a>コード  
 [!code-vb[VbVbalrThreading#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/class2.vb#21)]  
  
### <a name="comments"></a>コメント  
  
## <a name="see-also"></a>関連項目

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [同期プリミティブの概要](../../../standard/threading/overview-of-synchronization-primitives.md)
