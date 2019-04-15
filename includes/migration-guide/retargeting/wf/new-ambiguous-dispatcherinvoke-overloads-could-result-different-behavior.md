---
ms.openlocfilehash: 4529d8040fc08b5290ac46abd1ef752086ea3aeb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234736"
---
### <a name="new-ambiguous-dispatcherinvoke-overloads-could-result-in-different-behavior"></a>新しい (あいまいな) Dispatcher.Invoke オーバーロードが、異なる動作になる可能性がある

|   |   |
|---|---|
|説明|.NET Framework 4.5 では、<xref:System.Action> 型のパラメーターを含む <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=nameWithType> に新しいオーバーロードが追加されます。 既存のコードを再コンパイルすると、コンパイラは、<xref:System.Delegate> パラメーターを持つ Dispatcher.Invoke メソッドの呼び出しを、<xref:System.Action> パラメーターを持つ Dispatcher.Invoke メソッドの呼び出しとして解決することができます。 <xref:System.Delegate> パラメーターを持つ Dispatcher.Invoke オーバーロードの呼び出しが <xref:System.Action> パラメーターを持つ Dispatcher.Invoke オーバーロードの呼び出しとして解決された場合、次のような動作の差異が生じることがあります。<ul><li>例外が発生した場合、<xref:System.Windows.Threading.Dispatcher.UnhandledExceptionFilter> イベントと <xref:System.Windows.Threading.Dispatcher.UnhandledException> イベントは発生しません。 代わりに、例外は <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException?displayProperty=name> イベントによって処理されます。</li><li><xref:System.Windows.Threading.DispatcherOperation.Result> などの一部のメンバーの呼び出しは、操作が完了するまでブロックされます。</li></ul>|
|提案される解決策|あいまいさ (および例外処理またはブロック動作における考えられる相違点) を回避するために、呼び出し元の Dispatcher.Invoke は Invoke 呼び出しの 2 番目のパラメーターとして空の object[] を渡すことで、.NET Framework 4.0 メソッドのオーバーロードに解決されるようにできます。|
|スコープ|マイナー|
|Version|4.5|
|型|再ターゲット中|
|影響を受ける API|<ul><li><xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.TimeSpan,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.TimeSpan,System.Windows.Threading.DispatcherPriority,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.Windows.Threading.DispatcherPriority,System.Object[])?displayProperty=nameWithType></li></ul>|
