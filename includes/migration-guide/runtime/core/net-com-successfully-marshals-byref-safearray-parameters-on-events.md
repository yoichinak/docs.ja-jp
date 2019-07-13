---
ms.openlocfilehash: 9c72bc686e014a0bffdf272e3813358d1b29cc66
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/06/2019
ms.locfileid: "65199203"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a>.NET COM では、イベント時に ByRef SafeArray パラメーターを正常にマーシャリングします。

|   |   |
|---|---|
|説明|.NET Framework 4.7.2 以前のバージョンでは、COM イベントでの ByRef [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) パラメータ―は、ネイティブ コードに戻ってマーシャリングすることはできません。  今回の変更により、[SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) が正常にマーシャリングされるようになりました。<ul><li>[ x ] 後方互換</li></ul>|
|提案される解決策|COM イベント時に ByRef SafeArray パラメータ―を正常にマーシャリングすると、実行が中断されてしまう場合は、アプリケーション構成に次の構成の switch を追加して、このコードを無効化できます。<pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|スコープ|マイナー|
|Version|4.8|
|型|ランタイム|
