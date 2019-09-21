---
title: イベントの宣言と発生 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], events
- events [Visual Basic], walkthroughs
- declaring events [Visual Basic], walkthroughs
- events [Visual Basic], declaring
- events [Visual Basic], raising
- raising events [Visual Basic], walkthroughs
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
ms.openlocfilehash: 20e2b0efbf40597049c515134f408927f18d5603
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956333"
---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a>チュートリアル: イベントの宣言と発生 (Visual Basic)
このチュートリアルでは、という名前`Widget`のクラスのイベントを宣言して発生させる方法について説明します。 手順を完了したら、「チュートリアル:」のトピックを[読むことをお勧めします。イベント](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)の処理。オブジェクトからの`Widget`イベントを使用して、アプリケーションにステータス情報を提供する方法を示します。  
  
## <a name="the-widget-class"></a>ウィジェットクラス  
 `Widget`クラスがあることを前提としています。 `Widget`クラスには、実行に時間がかかる可能性があり、アプリケーションで何らかの完了インジケーターを設定できるようにするためのメソッドが用意されています。  
  
 もちろん、オブジェクトに`Widget`パーセントの [完了] ダイアログボックスを表示させることもできますが、その場合は、 `Widget`クラスを使用したすべてのプロジェクトでそのダイアログボックスがスタックします。 オブジェクトの設計では、オブジェクトを使用するアプリケーションで、フォームまたはダイアログボックスを管理するだけではなく、ユーザーインターフェイスを処理することをお勧めします。  
  
 の`Widget`目的は、他のタスクを実行することです。そのため、 `PercentDone`イベントを追加し、メソッドを`Widget`呼び出すプロシージャでそのイベントを処理し、ステータスの更新を表示することをお勧めします。 イベント`PercentDone`には、タスクを取り消すためのメカニズムも用意されています。  
  
#### <a name="to-build-the-code-example-for-this-topic"></a>このトピックのコード例をビルドするには  
  
1. 新しい Visual Basic Windows アプリケーションプロジェクトを開き、という名前`Form1`のフォームを作成します。  
  
2. 2つのボタンとラベルを`Form1`に追加します。  
  
3. 次の表のように、各オブジェクトに名前を付けます。  
  
    |オブジェクト|プロパティ|設定|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|開始タスク|  
    |`Button2`|`Text`|キャンセル|  
    |`Label`|`(Name)`, `Text`|lblPercentDone, 0|  
  
4. **[プロジェクト]** メニューの **[クラスの追加]** をクリックし`Widget.vb`て、プロジェクトにという名前のクラスを追加します。  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a>ウィジェットクラスのイベントを宣言するには  
  
- クラスでイベントを宣言するには、 `Event`キーワードを使用します。 `Widget` イベントには、 `ByVal`引数と`ByRef`引数を`Widget`指定できます`PercentDone` 。イベントの例を次に示します。  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#1)]  
  
 呼び出し元のオブジェクトがイベント`PercentDone`を受け取ると`Percent` 、引数には、完了したタスクの割合が含まれます。 引数をに`True`設定して、イベントを発生させたメソッドを取り消すことができます。 `Cancel`  
  
> [!NOTE]
> イベント引数は、プロシージャの引数と同じように宣言できます。ただし、次の例外があります。イベントに`Optional`または`ParamArray`引数を指定することはできません。また、イベントには戻り値がありません。  
  
 イベントは、 `Widget`クラスの`LongTask`メソッドによって発生します。 `PercentDone` `LongTask`2つの引数を取ります。メソッドが処理を実行している時間の長さと、 `LongTask` `PercentDone`イベントを発生させるために一時停止するまでの最小時間間隔を偽装します。  
  
#### <a name="to-raise-the-percentdone-event"></a>PercentDone イベントを発生させるには  
  
1. このクラスで使用さ`Timer`れるプロパティへのアクセスを簡単に`Imports`するには、ステートメントを`Class Widget`クラスモジュールの宣言セクションの先頭に追加します。  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#2)]  
  
2. `Widget` クラスに次のコードを追加します。  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#3)]  
  
 アプリケーションが`LongTask`メソッドを呼び出すと、 `Widget`クラスは秒`PercentDone`ごと`MinimumInterval`にイベントを発生させます。 イベントが返されるとき`LongTask`に、 `Cancel`引数がに`True`設定されているかどうかを確認します。  
  
 ここでは、いくつかの免責事項が必要です。 わかりやすく`LongTask`するために、この手順では、タスクの実行時間を事前に把握していることを前提としています。 これはほとんどの場合、そうではありません。 タスクを均等なサイズのチャンクに分割することは困難です。多くの場合、ユーザーにとって最も重要なのは、何かが発生したことを示す前にが経過した時間だけです。  
  
 このサンプルの別の欠陥が発見された可能性があります。 プロパティ`Timer`は、深夜から経過した秒数を返します。そのため、深夜の直前にアプリケーションが開始された場合は、アプリケーションが停止します。 時間を測定するためのより慎重なアプローチは、このような境界条件を考慮に入れるか、など`Now`のプロパティを使用して完全に回避することです。  
  
 `Widget`クラスでイベントを発生させることができるようになったので、次のチュートリアルに進むことができます。 [チュートリアル: イベントの処理は、 `PercentDone`を`WithEvents`使用してイベントハンドラーをイベントに関連付ける方法を示します。](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>
- <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>
- [チュートリアル: イベントの処理](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)
- [イベント](../../../../visual-basic/programming-guide/language-features/events/index.md)
