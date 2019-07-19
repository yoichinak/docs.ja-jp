---
ms.openlocfilehash: 2b768047a8b08501a8de4666d240072318427f28
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803450"
---
### <a name="managed-cryptography-classes-do-not-throw-a-cryptographyexception-in-fips-mode"></a>FIPS モードのマネージド暗号クラスで CryptographyException がスローされない

|   |   |
|---|---|
|説明|.NET Framework 4.7.2 以前のバージョンでは、システムの暗号化ライブラリが FIPS モードで構成されていると、<xref:System.Security.Cryptography.SHA256Managed> などのマネージド暗号化プロバイダー クラスで <xref:System.Security.Cryptography.CryptographicException> がスローされます。 これらの例外がスローされるのは、マネージド バージョンが FIPS (Federal Information Processing Standards) 140-2 の認定を受けていないためであり、また、FIPS ルールに基づく承認の対象と見なされなかった暗号アルゴリズムをブロックするためです。  少数の開発者は開発用コンピューターを FIPS モードで利用するため、これらの例外は運用システムでのみ頻繁にスローされます。.NET Framework 4.8 以降のバージョンをターゲットとするアプリケーションでは、より新しい緩いポリシーに自動的に切り替えられるため、そのような場合、<xref:System.Security.Cryptography.CryptographicException> が既定でスローされなくなりました。 代わりに、マネージド暗号化クラスでは、暗号化操作がシステムの暗号化ライブラリにリダイレクトされます。 このポリシー変更により、開発者環境と運用環境での混乱を招く可能性のある違いは実質的になくなり、ネイティブ コンポーネントとマネージド コンポーネントは同じ暗号化ポリシーの下で動作するようになります。|
|提案される解決策|この動作が望ましくない場合は、それを選択せずに、以前の動作を復元し、次の [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 構成設定を、アプリケーション構成ファイルの [<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) セクションに追加することで、<xref:System.Security.Cryptography.CryptographicException> が FIPS モードでスローされるようにすることができます。<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.UseLegacyFipsThrow=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>アプリケーションのターゲットが .NET Framework 4.7.2 以前である場合は、次の [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 構成設定を、アプリケーション構成ファイルの [<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) セクションに追加することで、この変更を選択することもできます。<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.UseLegacyFipsThrow=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|スコープ|エッジ|
|Version|4.8|
|型|再ターゲット中|
|影響を受ける API|<ul><li><xref:System.Security.Cryptography.AesManaged?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.MD5Cng?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.MD5CryptoServiceProvider?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RC2CryptoServiceProvider?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RijndaelManaged?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RIPEMD160Managed?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.SHA1Managed?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.SHA256Managed?displayProperty=nameWithType></li></ul>|

