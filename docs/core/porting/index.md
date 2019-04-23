---
title: .NET Framework から .NET Core にコードを移植する
description: 移植プロセスを理解し、.NET Framework プロジェクトを .NET Core に移植する際に役立つツールを確認します。
author: cartermp
ms.date: 12/07/2018
ms.custom: seodec18
ms.openlocfilehash: 870320c8467237e87a2675ec5cfb57647026d8ec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663233"
---
# <a name="port-your-code-from-net-framework-to-net-core"></a>.NET Framework から .NET Core にコードを移植する

.NET Framework 上で実行されるコードがある場合は、.NET Core 上でコードを実行することにも関心があるかもしれません。 ここでは、移植プロセスの概要と、コードを .NET Core に移植するときに役立つツールの一覧を示します。

## <a name="overview-of-the-porting-process"></a>移植プロセスの概要

プロジェクトを .NET Core に移植する場合、次のプロセスを実行することをお勧めします。 プロセスの各手順については、他の記事で詳しく説明します。

1. サードパーティの依存関係を識別し、理解します。

   この手順では、サードパーティの依存関係がどのようなものか、それらにどのように依存しているか、それらが .NET Core でも実行されるかどうかを確認する方法、および実行されない場合に従う手順について理解します。 またここでは、.NET Core で使われる [PackageReference](/nuget/consume-packages/package-references-in-project-files) 形式に依存関係を移行する方法についても説明しています。

2. 移植するすべてのプロジェクトを、.NET Framework 4.7.2 以降をターゲットとするように再ターゲットします。

   この手順により、.NET Core で特定の API がサポートされない場合に、.NET Framework 固有のターゲットに対して API の代替を確実に使用できます。

3. [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md)使用して、アセンブリを分析し、その結果に基づいて移植を行う計画を作成します。

   API Portability Analyzer ツールは、コンパイル済みアセンブリを分析し、レポートを生成します。これには、移植性に関する大まかな概要と、使用中の API のうちで .NET Core では利用できないものそれぞれについての内訳が記載されています。 このレポートをコードベースの分析と共に使用して、コードを移植する方法の計画を作成します。

4. テスト コードを移植します。

   .NET Core への移植はコードベースにとって大きな変更となるため、コードの移植時にテストを実行できるように、テストを移植することを強くお勧めします。 MSTest、xUnit、NUnit はすべて .NET Core をサポートしています。

5. 移植の計画を実行します。

移植プロセス中に使うと役立つツールを、次の一覧に示します。

* .NET Portability Analyzer - [コマンドライン ツール](https://github.com/Microsoft/dotnet-apiport/releases)または [Visual Studio 拡張機能](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)。アセンブリごとの問題の内訳を含む、.NET Framework と .NET Core の間のコードの移植性に関するレポートを生成できるツール チェーンです。 詳細については、[.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) に関するページをご覧ください。
* .NET API アナライザー - さまざまなプラットフォームでの C# API の互換性リスクの可能性と、非推奨の API の呼び出しを検出する Roslyn アナライザーです。 詳細については、「[.NET API アナライザー](../../standard/analyzers/api-analyzer.md)」をご覧ください。
* Reverse Package Search - 型を検索し、その型を含むパッケージを検索するための[便利な Web サービス](https://packagesearch.azurewebsites.net)。

さらに、[CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) ツールを使って、小規模なソリューションや個々のプロジェクトを .NET Core プロジェクトのファイル形式に移植してみることが可能です。

> [!WARNING] 
> CsprojToVs2017 はサードパーティ製のツールです。 すべてのプロジェクトに対してこれが動作する保証はありません。また、依存している動作に微妙な変更が生じる可能性があります。 CsprojToVs2017 は、自動化できる基本的なことを自動化するための "_開始点_" として使う必要があります。 これは、プロジェクトのファイル形式の移行に対する保証されたソリューションではありません。

>[!div class="step-by-step"]
>[次へ](net-framework-tech-unavailable.md)
