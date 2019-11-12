---
title: .NET Core で使用できない .NET Framework テクノロジ
description: .NET Core で使用できない .NET Framework テクノロジの詳細情報
author: cartermp
ms.date: 04/30/2019
ms.openlocfilehash: 47f93268c44682afeba87cde17fe9c39811b37bf
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739718"
---
# <a name="net-framework-technologies-unavailable-on-net-core"></a>.NET Core で使用できない .NET Framework テクノロジ

.NET Framework ライブラリで使用できるテクノロジの中には、.NET Core で使用できないものがあります。たとえば、AppDomain、リモート処理、コード アクセス セキュリティ (CAS)、セキュリティ透過性、System.EnterpriseServices などです。 ライブラリがこれらのテクノロジの 1 つ以上に依存する場合、以下に示す代替方法を検討してください。 API の互換性の詳細については、「[.NET Core の破壊的変更](../compatibility/breaking-changes.md)」を参照してください。

API またはテクノロジが現在実装されていないからといって、意図的にサポートされていないわけではありません。 まず、GitHub リポジトリで .NET Core を検索して、設計によって特定の問題が発生しているかどうかを確認する必要があります。このようなインジケーターが見つからない場合は、特定の API とテクノロジを求めるために、GitHub の [dotnet/corefx リポジトリの問題](https://github.com/dotnet/corefx/issues)で問題を報告してください。 [問題内の移植に関する要求](https://github.com/dotnet/corefx/labels/port-to-core)には、`port-to-core` のラベルが付いています。

## <a name="appdomains"></a>AppDomain

アプリケーション ドメイン (AppDomains) はアプリを互いに分離します。 AppDomain ではランタイム サポートが必要で、通常は非常に高額です。 追加のアプリ ドメインを作成することはサポートされていません。 将来この機能が追加される予定はありません。 コードの分離には、代わりの方法として、プロセスの分離やコンテナーの利用をお勧めします。 アセンブリの動的読み込みには、新しい <xref:System.Runtime.Loader.AssemblyLoadContext> クラスをお勧めします。

.NET Framework からのコードの移行を簡単にするために、.NET Core では <xref:System.AppDomain> API サーフェスの一部を公開しています。 API の中には、正常に機能するもの (<xref:System.AppDomain.UnhandledException?displayProperty=nameWithType> など)、処理を行わないメンバー (<xref:System.AppDomain.SetCachePath%2A> など)、<xref:System.PlatformNotSupportedException> をスローするもの (<xref:System.AppDomain.CreateDomain%2A> など) があります。 [dotnet/corefx GitHub リポジトリ](https://github.com/dotnet/corefx)の [ `System.AppDomain` 参照ソース](https://github.com/dotnet/corefx/blob/master/src/Common/src/CoreLib/System/AppDomain.cs)に照らして使用する種類を確認し、実装バージョンに合ったブランチを選択してください。

## <a name="remoting"></a>リモート処理

.NET リモート処理は、問題のあるアーキテクチャであると判断されました。 AppDomain 間の通信で使用されていますが、今後はサポートされなくなります。 また、リモート処理にはランタイム サポートが必要で、維持するのに高いコストがかかります。 これらの理由から、.NET リモート処理は .NET Core でサポートされておらず、また将来サポートが追加される予定もありません。

プロセス間の通信では、リモート処理に代わる方法として、<xref:System.IO.Pipes> または <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> クラスなどのプロセス間通信 (IPC) メカニズムを検討してください。

マシン間では、代替方法としてネットワーク ベースのソリューションを使用してください。 可能であれば、HTTP などのオーバーヘッドの少ないプレーンテキストのプロトコルを使用してください。 この場合、ASP.NET Core で使用される Web サーバーの [Kestrel Web Server](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel) も選択できます。 また、ネットワーク ベースのマシン間のシナリオとして、<xref:System.Net.Sockets> の使用も検討してください。 その他のオプションについては、[.NET オープン ソース開発者プロジェクト:メッセージング](https://github.com/Microsoft/dotnet/blob/master/dotnet-developer-projects.md#messaging)に関する記事をご覧ください。

## <a name="code-access-security-cas"></a>コード アクセス セキュリティ (CAS)

サンド ボックスは、マネージド アプリケーションやライブラリが使用または実行するリソースの制限を、ランタイムまたはフレームワークに依存しています。これは [.NET Framework ではサポートされていない](../../framework/misc/code-access-security.md)ため、.NET Core でもサポートされていません。 .NET Framework やランタイムでは、特権の昇格が発生するケースが多すぎるため、このまま CAS をセキュリティ境界と見なすことはできません。 さらに、CAS は実装が複雑化しており、その使用を予定していないアプリケーションでは、多くの場合で正確性のパフォーマンスに影響します。

仮想化、コンテナー、ユーザー アカウントなど、オペレーティング システムが提供するセキュリティ境界を使用して、最小限の特権セットでプロセスを実行します。

## <a name="security-transparency"></a>セキュリティ透過性

CAS と同様に、セキュリティ透過性はサンドボックス コードをセキュリティ クリティカルなコードから宣言的に分離しますが、[現在はセキュリティ境界としてはサポートされていません](../../framework/misc/security-transparent-code.md)。 この機能は、Silverlight で頻繁に使用されます。 

仮想化、コンテナー、ユーザー アカウントなど、オペレーティング システムが提供するセキュリティ境界を使用して、最低限の特権セットでプロセスを実行します。

## <a name="systementerpriseservices"></a>System.EnterpriseServices

System.EnterpriseServices (COM+) は、.NET Core でサポートされていません。

>[!div class="step-by-step"]
>[次へ](third-party-deps.md)
