---
ms.openlocfilehash: bc56a3437e16e5d2c9679847bf3a3035b9e34286
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "66379804"
---
### <a name="apps-published-with-clickonce-that-use-a-sha-256-code-signing-certificate-may-fail-on-windows-2003"></a>SHA-256 コード署名証明書を使用する ClickOnce で発行されたアプリケーションは、Windows 2003 では失敗することがある

|   |   |
|---|---|
|説明|この実行可能ファイルは SHA256 で署名されます。 以前は、コード署名証明書が SHA-1 か SHA-256 に関係なく、SHA 1 で署名されました。 この方法は、次の対象に適用されます。<ul><li>Visual Studio 2012 以降でビルドされたすべてのアプリケーション。</li><li>.NET Framework 4.5 がインストールされているシステム上で、Visual Studio 2010 以前でビルドされたアプリケーション。</li></ul>さらに、.NET Framework 4.5 以降が存在する場合、コンパイル対象となった .NET Framework のバージョンに関係なく、ClickOnce マニフェストはSHA-256 証明書の SHA 256 で署名されます。|
|提案される解決策|ClickOnce 実行可能ファイルの署名方法に関するこの変更は、Windows Server 2003 システムにのみ影響を及ぼします。これらのシステムには、KB 938397 をインストールする必要があります。アプリが .NET Framework 4.0 以前のバージョンをターゲットとしている場合でも、SHA-256 を使用したマニフェストの署名方法の変更により、.NET Framework 4.5 以降のバージョンに対するランタイム依存関係が導入されます。|
|スコープ|エッジ|
|Version|4.5|
|型|再ターゲット中|
