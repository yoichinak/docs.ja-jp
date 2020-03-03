---
ms.openlocfilehash: 6d9f4b630e95d9a63393da3ae0ecd83c2b994712
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859349"
---
### <a name="rsacng-now-correctly-loads-rsa-keys-of-non-standard-key-size"></a>RSACng でキー サイズが非標準の RSA キーが正しく読み込まれるようになりました

|   |   |
|---|---|
|説明|4\.6.2 より前の .NET Framework バージョンでは、RSA 証明書のキー サイズが標準ではない顧客は、拡張メソッドの <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=name> や <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=name> でそのキーにアクセスできません。  &quot;The requested key size is not supported (要求されたサイズのキーには対応していません)&quot; というメッセージと共に <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> がスローされます。 .NET Framework 4.6.2 では、この問題が修正されました。 同様に、<xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)> と <xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)> で <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> をスローすることなく非標準サイズのキーが処理されるようになりました。|
|提案される解決策|非標準サイズのキーが使用されるときに <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> がスローされるという以前の動作に依存する例外処理ロジックがある場合、そのロジックを除くことを検討してください。|
|スコープ|エッジ|
|Version|4.6.2|
|型|再ターゲット中|
|影響を受ける API|<ul><li><xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=nameWithType></li></ul>|

