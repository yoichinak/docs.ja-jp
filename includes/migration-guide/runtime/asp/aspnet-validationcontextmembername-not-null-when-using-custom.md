---
ms.openlocfilehash: df13f6938ebaf8e96bb2825c1495044621f1c31b
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802626"
---
### <a name="aspnet-validationcontextmembername-is-not-null-when-using-custom-dataannotationsvalidationattribute"></a>ASP.NET カスタムの DataAnnotations.ValidationAttribute を使用すると、ValidationContext.MemberName が NULL にならない

|   |   |
|---|---|
|説明|.NET Framework 4.7.2 以前のバージョンでは、カスタムの <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType> を使用すると、<xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> プロパティで <code>null</code> が返されます。  .NET Framework 4.8 では、メンバー名が返されます。|
|提案される解決策|<xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> プロパティの既定の動作は変わりません。  <code>ValidationContext.MemberName</code> プロパティから有効な値を取得するには、アプリ構成ファイルに次の値を追加します。<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:GetValidationMemberName&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|スコープ|不明|
|Version|4.8|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType></li></ul>|

