---
ms.openlocfilehash: e605e0f2636d83745815ec4ed27bf72692f18d15
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802679"
---
### <a name="aspnet-fix-handling-of-inputattributes-and-labelattributes-for-webforms-checkbox-control"></a>ASP.NET WebForms CheckBox コントロールの InputAttributes および LabelAttributes の処理の修正

|   |   |
|---|---|
|説明|.NET Framework 4.7.2 以前のバージョンをターゲットとするアプリケーションでは、WebForms <xref:System.Web.UI.WebControls.CheckBox> コントロールにプログラムで追加された <xref:System.Web.UI.WebControls.CheckBox.InputAttributes?displayProperty=nameWithType> および <xref:System.Web.UI.WebControls.CheckBox.LabelAttributes?displayProperty=nameWithType> がポストバック後に失われます。 .NET Framework 4.8 以降のバージョンをターゲットとするアプリケーションでは、これらはポストバック後に保持されます。|
|提案される解決策|ポストバック時に属性を復元する動作を正しいものにするには、<code>targetFrameworkVersion</code> を 4.8 以降に設定します。 次に例を示します。<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;system.web&gt;&#13;&#10;&lt;httpRuntime targetFramework=&quot;4.8&quot;/&gt;&#13;&#10;&lt;/system.web&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>これより小さい値に設定した場合、または、まったく設定しない場合、適切でない古い動作が維持されます。|
|スコープ|不明|
|Version|4.8|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Web.UI.WebControls.CheckBox?displayProperty=nameWithType></li></ul>|

