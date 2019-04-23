---
ms.openlocfilehash: 94fad6fe910da6c528c5e13f529a6db274e07d5c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59235696"
---
### <a name="change-in-behavior-for-taskwaitall-methods-with-time-out-arguments"></a>タイムアウト引数を持つ Task.WaitAll メソッドの動作の変更

|   |   |
|---|---|
|説明|.NET Framework 4.5 では、<xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType> の動作が、より一貫性のあるものになりました。 .NET Framework 4 では、これらのメソッドの動作に一貫性がありませんでした。 タイムアウトの期限が切れたときに、メソッドを呼び出す前に完了した、またはキャンセルされたタスクが 1 つ以上ある場合、メソッドでは <xref:System.AggregateException?displayProperty=name> 例外がスローされていました。 タイムアウトの期限が切れると、メソッド呼び出しの前に完了またはキャンセルされたタスクはなかったが、メソッド呼び出し後に 1 つ以上のタスクがこれらの状態になると、メソッドは false を返しました。<br/><br/>.NET Framework 4.5 では、これらのメソッドのオーバーロードは、タイムアウト期限が切れたときにタスクがまだ実行中であった場合は false を返し、入力タスクがキャンセルされ (メソッド呼び出しの前か後かに関わらず)、他に実行中のタスクがなかった場合に限り、<xref:System.AggregateException?displayProperty=name> 例外をスローします。|
|提案される解決策|<xref:System.Threading.Tasks.Task.WaitAll%2A> 呼び出しが呼び出される前にキャンセルされたタスクを検出する手段として <xref:System.AggregateException?displayProperty=name> がキャッチされていた場合、.NET Framework 4.6 は、すべての待機中タスクがタイムアウトの前に完了した場合に限ってスローするため、そのコードは、代わりに <xref:System.Threading.Tasks.Task.IsCanceled%2A> プロパティによって同じ検出を行う必要があります (例: .Any(t =&gt; t.IsCanceled))。|
|スコープ|マイナー|
|Version|4.5|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32,System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.TimeSpan)?displayProperty=nameWithType></li></ul>|
