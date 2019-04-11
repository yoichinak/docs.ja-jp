---
ms.openlocfilehash: cce19d6c9afa5f5ce9bb17b5b5d92f2060a08414
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2019
ms.locfileid: "58761112"
---
### <a name="currentculture-is-not-preserved-across-wpf-dispatcher-operations"></a>CurrentCulture が、複数の WPF ディスパッチャー操作にわたって維持されない

|   |   |
|---|---|
|説明|.NET Framework 4.6 以降では、<xref:System.Windows.Threading.Dispatcher?displayProperty=name> 内で <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> または <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> に加えられた変更は、そのディスパッチャー操作の終了時に失われます。 同様に、ディスパッチャー操作の外部で <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> または <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> に加えられた変更は、その操作の実行時には反映されない場合があります。具体的に言うと、<xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> と <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> の変更は、WPF UI コールバックと WPF アプリケーション内の他のコードの間でフローされない場合があるということです。これは、<xref:System.Threading.ExecutionContext?displayProperty=name> の変更によるものであり、この変更により、.NET Framework 4.6 以降を対象とするアプリでは、<xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> および <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> は実行コンテキストに格納されます。 WPF ディスパッチャー操作は、操作を開始するために使用された実行コンテキストを格納して、操作が完了したときに、以前のコンテキストを復元します。 <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> と <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> がそのコンテキストの一部になったため、ディスパッチャー操作内でそれらに加えられた変更は、操作の外部では保持されません。|
|提案される解決策|この変更による影響を受けるアプリは、望ましい <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> または <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> をフィールドに格納し、すべてのディスパッチャー操作の本体 (UI イベントのコールバック ハンドラーを含む) で、正しい <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> と <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> が設定されていることを確認することによって回避できます。 または、この WPF の変更の元となっている ExecutionContext の変更は、.NET Framework 4.6 以降を対象とするアプリのみに影響するため、.NET Framework 4.5.2 を対象とすることによって、この問題を回避できます。また、.NET Framework 4.6 以降を対象とするアプリでは、以下の互換性スイッチを設定することでこの問題を回避することができます。<pre><code class="lang-csharp">AppContext.SetSwitch(&quot;Switch.System.Globalization.NoAsyncCurrentCulture&quot;, true);&#13;&#10;</code></pre>この問題は、.NET Framework 4.6.2 の WPF で修正されました。 また、.NET Frameworks 4.6、4.6.1 では [KB 3139549](https://support.microsoft.com/kb/3139549) を通じて修正されました。 .NET Framework 4.6 以降を対象とするアプリケーションでは WPF アプリケーション (<xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name>/<xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name>) の正しい動作が自動的に取得されます。これは、ディスパッチャー操作にわたって維持されます。|
|スコープ|マイナー|
|Version|4.6|
|型|再ターゲット中|

