---
title: .NET Framework の構成ファイル スキーマ
ms.date: 05/01/2017
helpviewer_keywords:
- .NET Framework application configuration, configuration schema
- machine configuration files
- application configuration files, schema
- app.config files, schema
- schema configuration settings
- schemas, configuration settings
- enterprisesec.config files
- well-formed XML
- enterprisesec configuration files
- security.config files
- security [.NET Framework], configuration files
- application development [.NET Framework], schema
- XML tags
- container tags
- machine.config files
- configuration schema [.NET Framework]
- configuration settings [.NET Framework], applications
- configuration file reference [.NET Framework]
ms.assetid: 69003d39-dc8a-460c-a6be-e6d93e690b38
ms.openlocfilehash: 6ebb6487136bff567c57143e3000a20270c1f87e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705286"
---
# <a name="configuration-file-schema-for-the-net-framework"></a>.NET Framework の構成ファイル スキーマ

構成ファイルは、設定を変更し、アプリのポリシーを設定するために使用できる標準 XML ファイルです。 .NET Framework の構成スキーマは、アプリの動作を制御するために構成ファイルで使用できる要素で構成されます。 このセクションの目次は、スキーマ、起動時の階層、ランタイム、ネットワーク、およびその他の種類の構成設定を反映しています。

構成ファイルの種類、形式、および場所については、「[アプリの構成](~/docs/framework/configure-apps/index.md)」の記事を参照してください。 構成ファイルを直接編集する場合は、XML に関する知識が必要です。

> [!IMPORTANT]
> 構成ファイルの XML タグおよび属性では、大文字と小文字が区別されます。

## <a name="in-this-section"></a>このセクションの内容

[**\<configuration>** 要素](~/docs/framework/configure-apps/file-schema/configuration-element.md) すべての構成ファイルの最上位要素である `<configuration>` 要素について説明します。

[**\<assemblyBinding>** 要素](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) 構成レベルでのアセンブリ バインディング ポリシーを指定します。

[**\<linkedConfiguration>** 要素](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) インクルードする構成ファイルを指定します。

[スタートアップ設定スキーマ](~/docs/framework/configure-apps/file-schema/startup/index.md) 使用する共通言語ランタイムのバージョンを指定する要素について説明します。

[ランタイム設定スキーマ](~/docs/framework/configure-apps/file-schema/runtime/index.md) アセンブリのバインディングとランタイムの動作を構成する要素について説明します。

[ネットワーク設定スキーマ](~/docs/framework/configure-apps/file-schema/network/index.md) .NET Framework がインターネットに接続する方法を指定する要素について説明します。

[暗号設定スキーマ](~/docs/framework/configure-apps/file-schema/cryptography/index.md) アルゴリズムの表示名を、暗号化アルゴリズムを実装するクラスに割り当てる要素について説明します。

[構成セクション スキーマ](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md) カスタム設定の構成セクションを作成し、使用するための要素について説明します。

[トレースおよびデバッグ設定のスキーマ](~/docs/framework/configure-apps/file-schema/trace-debug/index.md) トレース スイッチとリスナーを指定する要素について説明します。

[コンパイラおよび言語プロバイダー設定のスキーマ](~/docs/framework/configure-apps/file-schema/compiler/index.md) 使用できる言語プロバイダーのコンパイラの構成を指定する要素について説明します。

[アプリケーション設定のスキーマ](~/docs/framework/configure-apps/file-schema/application-settings-schema.md) Windows フォームや ASP.NET アプリケーションで、アプリケーション スコープおよびユーザー スコープの設定の格納と取得を可能にする要素について説明します。

[アプリ設定スキーマ](~/docs/framework/configure-apps/file-schema/appsettings/index.md) ファイル パス、XML Web サービス URL、またはアプリケーションのその他のカスタム構成情報など、カスタム アプリケーションの設定が含まれています。

[Web 設定スキーマ](~/docs/framework/configure-apps/file-schema/web/index.md) IIS などのホスト アプリケーションと ASP.NET の連携を構成する要素も含め、Web 設定スキーマのすべての要素。 *Aspnet.config* ファイルで使用します。

[Windows フォーム構成スキーマ](winforms/index.md) マルチ モニターや高 DPI サポートなどのカスタマイズを含む、Windows フォーム アプリケーションの構成セクションのすべての要素。

[WCF 構成スキーマ](~/docs/framework/configure-apps/file-schema/wcf/index.md) WCF サービスとクライアント アプリケーションを構成できるすべての要素。

[WCF ディレクティブ構文](~/docs/framework/configure-apps/file-schema/wcf-directive/index.md) .svc コンパイラによって使用されるページ固有の属性を定義する、`@ServiceHost` ディレクティブについて説明します。

[WIF 構成スキーマ](windows-identity-foundation/index.md) Windows Identity Foundation (WIF) 構成スキーマのすべての要素。

## <a name="related-sections"></a>関連項目

[リモート処理設定スキーマ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100)) リモート処理を実装するクライアント アプリケーションとサーバー アプリケーションを構成する要素について説明します。

[ASP.NET の設定スキーマ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100)) ASP.NET Web アプリケーションの動作を制御する要素について説明します。

[Web サービス設定スキーマ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100)) ASP.NET Web サービス、およびそれらのクライアントの動作を制御する要素について説明します。

[.NET Framework アプリの構成](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100)) セキュリティ、アセンブリのバインディング、および .NET Framework のリモート処理を構成する方法について説明します。
