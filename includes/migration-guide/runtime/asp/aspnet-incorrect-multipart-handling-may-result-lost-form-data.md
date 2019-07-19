---
ms.openlocfilehash: 6a99ed916e4e86e85d7ebc2d6ea36a6372c00206
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802615"
---
### <a name="aspnet-incorrect-multipart-handling-may-result-in-lost-form-data"></a>ASP.NET 正しくないマルチパート処理により、フォーム データが失われる場合がある。

|   |   |
|---|---|
|説明|.NET Framework 4.7.2 以前のバージョンをターゲットとするアプリケーションでは、ASP.Net でマルチパート境界の値が正しく解析されないために、要求の実行中にフォーム データが使用できなくなる場合があります。 .NET Framework 4.8 以降のバージョンをターゲットとするアプリケーションではマルチパート データが正しく解析されるため、要求の実行中にフォーム値を使用することができます。|
|提案される解決策|.NET Framework 4.8 以降で実行されているアプリケーションで、Framework 4.8 以降をターゲットとする場合は、<code>targetFrameworkVersion</code> 要素を使用して、区切り記号を削除するように既定の動作を変更します。 以前のフレームワークのバージョンをターゲットとするか、<code>targetFrameworkVersion</code> を使用しない場合、一部の値の末尾の区切り記号が引き続き返されます。この動作は、<code>appSetting</code> で明示的に制御することもできます。<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:UseLegacyMultiValueHeaderHandling&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|スコープ|不明|
|Version|4.8|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Web.HttpRequest.Form?displayProperty=nameWithType></li><li><xref:System.Web.HttpRequest.Files?displayProperty=nameWithType></li><li><xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType></li></ul>|

