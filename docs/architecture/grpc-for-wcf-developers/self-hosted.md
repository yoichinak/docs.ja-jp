---
title: 自己ホスト型 gRPC アプリケーション-WCF 開発者向け gRPC
description: ASP.NET Core gRPC アプリケーションを自己ホスト型サービスとして展開する。
ms.date: 09/02/2019
ms.openlocfilehash: ee370ba1893b060505b38ddf84235bd84433ad32
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/21/2020
ms.locfileid: "77542990"
---
# <a name="self-hosted-grpc-applications"></a>自己ホスト型 gRPC アプリケーション

ASP.NET Core 3.0 アプリケーションは Windows Server の IIS でホストできますが、HTTP/2 機能の一部がサポートされていないため、現在、IIS で gRPC アプリケーションをホストすることはできません。 この機能は、Windows Server の今後の更新プログラムの目的です。

アプリケーションを Windows サービスとして実行できます。 または、.NET Core 3.0 ホスト拡張機能の新機能により、 [systemd](https://en.wikipedia.org/wiki/Systemd)によって制御される Linux サービスとして実行できます。

## <a name="run-your-app-as-a-windows-service"></a>Windows サービスとしてのアプリの実行

Windows サービスとして実行するように ASP.NET Core アプリケーションを構成する[には、NuGet からパッケージを](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices)インストールします。 次に、`Program.cs`の `CreateHostBuilder` メソッドに `UseWindowsService` の呼び出しを追加します。

```csharp
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .UseWindowsService() // Enable running as a Windows service
        .ConfigureWebHostDefaults(webBuilder =>
        {
            webBuilder.UseStartup<Startup>();
        });
```

> [!NOTE]
> アプリケーションが Windows サービスとして実行されていない場合、`UseWindowsService` 方法では何も実行されません。

ここで、次のいずれかの方法を使用してアプリケーションを発行します。

* Visual Studio で、プロジェクトを右クリックし、ショートカットメニューの **[発行]** を選択します。
* .NET Core CLI からです。

.NET Core アプリケーションを発行するときに、*フレームワークに依存*する展開と*自己完結*型の展開のどちらを作成するかを選択できます。 フレームワークに依存する展開では、.NET Core 共有ランタイムが実行されているホストにインストールされている必要があります。 自己完結型の展開は、.NET Core ランタイムとフレームワークの完全なコピーを使用して発行され、任意のホストで実行できます。 各方法の長所と短所を含む詳細については、 [.Net Core アプリケーションの展開](../../core/deploying/index.md)に関するドキュメントを参照してください。

.NET Core 3.0 ランタイムをホストにインストールする必要がないアプリケーションの自己完結型のビルドを発行するには、アプリケーションに含めるランタイムを指定します。 `-r` (または `--runtime`) フラグを使用します。

```dotnetcli
dotnet publish -c Release -r win-x64 -o ./publish
```

フレームワークに依存するビルドを発行するには、`-r` フラグを省略します。

```dotnetcli
dotnet publish -c Release -o ./publish
```

`publish` ディレクトリの完全な内容をインストールフォルダーにコピーします。 次に、 [sc ツール](/windows/desktop/services/controlling-a-service-using-sc)を使用して、実行可能ファイルの Windows サービスを作成します。

```console
sc create MyService binPath=C:\MyService\MyService.exe
```

### <a name="log-to-the-windows-event-log"></a>Windows イベントログにログを記録する

`UseWindowsService` メソッドは、ログメッセージを Windows イベントログに書き込むログ[記録](/aspnet/core/fundamentals/logging/)プロバイダーを自動的に追加します。 `appsettings.json` または別の構成ソースの `Logging` セクションに `EventLog` エントリを追加することによって、このプロバイダーのログ記録を構成できます。 

イベントログで使用するソース名をオーバーライドするには、これらの設定で `SourceName` プロパティを設定します。 名前を指定しない場合は、既定のアプリケーション名 (通常は実行可能アセンブリ名) が使用されます。

ログ記録の詳細については、この章の最後を参照してください。

## <a name="run-your-app-as-a-linux-service-with-systemd"></a>Systemd を使用してアプリを Linux サービスとして実行する

Linux サービス (Linux 用語の*デーモン*) として実行するように ASP.NET Core アプリケーションを構成するには、NuGet から[パッケージをインストールします](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd)。 次に、`Program.cs`の `CreateHostBuilder` メソッドに `UseSystemd` の呼び出しを追加します。

```csharp
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .UseSystemd() // Enable running as a Systemd service
        .ConfigureWebHostDefaults(webBuilder =>
        {
            webBuilder.UseStartup<Startup>();
        });
```

> [!NOTE]
> アプリケーションが Linux サービスとして実行されていない場合、`UseSystemd` 方法では何も実行されません。

次に、アプリケーションを発行します。 アプリケーションは、フレームワークに依存しているか、関連する Linux ランタイム (`linux-x64`など) に対して自己完結している可能性があります。 次のいずれかの方法を使用して発行できます。

* Visual Studio で、プロジェクトを右クリックし、ショートカットメニューの **[発行]** を選択します。 
* .NET Core CLI から、次のコマンドを使用します。

  ```dotnetcli
  dotnet publish -c Release -r linux-x64 -o ./publish
  ```
  
`publish` ディレクトリの完全な内容を、Linux ホストのインストールフォルダーにコピーします。 サービスを登録するには、`/etc/systemd/system` ディレクトリに追加する、*ユニットファイル*と呼ばれる特殊なファイルが必要です。 このフォルダーにファイルを作成するには、ルートアクセス許可が必要です。 ファイルに、使用する `systemd` する識別子と、`.service` 拡張機能の名前を指定します。 たとえば、 `/etc/systemd/system/myapp.service`を使用します。

次の例に示すように、サービスファイルは INI 形式を使用します。

```ini
[Unit]
Description=My gRPC Application

[Service]
Type=notify
ExecStart=/usr/sbin/myapp

[Install]
WantedBy=multi-user.target
```

`Type=notify` プロパティは、アプリケーションが起動時およびシャットダウン時に通知する `systemd` を示します。 `WantedBy=multi-user.target` 設定を行うと、Linux システムが "ランダウン 2" に達したときにサービスが開始されます。これは、グラフィカルでないマルチユーザーシェルがアクティブであることを意味します。

`systemd` がサービスを認識する前に、その構成を再読み込みする必要があります。 `systemd` は、`systemctl` コマンドを使用して制御します。 再読み込みが完了したら、`status` サブコマンドを使用して、アプリケーションが正常に登録されたことを確認します。

```console
sudo systemctl daemon-reload
sudo systemctl status myapp
```

サービスが正しく構成されている場合は、次の出力が表示されます。

```text
myapp.service - My gRPC Application
 Loaded: loaded (/etc/systemd/system/myapp.service; disabled; vendor preset: enabled)
 Active: inactive (dead)
```

サービスを開始するには、`start` コマンドを使用します。

```console
sudo systemctl start myapp.service
```

> [!TIP]
> `systemctl start`を使用している場合、`.service` の拡張機能は省略可能です。

システムの起動時にサービスを自動的に開始するように `systemd` するには、`enable` コマンドを使用します。

```console
sudo systemctl enable myapp
```

### <a name="log-to-journald"></a>Journald にログを記録する

Linux と同等の Windows イベントログは、`systemd`の一部である構造化されたログ記録システムサービスで `journald`です。 Linux デーモンによって標準出力に書き込まれたログメッセージは、`journald`に自動的に書き込まれます。 ログ記録レベルを構成するには、ログ構成の `Console` セクションを使用します。 `UseSystemd` host builder メソッドは、journal に合わせてコンソールの出力形式を自動的に構成します。

`journald` は Linux ログの標準であるため、さまざまなツールが統合されています。 ログは、`journald` から外部ログシステムに簡単にルーティングできます。 ホストでローカルに作業している場合は、`journalctl` コマンドを使用して、コマンドラインからのログを表示できます。

```console
sudo journalctl -u myapp
```

> [!TIP]
> ホストで使用できる GUI 環境がある場合は、 *QJournalctl*や*gnome ログ*など、Linux で使用できるグラフィカルなログビューアーがいくつかあります。

`journalctl`を使用してコマンドラインから `systemd` ジャーナルを照会する方法の詳細については、 [man ページ](https://manpages.debian.org/buster/systemd/journalctl.1)を参照してください。

## <a name="https-certificates-for-self-hosted-applications"></a>自己ホスト型アプリケーションの HTTPS 証明書

運用環境で gRPC アプリケーションを実行している場合は、信頼された証明機関 (CA) からの TLS 証明書を使用する必要があります。 この CA は、パブリック CA である場合もあれば、組織の内部の ca である場合もあります。

Windows ホストでは、<xref:System.Security.Cryptography.X509Certificates.X509Store> クラスを使用して、セキュリティで保護された[証明書ストア](/windows/win32/seccrypto/managing-certificates-with-certificate-stores)から証明書を読み込むことができます。 一部の Linux ホストでは、`X509Store` クラスを OpenSSL キーストアと共に使用することもできます。

また、いずれかの[X509Certificate2 コンストラクター](xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor%2A)を使用して証明書を作成することもできます。

* 強力なパスワードで保護された `.pfx` ファイルなどのファイル
* [Azure Key Vault](https://azure.microsoft.com/services/key-vault/)などのセキュリティで保護されたストレージサービスから取得したバイナリデータ

証明書を使用するように Kestrel を構成するには、構成とコードの2つの方法があります。

### <a name="set-https-certificates-by-using-configuration"></a>構成を使用して HTTPS 証明書を設定する

構成方法では、証明書 `.pfx` ファイルのパスと Kestrel 構成セクションのパスワードを設定する必要があります。 `appsettings.json`では、これは次のようになります。

```json
{
  "Kestrel": {
    "Certificates": {
      "Default": {
        "Path": "cert.pfx",
        "Password": "DO NOT STORE PLAINTEXT PASSWORDS IN APPSETTINGS FILES"
      }
    }
  }
}
```

Azure Key Vault または Hashicorp Vault などのセキュリティで保護された構成ソースを使用して、パスワードを指定します。

> [!IMPORTANT]
> 暗号化されていないパスワードを構成ファイルに保存しないでください。

### <a name="set-https-certificates-in-code"></a>コードでの HTTPS 証明書の設定

コードで Kestrel の HTTPS を構成するには、`Program` クラスの `IWebHostBuilder` で `ConfigureKestrel` メソッドを使用します。

```csharp
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureWebHostDefaults(webBuilder =>
        {
            webBuilder.UseStartup<Startup>();
            webBuilder.ConfigureKestrel(kestrel =>
            {
                kestrel.ConfigureHttpsDefaults(https =>
                {
                    https.ServerCertificate = new X509Certificate2("mycert.pfx", "password");
                });
            });
        });
```

ここでも、`.pfx` ファイルのパスワードをに保存し、セキュリティで保護された構成ソースから取得するようにしてください。

>[!div class="step-by-step"]
>[前へ](grpc-in-production.md)
>[次へ](docker.md)
