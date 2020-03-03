---
ms.openlocfilehash: 62ba525a28960d96c5458aa1481e1f319d5bc875
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859371"
---
### <a name="operationcontextcurrent-may-return-null-when-called-in-a-using-clause"></a>OperationContext.Current が using 句で呼びされたときに null を返す場合がある

|   |   |
|---|---|
|説明|次のすべての条件が満たされている場合は、<xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> が <code>null</code> を返し、<xref:System.NullReferenceException> が発生する可能性があります。<ul><li><xref:System.Threading.Tasks.Task> または <xref:System.Threading.Tasks.Task%601> を返すメソッドで <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> プロパティの値を取得します。</li><li><code>using</code> 句で <xref:System.ServiceModel.OperationContextScope> オブジェクトをインスタンス化します。</li><li><code>using statement</code> 内で <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> プロパティの値を取得します。 次に例を示します。</li></ul><pre><code class="lang-csharp">using (new OperationContextScope(OperationContext.Current))&#13;&#10;{&#13;&#10;OperationContext context = OperationContext.Current;      // OperationContext.Current is null.&#13;&#10;// ...&#13;&#10;}&#13;&#10;</code></pre>|
|提案される解決策|この問題に対処するために、次の操作を行うことができます。<ul><li>次のようにコードを変更して、新しい <code>null</code> 以外の <xref:System.ServiceModel.OperationContext.Current%2A> オブジェクトをインスタンス化します。</li></ul><pre><code class="lang-csharp">OperationContext ocx = OperationContext.Current;&#13;&#10;using (new OperationContextScope(OperationContext.Current))&#13;&#10;{&#13;&#10;OperationContext.Current = new OperationContext(ocx.Channel);&#13;&#10;// ...&#13;&#10;}&#13;&#10;</code></pre><ul><li>最新の更新プログラムを .NET framework 4.6.2 にインストールするか、最新バージョンの .NET Framework にアップグレードします。 これにより、<xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> で <xref:System.Threading.ExecutionContext> のフローが無効になり、.NET Framework 4.6.1 以前のバージョンで WCF アプリケーションの動作が復元されます。 この動作は構成可能です。構成ファイルに次のアプリ設定を追加することと同じです。</li></ul><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.ServiceModel.DisableOperationContextAsyncFlow&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>この変更が望ましくなく、アプリケーションが操作コンテキスト間の実行コンテキスト フローに依存している場合は、次のようにそのフローを有効にできます。<pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.ServiceModel.DisableOperationContextAsyncFlow&quot; value=&quot;false&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|スコープ|エッジ|
|Version|4.6.2|
|型|再ターゲット中|
|影響を受ける API|<ul><li><xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType></li></ul>|

