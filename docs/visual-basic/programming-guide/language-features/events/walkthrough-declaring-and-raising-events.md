---
title: 宣言と発生イベント (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], events
- events [Visual Basic], walkthroughs
- declaring events [Visual Basic], walkthroughs
- events [Visual Basic], declaring
- events [Visual Basic], raising
- raising events [Visual Basic], walkthroughs
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
ms.openlocfilehash: cab6c90947eae8abeb9387535eadb2f89e71454a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973091"
---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a>チュートリアル: 宣言と発生イベント (Visual Basic)
このチュートリアルを宣言してという名前のクラスのイベントを発生させる方法について説明`Widget`します。 手順を完了した後可能性がある、関連トピック[チュートリアル。イベントの処理](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)からのイベントを使用する方法を示す`Widget`アプリケーションで状態情報を提供するオブジェクト。  
  
## <a name="the-widget-class"></a>ウィジェット クラス  
 今のところ必要のある想定を`Widget`クラス。 `Widget`クラスにメソッドを実行するには長い時間がかかることがあり、ある種の完了のインジケーターを配置できるアプリケーションをします。  
  
 もちろん、行うことができます、`Widget`オブジェクト % 完了ダイアログ ボックスの表示が、すべてのプロジェクトを使用した場合は、そのダイアログ ボックスで、そのしするスタックは、`Widget`クラス。 オブジェクトの設計の原則は、ユーザー インターフェイス オブジェクト ハンドルを使用するアプリケーション、オブジェクトの全体的な目的は、フォームまたはダイアログ ボックスを管理する場合を除き、します。  
  
 目的は、`Widget`を追加することが、他のタスクを実行するには、`PercentDone`イベントと let プロシージャを呼び出す`Widget`メソッド処理 's イベントと表示状態を更新します。 `PercentDone`イベントは、タスクをキャンセルするためのメカニズムも提供できます。  
  
#### <a name="to-build-the-code-example-for-this-topic"></a>このトピックのコード例をビルドするには  
  
1. 新しい Visual Basic Windows アプリケーション プロジェクトを開き、という名前のフォームを作成する`Form1`します。  
  
2. 2 つのボタンとラベルを追加`Form1`します。  
  
3. 次の表のように、各オブジェクトに名前を付けます。  
  
    |オブジェクト|プロパティ|設定|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|開始タスク|  
    |`Button2`|`Text`|キャンセル|  
    |`Label`|`(Name)`, `Text`|lblPercentDone, 0|  
  
4. **プロジェクト**] メニューの [選択**クラスの追加**という名前のクラスを追加する`Widget.vb`をプロジェクトにします。  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a>ウィジェットのクラスのイベントを宣言するには  
  
- 使用して、`Event`でイベントを宣言するキーワード、`Widget`クラス。 イベントことがあります`ByVal`と`ByRef`、引数として`Widget`の`PercentDone`イベントを示します。  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#1)]  
  
 呼び出し元のオブジェクトを受信すると、 `PercentDone` 、イベント、`Percent`引数には、タスクが完了の割合が含まれています。 `Cancel`に引数を設定することができます`True`イベントを発生させたメソッドをキャンセルします。  
  
> [!NOTE]
>  例外を次のプロシージャの引数と同様に、イベント引数を宣言できます。イベントを使用できない`Optional`または`ParamArray`引数、およびイベントに戻り値がありません。  
  
 `PercentDone`イベントは、`LongTask`のメソッド、`Widget`クラス。 `LongTask` 2 つの引数: 時間の長さメソッドが行う作業、および前に最小の時間間隔を装う`LongTask`させる一時停止、`PercentDone`イベント。  
  
#### <a name="to-raise-the-percentdone-event"></a>ですイベントを発生させる  
  
1. アクセスを簡略化する、 `Timer` 、このクラスによって使用されるプロパティの追加、`Imports`クラスのモジュールの宣言セクションの先頭にステートメントの上、`Class Widget`ステートメント。  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#2)]  
  
2. `Widget` クラスに次のコードを追加します。  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#3)]  
  
 アプリケーションを呼び出すと、`LongTask`メソッド、`Widget`クラスが生成、`PercentDone`イベントすべて`MinimumInterval`秒。 イベントが返されるときに`LongTask`かどうかをチェック、`Cancel`引数に設定された`True`します。  
  
 免責事項をいくつかは、ここで必要です。 わかりやすくするため、`LongTask`プロシージャでは、事前にわかってタスクがどれくらいの時間を前提としています。 これは、ケースではほとんどありません。 何かが発生していることを示す値を取得するまでに経過する時間数では単には、多くの場合、最も重要なユーザーに、タスクを均等なサイズのチャンクに分割することは困難であり、できます。  
  
 このサンプルでは別の欠陥を発見することがあります。 `Timer`プロパティは、午前 0 時から経過した秒数を返します。 直前の午前 0 時に開始されている場合、アプリケーションとして行き詰まってそのため、します。 時間の計測をより慎重なアプローチはこのなどの境界条件を考慮に入れるに入れるかなどのプロパティを使用して`Now`します。  
  
 これで、`Widget`クラスは、イベントを発生させることができます、次のように次のチュートリアルに進むことができます。 [チュートリアル: イベントの処理](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)を使用する方法を示します`WithEvents`でイベント ハンドラーを関連付ける、`PercentDone`イベント。  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>
- <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>
- [チュートリアル: イベントの処理](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)
- [イベント](../../../../visual-basic/programming-guide/language-features/events/index.md)
