---
title: 非同期アプリケーションの微調整 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 4c3e7997-a95f-4fbe-a6ac-60ba042d30b9
ms.openlocfilehash: 49e57d56c4df79cd9a3e8d5f76d6fc76ebdfa722
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958175"
---
# <a name="fine-tuning-your-async-application-visual-basic"></a>非同期アプリケーションの微調整 (Visual Basic)
<xref:System.Threading.Tasks.Task> 型を使用できるメソッドとプロパティを使用して、非同期アプリケーションに精度と柔軟性を追加できます。 このセクションのトピックでは <xref:System.Threading.CancellationToken> および `Task` などのような、重要な <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> メソッドおよび <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> の使用例を示します。  
  
 `WhenAny` と `WhenAll` を使用すると、複数のタスクをより簡単に開始し、単一のタスクを監視して、その完了を待機できます。  
  
- `WhenAny` は、コレクションのいずれかのタスクが完了すると完了するタスクを返します。  
  
     を使用`WhenAny`する例については、「[完了後の残りの非同期タスクのキャンセル (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)」および「[完了時に複数の非同期タスクを開始して処理する (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)」を参照してください。  
  
- `WhenAll` は、コレクションのすべてのタスクが完了すると完了するタスクを返します。  
  
     詳細および `WhenAll` の使用例については、「[方法: Task.whenall (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)を使用して非同期のチュートリアルを拡張します。  
  
 ここでは、次の例について説明します。  
  
- [非同期タスクまたはタスクの一覧 (Visual Basic) をキャンセル](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)します。  
  
- [一定期間後に非同期タスクをキャンセルする (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)  
  
- [完了後の残りの非同期タスクのキャンセル (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)  
  
- [複数の非同期タスクを開始し、完了時に処理する (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
> この例を実行するには、コンピューターに Visual Studio 2012 以降および .NET Framework 4.5 以降がインストールされている必要があります。  
  
 次の図が示すように、プロジェクトは、プロセスを開始するボタンとそれを取り消すボタンを含む UI を作成します。 ボタンの名前は `startButton` と `cancelButton` です。  
  
 ![[キャンセル] ボタンがある WPF ウィンドウ](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "[開始/停止] ボタンがあるダイアログ ボックス")  
  
 完全な Windows Presentation Foundation (WPF) プロジェクトは、「[Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)」 (非同期のサンプル: アプリケーションの微調整) からダウンロードできます。  
  
## <a name="see-also"></a>関連項目

- [Async および Await を使用した非同期プログラミング (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
