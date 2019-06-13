---
ms.openlocfilehash: 21aa431bc0d0566b69247dd45b8cd1c87aebffdf
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2019
ms.locfileid: "66488316"
---
### <a name="product-versioning-changes-in-the-net-framework-46-and-later-versions"></a>.NET Framework 4.6 以降のバージョンでの製品のバージョン管理に関する変更点

|   |   |
|---|---|
|説明|製品のバージョン管理は、および .NET Framework 4、4.5、4.5.1、および 4.5.2 では特に、.NET Framework の以前のリリースから変更されました。 変更の詳細は次のとおりです。<ul><li>値、<code>Version</code>内のエントリ、<code>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full</code>にキーが変更された<code>4.6.xxxxx</code>の .NET Framework 4.6 とそのポイント リリースを<code>4.7.xxxxx</code>、.NET Framework 4.7 とそのポイント リリースとに<code> 4.8.xxxxx </CODE> 4.8 .NET Framework 用です。 .NET Framework 4.5、4.5.1、および 4.5.2 では、<code>4.5.xxxxx</code> という形式でした。</li><li>.NET Framework のファイルのファイルおよび製品のバージョン管理 4.0.30319.x の以前のバージョン管理スキームからに変わって 4.6.X.0、.NET Framework 4.6 とそのポイント リリース、.NET Framework 4.7 とそのポイント リリース、4.7.X.0 と 4.8.X.0 for .NET に4.8 のフレームワーク。 ファイルを右クリックしてファイルの [プロパティ] を表示すると、これらの新しい値を確認できます。</li><li><xref:System.Reflection.AssemblyFileVersionAttribute>と<xref:System.Reflection.AssemblyInformationalVersionAttribute>属性マネージ アセンブリのバージョンの値の形式で、.NET Framework 4.6 とそのポイント 4.6.X.0 リリース、4.7.X.0 に、.NET Framework 4.7 とそのポイント リリース、および .NET Framework 4.8 の 4.8.X.0 します。</li><li>.NET Framework 4.6 と以降のバージョンで、<xref:System.Environment.Version?displayProperty=nameWithType>プロパティは、固定のバージョン文字列を返します<code>4.0.30319.42000</code>します。 .NET framework 4、4.5、4.5.1、および 4.5.2 では、形式でのバージョン文字列が返されます<code>4.0.30319.xxxxx</code>ここで、 <code>xxxxx</code> 42000 より小さいは (たとえば、 &quot;4.0.30319.18010&quot;)。 アプリケーションのコードで Environment.Version プロパティに新しい依存関係を設定することは推奨されていないことに注意してください。</li></ul>詳細については、「[方法 :インストールされている .NET Framework バージョンを確認する](~/docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)」を参照してください。|
|提案される解決策|一般に、.NET Framework のランタイムのバージョンやインストール ディレクトリを検出する際、アプリケーションは推奨される技法に従う必要があります。<ul><li>.NET Framework のランタイム バージョンを検出するには、「[方法:インストールされている .NET Framework バージョンを確認する](~/docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)」を参照してください。</li><li>.NET Framework のインストール パスを確認するには、<code>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full</code> キーの <code>InstallPath</code> エントリの値を使用します。</li></ul> <blockquote> [!IMPORTANT] サブキー名は、<code>.NET Framework Setup</code> ではなく <code>NET Framework Setup</code> です。</blockquote> <ul><li>.NET Framework の共通言語ランタイムへのディレクトリ パスを確認するには、<xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory?displayProperty=nameWithType> メソッドを呼び出します。</li><li>CLR のバージョンを取得するには、<xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion?displayProperty=nameWithType> メソッドを呼び出します。 .NET Framework 4 とそのポイント リリース (.NET Framework 4.5、4.5.1、4.5.2、および .NET Framework 4.6、4.6.1、4.6.2、4.7、4.7.1) の場合、このメソッドは文字列 v4.0.30319 を返します。</li></ul>|
|スコープ|マイナー|
|Version|4.6|
|型|ランタイム|
