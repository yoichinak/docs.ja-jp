---
ms.openlocfilehash: cdcf7f540a9ded4108121b2cd8e855687a0c7e27
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234918"
---
### <a name="signedxmlgetpublickey-returns-rsacng-on-net462-or-lightup-without-retargeting-change"></a>変更の対象を変更せず、SignedXml.GetPublicKey が net462 (または Light-Up) で RSACng を返す

|   |   |
|---|---|
|説明|.NET Framework 4.6.2 より、<xref:System.Security.Cryptography.Xml.SignedXml.GetPublicKey%2A?displayProperty=nameWithType> メソッドによって返されるオブジェクトの具象型が CryptoServiceProvider 実装から Cng 実装に変わりました。これは突然の変更ではなく、 <code>certificate.PublicKey.Key</code> の使用から、<code>certificate.GetAnyPublicKey</code> に転送する内部 <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey%2A?displayProperty=nameWithType> の使用に実装が変わったためです。|
|提案される解決策|.NET Framework 4.7.1 で実行されるアプリから、アプリの構成ファイルの [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) セクションに次の構成スイッチを追加することで、.NET Framework 4.6.1 以前のバージョンで既定で使用されていた CryptoServiceProvider 実装を使用できます。<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.Xml.SignedXmlUseLegacyCertificatePrivateKey=true&quot; /&gt;&#13;&#10;</code></pre>|
|スコープ|エッジ|
|Version|4.6.2|
|型|再ターゲット中|
|影響を受ける API|<ul><li><xref:System.Security.Cryptography.Xml.SignedXml.CheckSignatureReturningKey(System.Security.Cryptography.AsymmetricAlgorithm@)?displayProperty=nameWithType></li></ul>|
