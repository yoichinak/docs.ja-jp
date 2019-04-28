---
title: パディングを使用した CBC モードの対称復号化に関するタイミングの脆弱性
description: 検出および暗号ブロック チェーン (CBC) モードでパディングを使用して暗号化解除の対称のタイミングの脆弱性を軽減する方法について説明します。
ms.date: 06/12/2018
author: blowdart
ms.author: mairaw
ms.openlocfilehash: 6d8c2593cdbc4bbff2b1507196989282b16aa9a8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61933901"
---
# <a name="timing-vulnerabilities-with-cbc-mode-symmetric-decryption-using-padding"></a>パディングを使用した CBC モードの対称復号化に関するタイミングの脆弱性

Microsoft は、安全を除き、暗号化テキストの整合性を確認せずに検証可能な埋め込みが適用されているときに、対称暗号化の暗号ブロック チェーン (CBC) モードで暗号化されたデータを復号化には不要になったと考えています非常に限定。状況。 この判断は、現在認識されている暗号リサーチに基づいています。 

## <a name="introduction"></a>はじめに

埋め込みの oracle 攻撃とは、攻撃者がキーを知ることがなく、データの内容を復号化には、暗号化されたデータに対する攻撃の一種です。

Oracle は参照を"なのかを"は、実行しているアクションが正しいかどうかについて、攻撃者の情報を提供します。 ボードの再生を想像してくださいまたは子カード ゲームです。 ときに当惑顔点灯笑顔で彼女は彼女と思われるため、oracle である、適切な移動を行うためについて。 、、対戦相手として使用できますこの oracle、次の操作を適切に計画します。

余白は、特定の暗号用語です。 データの暗号化に使用するアルゴリズムであり、一部の暗号は、各ブロックが固定サイズのデータのブロックで動作します。 暗号化するデータが、要素を入力する適切なサイズでない場合はこれまでに、データが埋め込まれます。 埋め込みの多くの形式では、常に存在する場合でも、元の入力が適切なサイズがその埋め込みが必要です。 これにより、余白を常に暗号化解除時に削除しても問題ありません。

次の 2 つをまとめて、パディングの oracle ソフトウェアの実装は復号化されたデータに有効な余白があるかどうかがわかります。 Oracle は、「無効な埋め込み」ことを示す値を返すように単純なものか、無効なブロックではなく有効なブロックを処理するさまざまなある程度までの時間がかかってのような複雑なものになります。

ブロック ベースの暗号化には 2 番目のブロック内のデータに最初のブロック内のデータのリレーションシップを決定すると、モードと呼ばれる、別のプロパティがあり、具合です。 CBC は、最もよく使用されるモードのいずれか。 CBC は、既知のとして初期化ベクター (IV)、初期乱数ブロックを紹介し、同じ暗号化された出力を常に生成しない同じキーを持つ、同じメッセージを暗号化するように静的な暗号化の結果と、前のブロックを結合します。

Oracle を公開するコードにわずかに変更されたメッセージを送信し、oracle では、ことを示すまでデータの送信を保持するデータが正しく、攻撃者は CBC データ構造と組み合わせて、パディングの oracle を使用できます。 この応答から、攻撃者は、バイトごとのメッセージを暗号化解除できます。

最近のコンピューターのネットワークはこのような高品質の攻撃者がリモート システム上 (0.1 ミリ秒未満) の実行の相違点の時間が非常に小さい検出できます。 成功と失敗の復号化の違いを観察するように設計されたツールからの攻撃に対して脆弱になりますが、データが改ざんされた場合にのみを正常に復号化が発生すると仮定すると、アプリケーションがあります。 このタイミングの違いは、他よりも、いくつかの言語またはライブラリでより重要なことがありますが、障害に対するアプリケーションの応答がアカウントに実行したときに、すべての言語とライブラリの実際的な脅威はこれを今すぐ信じします。

この攻撃は、暗号化されたデータを変更し、oracle と結果をテストする機能に依存しています。 暗号化されたデータへの変更を検出し、それに対するアクションは実行を拒否するのには完全に攻撃を軽減するしかありません。 これを行う標準的な方法では、データの署名を作成し、すべての操作を実行する前に、その署名を検証します。 署名は検証可能である必要があります、攻撃者が作成できないは、暗号化されたデータを変更し、変更されたデータに基づいて新しい署名の計算のそれ以外の場合。 適切なシグネチャの 1 つの一般的な型は、キー付きハッシュ メッセージ認証コード (HMAC) と呼ばれます。 HMAC は、既知の HMAC を生成する人にのみ、ユーザーの検証に秘密キーを受け取るというチェックサムと異なります。 キーを所有している、なしには、正しい HMAC を生成することはできません。 データが表示されたら、するは暗号化されたデータを取得、個別にコンピューティングいない HMAC の秘密キーを使用し、する、送信者の共有、比較が送信されるとき、いずれかに対してする HMAC 計算。 この比較は一定の時間である必要があります、それ以外の場合追加した別の検出可能な oracle では、異なる種類の攻撃を許可します。

要約すると、使用するには、CBC ブロック暗号を安全に埋め込み、データを復号化する前に一定の時間の比較を使用して検証する、HMAC (または別のデータの整合性チェック)、それらを組み合わせる必要があります。 変更されたすべてのメッセージでは、応答を生成するために同じ時間がかかる、攻撃が回避されます。

## <a name="who-is-vulnerable"></a>脆弱であります。

この脆弱性は、独自の暗号化と復号化を実行しているアプリケーションがマネージ コードとネイティブの両方に適用されます。 これが含まれている例。

- 復号化に後で、サーバー上の cookie を暗号化するアプリケーション。
- 列を持つユーザーがテーブルにデータを挿入する機能を提供するデータベース アプリケーションは、後で復号化します。
- データは、共有キーを使用して、転送中のデータを保護する暗号化に依存するアプリケーションを転送します。
- 暗号化し、「内」TLS トンネルのメッセージを復号化するアプリケーション。

だけで TLS を使用してが保護されないこれらのシナリオで注意してください。

脆弱なアプリケーションの場合:

- CBC 暗号モードを PKCS #7 または ANSI X.923 など、検証可能なパディング モードを使用してデータを復号化します。
- (MAC または非対称のデジタル署名) を使って、データの整合性チェックを実行せず、復号化を実行します。

これは、Cryptographic Message Syntax (PKCS #7/CMS) EnvelopedData 構造など、これらのプリミティブの上に抽象化の上に構築されたアプリケーションにも適用されます。

## <a name="related-areas-of-concern"></a>関連する重要な領域

Research は ISO 10126 等価では、メッセージのよく知られているか、予測可能なフッター構造内のスペースで埋められます CBC メッセージについてさらに関係する Microsoft の led が。 たとえば、W3C XML Encryption Syntax と処理の推奨事項 (xmlenc encryptedxml の互換性) の規則の下で準備のコンテンツ。 メッセージに署名し、暗号化するには、W3C ガイダンスと見なされていました適切な時点で、中に、Microsoft は常に暗号化、署名を行うようになりました推奨します。

アプリケーション開発者は常に、非対称署名キーの適用性の確認に注意してください、非対称キーと任意のメッセージの本質的な信頼関係が存在しないためです。

## <a name="details"></a>説明

従来は、両方の暗号化および HMAC または RSA 署名などの手段を使用して、重要なデータを認証することが重要合意がありました。 ただし、暗号化および認証操作をシーケンス処理する方法について明確なガイダンスは少ないがありました。 この記事に記載された脆弱性により Microsoft のガイダンスは常に「を暗号化し、サインオン」パラダイムを使用するようになりましたが。 最初に対称キーを使用してデータを暗号化し、MAC、または非対称署名、暗号化テキスト (暗号化されたデータ) を計算します。 データを復号化、逆を実行します。 最初に、MAC や、暗号化テキストの署名を確認し、暗号化を解除します。

10 年以上にわたって存在に呼ばれる「パディング oracle 攻撃」と呼ばれる脆弱性のクラスです。 これらの脆弱性を許可すると、攻撃者がデータのブロックあたり 4,096 個以下の試行を使用して、AES および 3 des などの対称ブロック アルゴリズムで暗号化されたデータを復号化します。 これらの脆弱性のため暗号をブロックするファクトの使用は、最後に検証可能な埋め込みデータを最も頻繁に使用します。 場合は、攻撃者は、暗号化テキストを改ざんし、末尾の余白の形式でエラーが発生改ざんが行われたかどうかを検出、攻撃者は、データを解読することができます、それが見つかりました。

埋め込みが ASP.NET の脆弱性など、有効かどうかに基づいて別のエラー コードを返すようサービスに実用的な攻撃されたに基づいて最初に、 [MS10 070](/security-updates/SecurityBulletins/2010/ms10-070)します。 ただし、Microsoft ようになりましたものであるが有効および無効な余白の処理間のタイミングでは、差分のみを使用して類似の攻撃を実施するは実用的であります。

すべての情報を生成せず、データの整合性を確認できます暗号化スキームは、署名を使用し、(内容) に関係なくデータの指定された長さの固定のランタイムと、署名の検証が実行されること、使用して攻撃者、[側チャネル](https://en.wikipedia.org/wiki/Side-channel_attack)します。 整合性チェックは、改ざんされたメッセージを拒否するため、埋め込み oracle 脅威が軽減されます。

## <a name="guidance"></a>ガイダンス

何よりもまず、経由でトランスポート層セキュリティ (TLS)、Secure Sockets Layer (SSL) に後続必要がある機密性のあるすべてのデータに送信することをお勧めします。

次に、アプリケーションを分析します。

- 実行しているどのような暗号化とどのような暗号化は、プラットフォームと Api を使用しているによって提供されていると正確に理解します。
- 各使用法、対称の各層であることがはっきり[ブロック暗号アルゴリズム](https://en.wikipedia.org/wiki/Block_cipher#Notable_block_ciphers)AES および 3 des、CBC モードでは、シークレット キー付きのデータの整合性チェックの使用を組み込むことなど、(、非対称の署名、HMAC する暗号モードを変更します。[認証暗号化](https://en.wikipedia.org/wiki/Authenticated_encryption)(AE) モード CCM、GCM など)。

現在の研究に基づく、一般と思われます場合、認証と暗号化の手順は、の暗号化のない AE モード別に行う、暗号文の認証 (暗号化-、-記号) が最適な一般的なオプションです。 ただし、暗号化万能型の正しい答えはありません、この一般論がプロフェッショナルな暗号技術者からのアドバイスをすぐに有向はありません。

メッセージング形式の変更が認証されていない CBC 暗号化解除を実行できないアプリケーションなどの軽減策を組み込むしようとすることが推奨されます。

- 復号化、パディングを削除するを確認または復号化を許可しません。
  - 適用された埋め込みは削除するか、無視する必要がある、負荷をアプリケーションに移動します。
  - 利点は、その他のアプリケーション データの検証ロジックに組み込むことが、埋め込みの検証と削除です。 パディングの検証とデータの検証は、定数時間で完了できます、脅威が減少します。
  - 埋め込みの解釈が認識されるメッセージの長さを変更するためもありますタイミングについてはこのアプローチから生成されます。
- ISO10126 を復号化のパディング モードを変更します。
  - ISO10126 復号化の埋め込みが PKCS7 暗号化パディングと ANSIX923 暗号化パディングの両方との互換性です。
  - モードを変更すると、ブロック全体ではなく、1 バイトを埋め込み oracle サポート技術情報が減少します。 ただし、コンテンツがある XML 要素では、終了などのよく知られているフッター場合、関連する攻撃は、メッセージの残りの部分を攻撃する続行できます。
  - これは防ぐことも、攻撃者が別のメッセージ オフセットで複数回暗号化された同じプレーン テキストを強制する状況でプレーン テキストの回復。
- ゲートするタイミングのシグナルを緩衝復号化の呼び出しの評価:
  - ホールド時間の計算の余白を含む任意のデータ セグメントに対して暗号化解除操作が行われる最大時間を超える場合の最小値が必要です。
  - ガイダンスに従い、時間の計算を行う必要があります[高解像度のタイムスタンプを取得](/windows/desktop/sysinfo/acquiring-high-resolution-time-stamps)を使用していない<xref:System.Environment.TickCount?displayProperty=nameWithType>(対象ロール-over/オーバーフロー) または 2 つのシステムのタイムスタンプ (NTP 調整の対象を削除します。エラーの場合)。
  - 時間計算する必要があります内のすべての潜在的な例外を含む、復号化操作を含む管理または末尾に埋め込まれただけでなく、C++ アプリケーションです。
  - 成功または失敗をまだ決定されていますが場合、タイミング ゲートは、有効期限が切れるときにエラーを返す必要があります。
- 認証されていない復号化を実行しているサービスは、大量の「無効」のメッセージが取得することを検出する監視が必要です。
  - このシグナルが (合法的に破損したデータ) の偽陽性と偽陰性の (分散化検出を回避するための十分に長い時間の経過と共に攻撃) の両方を実行するも留意してください。

## <a name="finding-vulnerable-code---native-applications"></a>脆弱なコードは、ネイティブ アプリケーションの検索

Windows の暗号化に対してビルドされたプログラム。[次へ] の Generation (CNG) ライブラリ:

- 復号化の呼び出しはに対する[BCryptDecrypt](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptdecrypt)を指定して、`BCRYPT_BLOCK_PADDING`フラグ。
- キー ハンドルが呼び出すことによって初期化されている[BCryptSetProperty](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptsetproperty)で[BCRYPT_CHAINING_MODE](/windows/desktop/SecCNG/cng-property-identifiers#BCRYPT_CHAINING_MODE)設定`BCRYPT_CHAIN_MODE_CBC`します。
  - `BCRYPT_CHAIN_MODE_CBC`既定値は、影響を受けるはコードに、値を割り当てることがない可能性がありますが`BCRYPT_CHAINING_MODE`します。

以前の Windows 暗号化 API に対してビルドされたプログラム。

- 復号化の呼び出しはに対する[CryptDecrypt](/windows/desktop/api/wincrypt/nf-wincrypt-cryptdecrypt)で`Final=TRUE`します。
- キー ハンドルが呼び出すことによって初期化されている[CryptSetKeyParam](/windows/desktop/api/wincrypt/nf-wincrypt-cryptsetkeyparam)で[KP_MODE](/windows/desktop/api/wincrypt/nf-wincrypt-cryptgetkeyparam)設定`CRYPT_MODE_CBC`します。
  - `CRYPT_MODE_CBC`既定値は、影響を受けるはコードに、値を割り当てることがない可能性がありますが`KP_MODE`します。

## <a name="finding-vulnerable-code---managed-applications"></a>脆弱性のあるコードの検索 - マネージ アプリケーション

- 復号化の呼び出しはに対する、<xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor>または<xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor(System.Byte[],System.Byte[])>メソッド<xref:System.Security.Cryptography.SymmetricAlgorithm?displayProperty=nameWithType>します。
  - これは、.NET 内で次の派生型が含まれていますが、サード パーティの型を含めることもできます。
    - <xref:System.Security.Cryptography.Aes>
    - <xref:System.Security.Cryptography.AesCng>
    - <xref:System.Security.Cryptography.AesCryptoServiceProvider>
    - <xref:System.Security.Cryptography.AesManaged>
    - <xref:System.Security.Cryptography.DES>
    - <xref:System.Security.Cryptography.DESCryptoServiceProvider>
    - <xref:System.Security.Cryptography.RC2>
    - <xref:System.Security.Cryptography.RC2CryptoServiceProvider>
    - <xref:System.Security.Cryptography.Rijndael>
    - <xref:System.Security.Cryptography.RijndaelManaged>
    - <xref:System.Security.Cryptography.TripleDES>
    - <xref:System.Security.Cryptography.TripleDESCng>
    - <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider>
- <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType>プロパティに設定されました<xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType>、 <xref:System.Security.Cryptography.PaddingMode.ANSIX923?displayProperty=nameWithType>、または<xref:System.Security.Cryptography.PaddingMode.ISO10126?displayProperty=nameWithType>します。
  - <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType>既定値は、影響を受けるはコードが割り当てられませんが、<xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType>プロパティ。
- <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType>プロパティに設定されました <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType>
  - <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType>既定値は、影響を受けるはコードが割り当てられませんが、<xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType>プロパティ。

## <a name="finding-vulnerable-code---cryptographic-message-syntax"></a>暗号化メッセージ構文脆弱性のあるコードの検索

暗号化されたコンテンツを持つ、CBC モードの AES (2.16.840.1.101.3.4.1.2、2.16.840.1.101.3.4.1.22、2.16.840.1.101.3.4.1.42)、DES (1.3.14.3.2.7)、3 des を使用して認証されていない、CMS EnvelopedData メッセージ (1.2.840.113549.3.7) または RC2 (1.2.840.113549.3.2) は、脆弱性もとしてメッセージ CBC モードの他のブロック暗号アルゴリズムを使用します。

ストリーム暗号は、この特定の脆弱性に影響を受けやすい中、ContentEncryptionAlgorithm 値を調べることで、常にで、データの認証を行うことをお勧めします。

Blob は、CMS EnvelopedData、マネージ アプリケーションに渡されるすべての値が検出<xref:System.Security.Cryptography.Pkcs.EnvelopedCms.Decode(System.Byte[])?displayProperty=fullName>します。

ネイティブのアプリケーションを使用して CMS ハンドルを指定した値として CMS EnvelopedData blob を検出できる[CryptMsgUpdate](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgupdate)が結果として[CMSG_TYPE_PARAM](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsggetparam)は`CMSG_ENVELOPED`CMS ハンドルや後で送信、`CMSG_CTRL_DECRYPT`命令を使用して[CryptMsgControl](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgcontrol)します。

## <a name="vulnerable-code-example---managed"></a>脆弱なコード例の管理

Cookie を読み取ってを復号化し、データの整合性チェックが表示されません。 そのため、このメソッドによって読み取られる cookie の内容は、受信したユーザーまたは暗号化された cookie の値を取得した任意の攻撃者によって攻撃があります。

```csharp
private byte[] DecryptCookie(string cookieName)
{
    HttpCookie cookie = Request.Cookies[cookieName];

    if (cookie == null)
    {
        return null;
    }

    using (ICryptoTransform decryptor = _aes.CreateDecryptor())
    using (MemoryStream memoryStream = new MemoryStream())
    using (CryptoStream cryptoStream =
        new CryptoStream(memoryStream, decryptor, CryptoStreamMode.Write))
    {
        byte[] readCookie = Convert.FromBase64String(cookie.Value);
        cryptoStream.Write(readCookie, 0, readCookie.Length);
        cryptoStream.FlushFinalBlock();
        return memoryStream.ToArray();
    }
}
```

## <a name="example-code-following-recommended-practices---managed"></a>推奨されるベスト プラクティス - マネージ コードの次の例

次のサンプル コードの非標準のメッセージ形式を使用します。

`cipher_algorithm_id || hmac_algorithm_id || hmac_tag || iv || ciphertext`

場所、`cipher_algorithm_id`と`hmac_algorithm_id`アルゴリズム識別子は、これらのアルゴリズムのアプリケーションのローカル (標準) の表現です。 これらの識別子は、ベア連結されたバイト ストリームとしての代わりに、既存のメッセージング プロトコルの他の部分で意味をようにできます。

この例では、1 つのマスター _ キーを使用して、暗号化キーと、HMAC キーの両方を派生します。 デュアル キー付きのアプリケーションにし、2 つのキーとして別の値を維持する方法の片方向キーとアプリケーションを有効にするため、利便性のためであると指定されます。 さらに、同期、HMAC キーと暗号化キーを取得できませんを保証します。

このサンプルは受け入れません、<xref:System.IO.Stream>暗号化または復号化します。 現在のデータ形式で 1 回暗号化困難なため、`hmac_tag`値の前に、暗号化テキスト。 ただし、この形式は、パーサーを単純に先頭にあるすべての固定サイズ要素に保持するために選択されました。 このデータ形式に 1 回の復号化は、実装者を GetHashAndReset を呼び出し、TransformFinalBlock を呼び出す前に結果を確認する警告が表示されますが、可能性があります。 ストリーミングの暗号化が重要な場合は、さまざまな AE モードが必要に可能性があります。

```csharp
// ==++==
//
//   Copyright (c) Microsoft Corporation.  All rights reserved.
//
//   Shared under the terms of the Microsoft Public License,
//   https://opensource.org/licenses/MS-PL
//
// ==--==

using System;
using System.Diagnostics;
using System.IO;
using System.Runtime.CompilerServices;
using System.Security.Cryptography;

namespace Microsoft.Examples.Cryptography
{
    public enum AeCipher : byte
    {
        Unknown,
        Aes256CbcPkcs7,
    }

    public enum AeMac : byte
    {
        Unknown,
        HMACSHA256,
        HMACSHA384,
    }

    /// <summary>
    /// Provides extension methods to make HashAlgorithm look like .NET Core's
    /// IncrementalHash
    /// </summary>
    internal static class IncrementalHashExtensions
    {
        public static void AppendData(this HashAlgorithm hash, byte[] data)
        {
            hash.TransformBlock(data, 0, data.Length, null, 0);
        }

        public static void AppendData(
            this HashAlgorithm hash,
            byte[] data,
            int offset,
            int length)
        {
            hash.TransformBlock(data, offset, length, null, 0);
        }

        public static byte[] GetHashAndReset(this HashAlgorithm hash)
        {
            hash.TransformFinalBlock(Array.Empty<byte>(), 0, 0);
            return hash.Hash;
        }
    }

    public static partial class AuthenticatedEncryption
    {
        /// <summary>
        /// Use <paramref name="masterKey"/> to derive two keys (one cipher, one HMAC)
        /// to provide authenticated encryption for <paramref name="message"/>.
        /// </summary>
        /// <param name="masterKey">The master key from which other keys derive.</param>
        /// <param name="message">The message to encrypt</param>
        /// <returns>
        /// A concatenation of
        /// [cipher algorithm+chainmode+padding][mac algorithm][authtag][IV][ciphertext],
        /// suitable to be passed to <see cref="Decrypt"/>.
        /// </returns>
        /// <remarks>
        /// <paramref name="masterKey"/> should be a 128-bit (or bigger) value generated
        /// by a secure random number generator, such as the one returned from
        /// <see cref="RandomNumberGenerator.Create()"/>.
        /// This implementation chooses to block deficient inputs by length, but does not
        /// make any attempt at discerning the randomness of the key.
        ///
        /// If the master key is being input by a prompt (like a password/passphrase)
        /// then it should be properly turned into keying material via a Key Derivation
        /// Function like PBKDF2, represented by Rfc2898DeriveBytes. A 'password' should
        /// never be simply turned to bytes via an Encoding class and used as a key.
        /// </remarks>
        public static byte[] Encrypt(byte[] masterKey, byte[] message)
        {
            if (masterKey == null)
                throw new ArgumentNullException(nameof(masterKey));
            if (masterKey.Length < 16)
                throw new ArgumentOutOfRangeException(
                    nameof(masterKey),
                    "Master Key must be at least 128 bits (16 bytes)");
            if (message == null)
                throw new ArgumentNullException(nameof(message));

            // First, choose an encryption scheme.
            AeCipher aeCipher = AeCipher.Aes256CbcPkcs7;

            // Second, choose an authentication (message integrity) scheme.
            //
            // In this example we use the master key length to change from HMACSHA256 to
            // HMACSHA384, but that is completely arbitrary. This mostly represents a
            // "cryptographic needs change over time" scenario.
            AeMac aeMac = masterKey.Length < 48 ? AeMac.HMACSHA256 : AeMac.HMACSHA384;

            // It's good to be able to identify what choices were made when a message was
            // encrypted, so that the message can later be decrypted. This allows for
            // future versions to add support for new encryption schemes, but still be
            // able to read old data. A practice known as "cryptographic agility".
            //
            // This is similar in practice to PKCS#7 messaging, but this uses a
            // private-scoped byte rather than a public-scoped Object IDentifier (OID).
            // Please note that the scheme in this example adheres to no particular
            // standard, and is unlikely to survive to a more complete implementation in
            // the .NET Framework.
            //
            // You may be well-served by prepending a version number byte to this
            // message, but may want to avoid the value 0x30 (the leading byte value for
            // DER-encoded structures such as X.509 certificates and PKCS#7 messages).
            byte[] algorithmChoices = { (byte)aeCipher, (byte)aeMac };
            byte[] iv;
            byte[] cipherText;
            byte[] tag;

            // Using our algorithm choices, open an HMAC (as an authentication tag
            // generator) and a SymmetricAlgorithm which use different keys each derived
            // from the same master key.
            //
            // A custom implementation may very well have distinctly managed secret keys
            // for the MAC and cipher, this example merely demonstrates the master to
            // derived key methodology to encourage key separation from the MAC and
            // cipher keys.
            using (HMAC tagGenerator = GetMac(aeMac, masterKey))
            {
                using (SymmetricAlgorithm cipher = GetCipher(aeCipher, masterKey))
                using (ICryptoTransform encryptor = cipher.CreateEncryptor())
                {
                    // Since no IV was provided, a random one has been generated
                    // during the call to CreateEncryptor.
                    //
                    // But note that it only does the auto-generation once. If the cipher
                    // object were used again, a call to GenerateIV would have been
                    // required.
                    iv = cipher.IV;

                    cipherText = Transform(encryptor, message, 0, message.Length);
                }

                // The IV and ciphertest both need to be included in the MAC to prevent
                // tampering.
                //
                // By including the algorithm identifiers, we have technically moved from
                // simple Authenticated Encryption (AE) to Authenticated Encryption with
                // Additional Data (AEAD). By including the algorithm identifiers in the
                // MAC, it becomes harder for an attacker to change them as an attempt to
                // perform a downgrade attack.
                //
                // If you've added a data format version field, it can also be included
                // in the MAC to further inhibit an attacker's options for confusing the
                // data processor into believing the tampered message is valid.
                tagGenerator.AppendData(algorithmChoices);
                tagGenerator.AppendData(iv);
                tagGenerator.AppendData(cipherText);
                tag = tagGenerator.GetHashAndReset();
            }

            // Build the final result as the concatenation of everything except the keys.
            int totalLength =
                algorithmChoices.Length +
                tag.Length +
                iv.Length +
                cipherText.Length;

            byte[] output = new byte[totalLength];
            int outputOffset = 0;

            Append(algorithmChoices, output, ref outputOffset);
            Append(tag, output, ref outputOffset);
            Append(iv, output, ref outputOffset);
            Append(cipherText, output, ref outputOffset);

            Debug.Assert(outputOffset == output.Length);
            return output;
        }

        /// <summary>
        /// Reads a message produced by <see cref="Encrypt"/> after verifying it hasn't
        /// been tampered with.
        /// </summary>
        /// <param name="masterKey">The master key from which other keys derive.</param>
        /// <param name="cipherText">
        /// The output of <see cref="Encrypt"/>: a concatenation of a cipher ID, mac ID,
        /// authTag, IV, and cipherText.
        /// </param>
        /// <returns>The decrypted content.</returns>
        /// <exception cref="ArgumentNullException">
        /// <paramref name="masterKey"/> is <c>null</c>.
        /// </exception>
        /// <exception cref="ArgumentNullException">
        /// <paramref name="cipherText"/> is <c>null</c>.
        /// </exception>
        /// <exception cref="CryptographicException">
        /// <paramref name="cipherText"/> identifies unknown algorithms, is not long
        /// enough, fails a data integrity check, or fails to decrypt.
        /// </exception>
        /// <remarks>
        /// <paramref name="masterKey"/> should be a 128-bit (or larger) value
        /// generated by a secure random number generator, such as the one returned from
        /// <see cref="RandomNumberGenerator.Create()"/>. This implementation chooses to
        /// block deficient inputs by length, but doesn't make any attempt at
        /// discerning the randomness of the key.
        ///
        /// If the master key is being input by a prompt (like a password/passphrase),
        /// then it should be properly turned into keying material via a Key Derivation
        /// Function like PBKDF2, represented by Rfc2898DeriveBytes. A 'password' should
        /// never be simply turned to bytes via an Encoding class and used as a key.
        /// </remarks>
        public static byte[] Decrypt(byte[] masterKey, byte[] cipherText)
        {
            // This example continues the .NET practice of throwing exceptions for
            // failures. If you consider message tampering to be normal (and thus
            // "not exceptional") behavior, you may like the signature
            // bool Decrypt(byte[] messageKey, byte[] cipherText, out byte[] message)
            // better.
            if (masterKey == null)
                throw new ArgumentNullException(nameof(masterKey));
            if (masterKey.Length < 16)
                throw new ArgumentOutOfRangeException(
                    nameof(masterKey),
                    "Master Key must be at least 128 bits (16 bytes)");
            if (cipherText == null)
                throw new ArgumentNullException(nameof(cipherText));

            // The format of this message is assumed to be public, so there's no harm in
            // saying ahead of time that the message makes no sense.
            if (cipherText.Length < 2)
            {
                throw new CryptographicException();
            }

            // Use the message algorithm headers to determine what cipher algorithm and
            // MAC algorithm are going to be used. Since the same Key Derivation
            // Functions (KDFs) are being used in Decrypt as Encrypt, the keys are also
            // the same.
            AeCipher aeCipher = (AeCipher)cipherText[0];
            AeMac aeMac = (AeMac)cipherText[1];

            using (SymmetricAlgorithm cipher = GetCipher(aeCipher, masterKey))
            using (HMAC tagGenerator = GetMac(aeMac, masterKey))
            {
                int blockSizeInBytes = cipher.BlockSize / 8;
                int tagSizeInBytes = tagGenerator.HashSize / 8;
                int headerSizeInBytes = 2;
                int tagOffset = headerSizeInBytes;
                int ivOffset = tagOffset + tagSizeInBytes;
                int cipherTextOffset = ivOffset + blockSizeInBytes;
                int cipherTextLength = cipherText.Length - cipherTextOffset;
                int minLen = cipherTextOffset + blockSizeInBytes;

                // Again, the minimum length is still assumed to be public knowledge,
                // nothing has leaked out yet. The minimum length couldn't just be calculated
                // without reading the header.
                if (cipherText.Length < minLen)
                {
                    throw new CryptographicException();
                }

                // It's very important that the MAC be calculated and verified before
                // proceeding to decrypt the ciphertext, as this prevents any sort of
                // information leaking out to an attacker.
                //
                // Don't include the tag in the calculation, though.

                // First, everything before the tag (the cipher and MAC algorithm ids)
                tagGenerator.AppendData(cipherText, 0, tagOffset);

                // Skip the data before the tag and the tag, then read everything that
                // remains.
                tagGenerator.AppendData(
                    cipherText,
                    tagOffset + tagSizeInBytes,
                    cipherText.Length - tagSizeInBytes - tagOffset);

                byte[] generatedTag = tagGenerator.GetHashAndReset();

                // The time it took to get to this point has so far been a function only
                // of the length of the data, or of non-encrypted values (e.g. it could
                // take longer to prepare the *key* for the HMACSHA384 MAC than the
                // HMACSHA256 MAC, but the algorithm choice wasn't a secret).
                //
                // If the verification of the authentication tag aborts as soon as a
                // difference is found in the byte arrays then your program may be
                // acting as a timing oracle which helps an attacker to brute-force the
                // right answer for the MAC. So, it's very important that every possible
                // "no" (2^256-1 of them for HMACSHA256) be evaluated in as close to the
                // same amount of time as possible. For this, we call CryptographicEquals
                if (!CryptographicEquals(
                    generatedTag,
                    0,
                    cipherText,
                    tagOffset,
                    tagSizeInBytes))
                {
                    // Assuming every tampered message (of the same length) took the same
                    // amount of time to process, we can now safely say
                    // "this data makes no sense" without giving anything away.
                    throw new CryptographicException();
                }

                // Restore the IV into the symmetricAlgorithm instance.
                byte[] iv = new byte[blockSizeInBytes];
                Buffer.BlockCopy(cipherText, ivOffset, iv, 0, iv.Length);
                cipher.IV = iv;

                using (ICryptoTransform decryptor = cipher.CreateDecryptor())
                {
                    return Transform(
                        decryptor,
                        cipherText,
                        cipherTextOffset,
                        cipherTextLength);
                }
            }
        }

        private static byte[] Transform(
            ICryptoTransform transform,
            byte[] input,
            int inputOffset,
            int inputLength)
        {
            // Many of the implementations of ICryptoTransform report true for
            // CanTransformMultipleBlocks, and when the entire message is available in
            // one shot this saves on the allocation of the CryptoStream and the
            // intermediate structures it needs to properly chunk the message into blocks
            // (since the underlying stream won't always return the number of bytes
            // needed).
            if (transform.CanTransformMultipleBlocks)
            {
                return transform.TransformFinalBlock(input, inputOffset, inputLength);
            }

            // If our transform couldn't do multiple blocks at once, let CryptoStream
            // handle the chunking.
            using (MemoryStream messageStream = new MemoryStream())
            using (CryptoStream cryptoStream =
                new CryptoStream(messageStream, transform, CryptoStreamMode.Write))
            {
                cryptoStream.Write(input, inputOffset, inputLength);
                cryptoStream.FlushFinalBlock();
                return messageStream.ToArray();
            }
        }

        /// <summary>
        /// Open a properly configured <see cref="SymmetricAlgorithm"/> conforming to the
        /// scheme identified by <paramref name="aeCipher"/>.
        /// </summary>
        /// <param name="aeCipher">The cipher mode to open.</param>
        /// <param name="masterKey">The master key from which other keys derive.</param>
        /// <returns>
        /// A SymmetricAlgorithm object with the right key, cipher mode, and padding
        /// mode; or <c>null</c> on unknown algorithms.
        /// </returns>
        private static SymmetricAlgorithm GetCipher(AeCipher aeCipher, byte[] masterKey)
        {
            SymmetricAlgorithm symmetricAlgorithm;

            switch (aeCipher)
            {
                case AeCipher.Aes256CbcPkcs7:
                    symmetricAlgorithm = Aes.Create();
                    // While 256-bit, CBC, and PKCS7 are all the default values for these
                    // properties, being explicit helps comprehension more than it hurts
                    // performance.
                    symmetricAlgorithm.KeySize = 256;
                    symmetricAlgorithm.Mode = CipherMode.CBC;
                    symmetricAlgorithm.Padding = PaddingMode.PKCS7;
                    break;
                default:
                    // An algorithm we don't understand
                    throw new CryptographicException();
            }

            // Instead of using the master key directly, derive a key for our chosen
            // HMAC algorithm based upon the master key.
            //
            // Since none of the symmetric encryption algorithms currently in .NET
            // support key sizes greater than 256-bit, we can use HMACSHA256 with
            // NIST SP 800-108 5.1 (Counter Mode KDF) to derive a value that is
            // no smaller than the key size, then Array.Resize to trim it down as
            // needed.

            using (HMAC hmac = new HMACSHA256(masterKey))
            {
                // i=1, Label=ASCII(cipher)
                byte[] cipherKey = hmac.ComputeHash(
                    new byte[] { 1, 99, 105, 112, 104, 101, 114 });

                // Resize the array to the desired keysize. KeySize is in bits,
                // and Array.Resize wants the length in bytes.
                Array.Resize(ref cipherKey, symmetricAlgorithm.KeySize / 8);

                symmetricAlgorithm.Key = cipherKey;
            }

            return symmetricAlgorithm;
        }

        /// <summary>
        /// Open a properly configured <see cref="HMAC"/> conforming to the scheme
        /// identified by <paramref name="aeMac"/>.
        /// </summary>
        /// <param name="aeMac">The message authentication mode to open.</param>
        /// <param name="masterKey">The master key from which other keys derive.</param>
        /// <returns>
        /// An HMAC object with the proper key, or <c>null</c> on unknown algorithms.
        /// </returns>
        private static HMAC GetMac(AeMac aeMac, byte[] masterKey)
        {
            HMAC hmac;

            switch (aeMac)
            {
                case AeMac.HMACSHA256:
                    hmac = new HMACSHA256();
                    break;
                case AeMac.HMACSHA384:
                    hmac = new HMACSHA384();
                    break;
                default:
                    // An algorithm we don't understand
                    throw new CryptographicException();
            }

            // Instead of using the master key directly, derive a key for our chosen
            // HMAC algorithm based upon the master key.
            // Since the output size of the HMAC is the same as the ideal key size for
            // the HMAC, we can use the master key over a fixed input once to perform
            // NIST SP 800-108 5.1 (Counter Mode KDF):
            hmac.Key = masterKey;

            // i=1, Context=ASCII(MAC)
            byte[] newKey = hmac.ComputeHash(new byte[] { 1, 77, 65, 67 });

            hmac.Key = newKey;
            return hmac;
        }

        // A simple helper method to ensure that the offset (writePos) always moves
        // forward with new data.
        private static void Append(byte[] newData, byte[] combinedData, ref int writePos)
        {
            Buffer.BlockCopy(newData, 0, combinedData, writePos, newData.Length);
            writePos += newData.Length;
        }

        /// <summary>
        /// Compare the contents of two arrays in an amount of time which is only
        /// dependent on <paramref name="length"/>.
        /// </summary>
        /// <param name="a">An array to compare to <paramref name="b"/>.</param>
        /// <param name="aOffset">
        /// The starting position within <paramref name="a"/> for comparison.
        /// </param>
        /// <param name="b">An array to compare to <paramref name="a"/>.</param>
        /// <param name="bOffset">
        /// The starting position within <paramref name="b"/> for comparison.
        /// </param>
        /// <param name="length">
        /// The number of bytes to compare between <paramref name="a"/> and
        /// <paramref name="b"/>.</param>
        /// <returns>
        /// <c>true</c> if both <paramref name="a"/> and <paramref name="b"/> have
        /// sufficient length for the comparison and all of the applicable values are the
        /// same in both arrays; <c>false</c> otherwise.
        /// </returns>
        /// <remarks>
        /// An "insufficient data" <c>false</c> response can happen early, but otherwise
        /// a <c>true</c> or <c>false</c> response take the same amount of time.
        /// </remarks>
        [MethodImpl(MethodImplOptions.NoInlining | MethodImplOptions.NoOptimization)]
        private static bool CryptographicEquals(
            byte[] a,
            int aOffset,
            byte[] b,
            int bOffset,
            int length)
        {
            Debug.Assert(a != null);
            Debug.Assert(b != null);
            Debug.Assert(length >= 0);

            int result = 0;

            if (a.Length - aOffset < length || b.Length - bOffset < length)
            {
                return false;
            }

            unchecked
            {
                for (int i = 0; i < length; i++)
                {
                    // Bitwise-OR of subtraction has been found to have the most
                    // stable execution time.
                    //
                    // This cannot overflow because bytes are 1 byte in length, and
                    // result is 4 bytes.
                    // The OR propagates all set bytes, so the differences are only
                    // present in the lowest byte.
                    result = result | (a[i + aOffset] - b[i + bOffset]);
                }
            }

            return result == 0;
        }
    }
}
```
