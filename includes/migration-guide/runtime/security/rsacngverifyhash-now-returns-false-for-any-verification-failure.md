---
ms.openlocfilehash: 7d60578ac2913037e1cdeda329f06f9a4986574d
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67857523"
---
### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a>RSACng.VerifyHash で検証が失敗した場合に False が返されるようになった

|   |   |
|---|---|
|説明|.NET Framework 4.6.2 以降では、署名自体の形式が正しくない場合、このメソッドでは <strong>False</strong> が返されます。 今すぐ false を返しますの検証に失敗しました。 .NET Framework 4.6 および 4.6.1 では、メソッドによってスローされる、<xref:System.Security.Cryptography.CryptographicException?displayProperty=name>署名自体が正しくフォーマットされている場合。|
|提案される解決策|検証が失敗し、メソッドで <strong>False</strong> が返される場合は、代わりにその実行が <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> の処理に依存するコードが実行される必要があります。|
|スコープ|マイナー|
|Version|4.6.2|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|

