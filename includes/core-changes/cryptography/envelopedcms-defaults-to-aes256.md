---
ms.openlocfilehash: b965c3a975b0f2cadd906799fef1665261d96d6e
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182020"
---
### <a name="envelopedcms-defaults-to-aes-256-encryption"></a>EnvelopedCms が AES-256 暗号化を既定で使用

`EnvelopedCms` で使用される既定の対称暗号化アルゴリズムが TripleDES から AES-256 に変更されました。

#### <a name="details"></a>説明

.NET Core Preview 7 以前のバージョンでは、コンストラクターのオーバーロードを使って対称暗号化アルゴリズムを指定せずに <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> を使用してデータを暗号化する場合、データは TripleDES/3DES/3DEA/DES3-EDE アルゴリズムで暗号化されていました。

.NET Core 3.0 Preview 8 以降では ([System.Security.Cryptography.Pkcs](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/) NuGet パッケージのバージョン 4.6.0 を介して)、アルゴリズムを最新化し、既定のオプションのセキュリティを向上するために、既定のアルゴリズムが AES-256 に変更されました。 メッセージ受信者の証明書に Diffie-Hellman (非 EC) 公開キーが含まれている場合、基になるプラットフォームの制限のために、暗号化操作は、<xref:System.Security.Cryptography.CryptographicException> で失敗する可能性があります。

次のサンプル コードでは、.NET Core 3.0 Preview 7 以前で実行されている場合、データは TripleDES で暗号化され、 NET Core 3.0 Preview 8 以降で実行されている場合は AES-256 で暗号化されます。

```csharp
EnvelopedCms cms = new EnvelopedCms(content);
cms.Encrypt(recipient);
return cms.Encode();
```

#### <a name="version-introduced"></a>導入されたバージョン

3.0 Preview 8

#### <a name="recommended-action"></a>推奨される操作

この変更によって悪影響を受ける場合は、型 <xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier> を含む <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> コンストラクターで暗号化アルゴリズム識別子を明示的に指定することで、TripleDES 暗号化に戻すことができます。次に例を示します。

```csharp
Oid tripleDesOid = new Oid("1.2.840.113549.3.7", null);
AlgorithmIdentifier tripleDesIdentifier = new AlgorithmIdentifier(tripleDesOid);
EnvelopedCms cms = new EnvelopedCms(content, tripleDesIdentifier);

cms.Encrypt(recipient);
return cms.Encode()l
```

#### <a name="category"></a>カテゴリ

暗号

#### <a name="affected-apis"></a>影響を受ける API

- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.ContentInfo)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor(System.Security.Cryptography.Pkcs.ContentInfo)`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)`

-->