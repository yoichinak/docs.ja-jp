---
title: WPF アプリケーションを .NET Core 3.0 に移行する
description: Windows プレゼンテーション ファンデーション (WPF) アプリを .NET Core 3.0 に移行する方法について説明します。
author: mjrousos
ms.date: 09/12/2019
ms.author: mikerou
ms.openlocfilehash: f52005e7c8a6312b8c4e09a950f1f635af1894e4
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2020
ms.locfileid: "81432594"
---
# <a name="migrating-wpf-apps-to-net-core"></a>WPF アプリを .NET コアに移行する

この記事では、.NET Framework から .NET Core 3.0 に Windows プレゼンテーション ファンデーション (WPF) アプリを移行するために必要な手順について説明します。 手持ちの WPF アプリケーションを移植する必要はありませんが、プロセスを試したい場合は[、GitHub](https://github.com/dotnet/windows-desktop/tree/master/Samples/BeanTrader)で入手できる**Bean Trader**サンプル アプリを使用できます。 元のアプリ (対象となる .NET Framework 4.7.2) は、NetFx\BeanTraderClient フォルダーで使用できます。 まず、アプリの移植に必要な手順を説明し、次に**Bean Trader**サンプルに適用される特定の変更について説明します。

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

NET Core に移行するには、まず次の手順を実行する必要があります。

01. NuGet の依存関係を理解し、更新します。

    01. 形式を使用するように NuGet`<PackageReference>`依存関係をアップグレードします。
    01. NET Core または .NET 標準互換性の最上位レベルの NuGet 依存関係を確認します。
    01. NuGet パッケージを新しいバージョンにアップグレードします。
    01. NET[の依存関係を理解するには、.NET 移植性アナライザ](../../standard/analyzers/portability-analyzer.md)ーを使用します。

01. プロジェクト ファイルを新しい SDK スタイル形式に移行します。

    01. .NET コアと .NET Framework の両方を対象とするか、.NET Core のみを対象とするかを選択します。
    01. 関連するプロジェクト ファイルのプロパティと項目を新しいプロジェクト ファイルにコピーします。

01. ビルドの問題を修正します。

    01. [互換性](https://www.nuget.org/packages/Microsoft.Windows.Compatibility/)パッケージへの参照を追加します。
    01. API レベルの違いを見つけて修正します。
    01. または 以外*の app.config*セクションを`appSettings``connectionStrings`削除します。
    01. 生成されたコードを必要に応じて再生成します。

01. ランタイム テスト:

    01. 移植されたアプリが期待どおりに動作することを確認します。
    01. 例外に<xref:System.NotSupportedException>注意してください。

## <a name="about-the-sample"></a>サンプルについて

この記事では、実際の WPF アプリと同様のさまざまな依存関係を使用するため[、Bean Trader サンプル](https://github.com/dotnet/windows-desktop/tree/master/Samples/BeanTrader)アプリを参照します。 アプリは大きくはありませんが、複雑さの点で「ハローワールド」からのステップアップを意図しています。 アプリは、実際のアプリを移植しながら、ユーザーが遭遇する可能性のあるいくつかの問題を示しています。 アプリは WCF サービスと通信するため、正しく実行するには、BeanTraderServer プロジェクト (同じ GitHub リポジトリで利用可能) を実行し、BeanTraderClient の設定が正しいエンドポイントを指していることを確認する必要があります。 (デフォルトでは、このサンプルでは、サーバーが 同じマシン上で*http://localhost:8090*実行されていると仮定しています。

このサンプル アプリは、.NET Core の移植に関する課題とソリューションを示すことを目的としています。 WPF のベスト プラクティスを示すものではありません。 実際には、移植中に少なくともいくつかの興味深い課題に遭遇することを確認するために、意図的にいくつかのアンチパターンが含まれています。

## <a name="getting-ready"></a>開発の準備

.NET Framework アプリを .NET Core に移行する際の主な課題は、依存関係が異なる場合とまったく機能しないことです。 移行は以前よりずっと簡単です。多くの NuGet パッケージが .NET 標準を対象としているようになりました。 NET Core 2.0 以降では、.NET Framework と .NET Core のサーフェス領域が似ています。 それでも、NuGet パッケージと利用可能な .NET API の両方からのサポートの違いが残っています。 移行の最初の手順は、アプリの依存関係を確認し、参照が .NET Core に簡単に移行できる形式であることを確認することです。

### <a name="upgrade-to-packagereference-nuget-references"></a>NuGet`<PackageReference>`参照にアップグレード

古い .NET Framework プロジェクトでは、通常、*パッケージ.config*ファイルに NuGet の依存関係が一覧表示されます。 新しい SDK スタイルのプロジェクト ファイル形式では、NuGet パッケージを別の構成ファイルではなく csproj ファイル自体の要素として[`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files)参照します。

移行時には、-style 参照を使用`<PackageReference>`する利点が 2 つあります。

- これは、新しい .NET Core プロジェクト ファイルに必要な NuGet 参照のスタイルです。 既に を使用`<PackageReference>`している場合は、これらのプロジェクト ファイル要素をコピーして新しいプロジェクトに直接貼り付けることができます。
- packages.config ファイルとは`<PackageReference>`異なり、要素は、プロジェクトが直接依存している最上位の依存関係のみを参照します。 その他すべての推移的な NuGet パッケージは、復元時に決定され、自動生成された obj\project.assets.json ファイルに記録されます。 これにより、プロジェクトの依存関係を簡単に判断できます。

.NET Framework アプリを .NET Core に移行する最初の手順は、NuGet 参照を使用`<PackageReference>`するように更新することです。 ビジュアルスタジオはこれを簡単にします。 Visual Studio の**ソリューション エクスプローラー**でプロジェクトの*packages.config*ファイルを右クリックし、[**パッケージ.config をパッケージ参照に移行**する] を選択します。

![パッケージリファレンスへのアップグレード](./media/convert-project-from-net-framework/package-reference-migration.png)

計算された最上位レベルの NuGet 依存関係を示すダイアログが表示され、他のどの NuGet パッケージを最上位レベルに昇格するかを確認します。 これらの他のパッケージは、Bean Trader サンプルの最上位レベルである必要はありませんので、これらのボックスをすべてオフにすることができます。 次に **、[OK] を**クリックすると *、packages.config*ファイルが削除され、`<PackageReference>`プロジェクト ファイルに要素が追加されます。

`<PackageReference>`-style 参照では、NuGet パッケージをパッケージ フォルダーにローカルに格納しません。 代わりに、最適化としてグローバルに格納されます。 移行が完了したら、csproj ファイルを編集し、以前`<Analyzer>`に.から来たアナライザーを参照している要素を削除*します。\パッケージ*ディレクトリ。 心配しないで。NuGet パッケージ参照が残っているため、アナライザーはプロジェクトに含まれます。 古い packages.config スタイル`<Analyzer>`の要素をクリーンアップするだけです。

### <a name="review-nuget-packages"></a>NuGet パッケージの確認

これで、プロジェクトが依存する最上位レベルの NuGet パッケージが表示され、これらのパッケージが .NET Core で使用できるかどうかを確認できます。 パッケージが .NET Core をサポートしているかどうかを確認するには[、nuget.org](https://www.nuget.org/)への依存関係を調べます。コミュニティが作成した[fuget.org](https://www.fuget.org/)サイトでは、パッケージ情報ページの上部にこの情報が目立つように表示されます。

NET Core 3.0 を対象とする場合、.NET Core または .NET Standard を対象とするパッケージは動作します (.NET Core は .NET 標準の領域を実装しているため)。 場合によっては、使用されるパッケージの特定のバージョンは、.NET Core または .NET Standard を対象としませんが、新しいバージョンは、その対象になります。 この場合は、パッケージの最新バージョンへのアップグレードを検討する必要があります。

.NET Framework を対象とするパッケージも使用できますが、リスクが生じます。 .NET Core と .NET Framework のサーフェス領域は、多*くの場合*、依存関係が機能するほど類似しているため、.NET コアから .NET Framework への依存関係は許可されます。 ただし、パッケージが .NET Core に存在しない .NET API を使用しようとすると、ランタイム例外が発生します。 そのため、他のオプションが利用できない場合にのみ .NET Framework パッケージを参照し、これを行うとテストの負担が発生することを理解する必要があります。

.NET Core または .NET Standard を対象としないパッケージが参照されている場合は、他の方法を考える必要があります。

- 代わりに使用できる他の同様のパッケージはありますか? NuGet の作成者が個別に ' を発行する場合もあります。特に .NET Core を対象とするライブラリのコアバージョン。 エンタープライズ ライブラリ パッケージはコミュニティ発行の一例です。ネットコア」の代替案。 その他の場合は、特定のサービスの新しい SDK (パッケージ名が異なる場合もあります) は .NET Standard で使用できます。 代替手段がない場合は、.NET Framework を対象とするパッケージを使用して、.NET Core で実行した後に完全にテストする必要があることを念頭に置いて続行できます。

Bean のトレーダーのサンプルには、次の最上位の NuGet 依存関係があります。

- [**ウィンザー、バージョン 4.1.1**](https://www.castleproject.org/projects/windsor/)  

  このパッケージは .NET 標準 1.6 を対象とするため、.NET Core で動作します。

- [**コード分析.FxCop アナライザ、バージョン 2.6.3**](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.3)  
  これはメタ パッケージなので、サポートするプラットフォームはすぐには明らかではありませんが、[ドキュメントでは](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisfxcopanalyzers)、最新バージョン (2.9.2) が .NET Framework と .NET Core の両方で動作することを示しています。

- [**ニト.非同期、バージョン 4.0.1**](https://www.nuget.org/packages/Nito.AsyncEx/4.0.1)  

  このパッケージは .NET Core を対象としませんが、新しいバージョンの 5.0 は対象になります。 移行時に一般的な方法は、多くの NuGet パッケージが最近 .NET Standard サポートを追加していますが、古いバージョンのプロジェクトでは .NET Framework のみを対象とするためです。 バージョンの違いがマイナーバージョンの違いである場合、新しいバージョンにアップグレードするのは簡単です。 これはメジャー バージョンの変更であるため、パッケージに重大な変更が加えられる可能性があるため、アップグレードには注意が必要です。 しかし、前進する道がありますが、それは良いことです。

- [**MahApps.メトロ、バージョン1.6.5**](https://www.nuget.org/packages/MahApps.Metro/1.6.5)  

  このパッケージは .NET Core を対象としませんが、新しいプレリリース (2.0-alpha) を使用しています。 繰り返しますが、変更を破ることに気をつける必要がありますが、新しいパッケージは励みになります。

Bean Trader サンプルの NuGet 依存関係はすべて、ターゲットの .NET Standard/.NET Core を対象とするか、新しいバージョンを使用するため、ここでブロッキングの問題が発生する可能性は低いです。

### <a name="upgrade-nuget-packages"></a>NuGet パッケージをアップグレードする

可能であれば、この時点で (プロジェクトが .NET Framework を対象としている) 新しいバージョンを使用して .NET Core または .NET Standard のみを対象とするパッケージのバージョンをアップグレードして、互換性に関する変更を早期に検出して対処することをお勧めします。

既存の .NET Framework バージョンのアプリに重要な変更を加えたくない場合は、.NET Core を対象とする新しいプロジェクト ファイルが作成されるまで待機できます。 ただし、NuGet パッケージを .NET Core 互換バージョンにアップグレードすると、新しいプロジェクト ファイルを作成すると移行プロセスがさらに簡単になり、.NET Framework バージョンと .NET Core バージョンのアプリ間の違いが少なくなります。

Bean Trader サンプルを使用すると、必要なすべてのアップグレードを簡単に (Visual Studio の NuGet パッケージ マネージャーを使用して) 行うことができますが、1 つの例外を除いて**MahApps.Metro 1.6.5**から**2.0**へのアップグレードでは、テーマとアクセント管理 API に関連する変更が大きめになります。

理想的には、アプリは新しいバージョンのパッケージを使用するように更新されます (.NET Core で動作する可能性が高いため)。 ただし、場合によっては、実現不可能な場合があります。 これらの場合、必要な変更は簡単ではなく、このチュートリアルでは **、MahApps.Metro** 2 ではなく .NET Core 3 への移行に重点を置いているため **、MahApps.Metro**をアップグレードしないでください。 また、Bean Trader アプリは**MahApps.Metro**のごく一部しか使用しないため、これは低リスクの .NET Framework 依存関係です。 もちろん、移行が完了したらすべてが機能していることを確認するためのテストが必要です。 これが現実世界のシナリオである場合は、移行を行わないため **、MahApps.Metro**バージョン 2.0 に移行する作業を追跡する問題を提出すると、技術的な負債が残っています。

NuGet パッケージが最新バージョンに更新されると、Bean Trader サンプルのプロジェクト ファイル内の`<PackageReference>`項目グループは次のようになります。

```xml
<ItemGroup>
  <PackageReference Include="Castle.Windsor">
    <Version>4.1.1</Version>
  </PackageReference>
  <PackageReference Include="MahApps.Metro">
    <Version>1.6.5</Version>
  </PackageReference>
  <PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers">
    <Version>2.9.2</Version>
  </PackageReference>
  <PackageReference Include="Nito.AsyncEx">
    <Version>5.0.0</Version>
  </PackageReference>
</ItemGroup>
```

### <a name="net-framework-portability-analysis"></a>NET フレームワークの移植性分析

プロジェクトの NuGet 依存関係の状態を理解したら、次に考慮すべき点は .NET Framework API の依存関係です。 [NET ポータビリティ アナライザ](../../standard/analyzers/portability-analyzer.md)ー ツールは、プロジェクトで使用する .NET API のうち、他の .NET プラットフォームで使用できる .NET API を理解するのに役立ちます。

このツールは[Visual Studio プラグイン](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)、コマンド ライン[ツール](https://github.com/Microsoft/dotnet-apiport/releases)、または[シンプルな GUI](https://github.com/Microsoft/dotnet-apiport-ui)でラップされ、オプションが簡略化されます。 [「.NET Core](https://devblogs.microsoft.com/dotnet/porting-desktop-apps-to-net-core/)へのデスクトップ アプリの移植」のブログ記事の GUI を使用した .NET ポータビリティ アナライザー (API ポート) の使用について詳しくは、こちらをご覧ください。 コマンド ラインを使用する場合は、次の手順を実行します。

1. NET[ポータビリティ アナライザ](https://github.com/Microsoft/dotnet-apiport/releases)ーをまだダウンロードしていない場合は、ダウンロードしてください。
1. 移植する .NET Framework アプリが正常にビルドされることを確認します (これは、移行の前に、関係なく、この方法を使用することをお勧めします)。
1. 次のようなコマンド ラインで API ポートを実行します。

    ```console
    ApiPort.exe analyze -f <PathToBeanTraderBinaries> -r html -r excel -t ".NET Core"
    ```

    この`-f`引数は、分析するバイナリを含むパスを指定します。 引数`-r`は、必要な出力ファイル形式を指定します。 この`-t`引数は、API の使用を分析する .NET プラットフォームを指定します。 この場合は、.NET Core が必要です。

HTML レポートを開くと、最初のセクションに、分析されたすべてのバイナリと、対象プラットフォームで使用できる .NET API の割合が一覧表示されます。 割合は単独では意味がありません。 さらに役立つのは、欠落している特定の API を確認する方法です。 これを行うには、アセンブリ名を選択するか、個々のアセンブリのレポートまでスクロールします。

ソース コードを所有しているアセンブリに注目します。 たとえば、Bean Trader ApiPort レポートには多くのバイナリが記載されていますが、そのほとんどが NuGet パッケージに属しています。 `Castle.Windsor`は、.NET Core に存在しない System.Web API に依存していることを示しています。 以前に .NET Core をサポートしていることを`Castle.Windsor`確認したため、これは問題ではありません。 NuGet パッケージは、異なる .NET プラットフォームで使用するバイナリが異なるので、.NET Framework バージョン`Castle.Windsor`が System.Web API を使用するかどうかは、パッケージが .NET Standard または .NET Core を対象としている限り、無関係です ( この場合は使用します ) 。

Bean Trader サンプルでは、考慮する必要がある唯一のバイナリは**BeanTraderClient**で、レポートには.NET API が`System.ServiceModel.ClientBase<T>.Close`2`System.ServiceModel.ClientBase<T>.Open`つしか存在しない、とが表示されます。

![ビートレーダークライアントポータビリティレポート](./media/convert-project-from-net-framework/portability-report.png)

WCF クライアント API は (ほとんど) .NET Core でサポートされているため、これらの中心的な API に代わる方法が必要であるため、これらの問題がブロックされる可能性は低いです。 実際には、.NET `System.ServiceModel`Core のサーフェス領域 (を<https://apisof.net>使用して) を見ると、.NET Core に非同期の代替手段があることがわかります。

このレポートと以前の NuGet 依存関係分析に基づいて、Bean Trader サンプルを .NET Core に移行する際に大きな問題が発生する必要はないようです。 移行を実際に開始する次の手順に進みます。

## <a name="migrating-the-project-file"></a>プロジェクト ファイルの移行

アプリで新しい SDK スタイルの[プロジェクト ファイル形式](../../core/tools/csproj.md)を使用していない場合は、.NET Core を対象とするための新しいプロジェクト ファイルが必要です。 既存の csproj ファイルを置き換えたり、既存のプロジェクトを現在の状態に変更したくない場合は、.NET Core を対象とする新しい csproj ファイルを追加できます。 [複数のターゲット](../../standard/library-guidance/cross-platform-targeting.md)を持つ単一の SDK スタイルのプロジェクト ファイル (複数`<TargetFrameworks>`のターゲットを指定) を使用して、.NET Framework および .NET Core 用のアプリのバージョンをビルドできます。

新しいプロジェクト ファイルを作成するには、Visual Studio で新しい WPF プロジェクト`dotnet new wpf`を作成するか、一時ディレクトリでコマンドを使用してプロジェクト ファイルを生成し、正しい場所にコピーまたは名前を変更します。 コミュニティで作成されたツール[CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017)もあり、プロジェクトファイルの一部の移行を自動化できます。 ツールは役に立ちますが、移行のすべての詳細が正しいことを確認するために、結果を確認する必要があります。 ツールが最適に処理しない特定の領域の 1 つは *、packages.config*ファイルから NuGet パッケージを移行することです。 ツールが、引き続き*packages.config*ファイルを使用して NuGet パッケージを参照するプロジェクト`<PackageReference>`ファイルで実行される場合、`<PackageReference>`自動的に要素に移行されますが、最上位レベルのパッケージだけでなく *、すべての*パッケージの要素が追加されます。 Visual Studio を使用`<PackageReference>`して既に要素に移行している場合 (このサンプルで行ったように)、このツールは残りの変換に役立ちます。 Scott Hanselman が[csproj ファイルの移行に関するブログ記事](https://www.hanselman.com/blog/UpgradingAnExistingNETProjectFilesToTheLeanNewCSPROJFormatFromNETCore.aspx)で推奨しているように、手で移植することは教育的であり、移植するプロジェクトが少ししかない場合は、より良い結果を得ることができます。 しかし、数十または数百のプロジェクトファイルを移植する場合、[CsprojToVs2017]のようなツールが役立ちます。

Bean Trader サンプルの新しいプロジェクト ファイルを作成`dotnet new wpf`するには、一時ディレクトリで実行し、生成された *.csproj*ファイルを*BeanTraderClient*フォルダに移動し、名前を**BeanTraderClient.Core.csproj**に変更します。

新しいプロジェクト ファイル形式には、C# ファイル *、resx*ファイル、およびディレクトリ内またはディレクトリの下にある XAML ファイルが自動的に含まれるため、プロジェクト ファイルは既にほぼ完成しています。 移行を完了するには、古いプロジェクト ファイルと新しいプロジェクト ファイルを並べて開き、古いプロジェクト ファイルを調べて、そのファイルに含まれる情報を移行する必要があるかどうかを確認します。 Bean Trader サンプルケースでは、以下の項目を新しいプロジェクトにコピーする必要があります。

- `<RootNamespace>`プロパティ、 `<AssemblyName>`、`<ApplicationIcon>`および プロパティはすべてコピーする必要があります。

- Bean Trader サンプル`<GenerateAssemblyInfo>false</GenerateAssemblyInfo>`には、AssemblyInfo.cs ファイルにアセンブリ レベルの属性 ( など`[AssemblyTitle]`) が含まれているため、新しいプロジェクト ファイルにプロパティを追加する必要もあります。 既定では、新しい SDK スタイルのプロジェクトは、csproj ファイルのプロパティに基づいてこれらの属性を自動生成します。 この場合は、この場合 (自動生成された属性が AssemblyInfo.cs の属性と競合する) には、これが発生しないようにするため、自動`<GenerateAssemblyInfo>`生成された属性は で無効になります。

- *resx*ファイルは自動的に埋め込みリソース`<Resource>`として含まれますが、画像のような他の項目は含まれません。 したがって、画像ファイル`<Resource>`とアイコンファイルを埋め込むための要素をコピーします。 新しいプロジェクト ファイル形式の globbing パターンのサポートを使用して、png 参照を 1`<Resource Include="**\*.png" />`行に単純化できます。

- 同様に`<None>`、項目は自動的に含まれますが、デフォルトでは出力ディレクトリにコピーされません。 Bean Trader プロジェクトには出力`<None>`ディレクトリに*コピーされる*項目 (動作を使用`PreserveNewest`) が含まれているため、このファイルに対して自動的`<None>`に入力された項目を更新する必要があります。

  ```xml
  <None Update="BeanTrader.pfx">
    <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
  </None>
  ```

- Bean Trader サンプルには`Content`XAML ファイル (Default.Accent.xaml)`Page`が含まれています (ではなく) このファイルで定義されているテーマとアクセントは、アプリ自体に埋め込まれるのではなく、実行時にファイルの XAML から読み込まれます。 ただし、新しいプロジェクト システムでは、XAML`<Page>`ファイルであるため、このファイルは自動的に として含まれます。 そのため、XAML ファイルをページ ( )`<Page Remove="**\Default.Accent.xaml" />`として削除し、コンテンツとして追加する必要があります。

  ```xml
  <Content Include="Resources\Themes\Default.Accent.xaml">
      <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
  </Content>
  ```

- 最後に、すべての要素を含む を`<ItemGroup>`コピーして`<PackageReference>`NuGet 参照を追加します。 NuGet パッケージを .NET Core 互換バージョンにアップグレードしていない場合は、パッケージ参照が .NET Core 固有のプロジェクトに含まれるようになります。

この時点で、新しいプロジェクトを BeanTrader ソリューションに追加して、Visual Studio で開く必要があります。 **プロジェクトはソリューション エクスプローラ**で正しく表示され`dotnet restore BeanTraderClient.Core.csproj`、パッケージを正常に復元する必要があります (対象となる .NET Framework を使用している MahApps.Metro バージョンに関連する 2 つの警告が予想されます)。

両方のプロジェクト ファイルを並べて保存することもできますが (古いプロジェクトをそのまま構築する場合も望ましい場合もあります)、移行プロセスが複雑になります (2 つのプロジェクトは同じ bin フォルダと obj フォルダを使用しようとします)。 NET Core と .NET Framework の両方のターゲットをビルドする場合は`<TargetFramework>netcoreapp3.0</TargetFramework>`、`<TargetFrameworks>netcoreapp3.0;net472</TargetFrameworks>`代わりに新しいプロジェクト ファイルのプロパティを置き換えることができます。 Bean トレーダサンプルの場合は、古いプロジェクトファイル (BeanTraderClient.csproj) は不要になったため削除します。 両方のプロジェクト ファイルを保持する場合は、異なる出力パスと中間出力パスにビルドするようにしてください。

## <a name="fix-build-issues"></a>ビルドの問題を修正する

移植プロセスの 3 番目の手順は、プロジェクトをビルドすることです。 一部のアプリは、プロジェクト ファイルが SDK スタイルのプロジェクトに変換されると、既に正常にビルドされます。 アプリの場合は、おめでとうございます! ステップ 4 に進むことができます。 他のアプリは、.NET Core 用にビルドするためにいくつかの更新プログラムが必要になります。 Bean Trader`dotnet build`サンプル プロジェクトで実行する (または Visual Studio でビルドする) 場合は、多くのエラーが発生しますが、すぐに修正されます。

### <a name="systemservicemodel-references-and-microsoftwindowscompatibility"></a>サービスモデルの参照と互換性

エラーの一般的な原因は、.NET Core で使用できる API の参照が見つからないが、.NET Core アプリのメタパッケージには自動的には含まれない点です。 これに対処するには、パッケージを参照する`Microsoft.Windows.Compatibility`必要があります。 互換性パッケージには、WCF クライアント、ディレクトリ サービス、レジストリ、構成、ACL API など、Windows デスクトップ アプリで一般的な API の広範なセットが含まれています。

Bean Trader サンプルでは、ビルド エラーの大部分は型が不足<xref:System.ServiceModel>しているためです。 これらは、必要な WCF NuGet パッケージを参照することで解決できます。 WCF クライアント API は`Microsoft.Windows.Compatibility`パッケージ内に存在する API の中に存在しますが、互換性パッケージを参照すると、さらに優れたソリューションになります (API に関連する問題だけでなく、互換性パッケージが使用可能になる WCF の問題の解決策も対処するため)。 この`Microsoft.Windows.Compatibility`パッケージは、ほとんどの .NET Core 3.0 WPF および WinForms の移植シナリオで役立ちます。 NuGet 参照を に`Microsoft.Windows.Compatibility`追加した後、ビルド エラーは 1 つだけ残ります。

### <a name="cleaning-up-unused-files"></a>未使用のファイルのクリーンアップ

移行の問題の 1 つは、*すべての*ソースを自動的に含む新しい SDK スタイル のプロジェクトで取得されるビルドに以前は含まれていなかった C# および XAML ファイルに関連することがよくあります。

Bean Trader サンプルで表示される次のビルド エラーは *、OldUnusedViewModel.cs*の不適切なインターフェイス実装を参照しています。 ファイル名はヒントですが、検査では、このソースファイルが正しくないことがわかります。 元の .NET Framework プロジェクトに含まれていないため、以前は問題が発生しませんでした。 ディスク上に存在するソース ファイルが古い*csproj*に含まれていないものは、自動的にインクルードされるようになりました。

このような 1 回限りの問題では、以前の*csproj*と比較してファイルが不要であることを確認し`<Compile Remove="" />`、ソース ファイルが不要な場合は削除するのも簡単です。 この場合 *、OldUnusedViewModel.cs*削除しても安全です。

この方法で除外する必要があるソース ファイルが多数ある場合は、`<EnableDefaultCompileItems>`プロジェクト ファイルでプロパティを false に設定することで、C# ファイルの自動インクルードを無効にすることができます。 その後、古い`<Compile Include>`プロジェクト ファイルから新しいプロジェクト ファイルに項目をコピーして、含めるソースだけをビルドできます。 同様に`<EnableDefaultPageItems>`、XAML ページの自動インクルードをオフにし、1`<EnableDefaultItems>`つのプロパティで両方を制御するためにも使用できます。

### <a name="a-brief-aside-on-multi-pass-compilers"></a>マルチパスコンパイラの簡単な脇

Bean Trader サンプルから問題のあるファイルを削除すると、ビルドを再実行でき、4 つのエラーが発生します。 あなたは前に1つを持っていませんでしたか? エラーの数が増え、なぜ増えましたか? C# コンパイラは[マルチパス コンパイラ](https://docs.microsoft.com/archive/blogs/ericlippert/how-many-passes)です。 これは、各ソース ファイルを 2 回通過することを意味します。 まず、コンパイラは各ソース ファイル内のメタデータと宣言を調べ、宣言レベルの問題を特定します。 これらはあなたが修正したエラーです。 次に、コードをもう一度実行して、C# ソースを IL にビルドします。これらは、現在表示されているエラーの 2 番目のセットです。

> [!NOTE]
> C# コンパイラは[2 つ以上のパス](https://docs.microsoft.com/archive/blogs/ericlippert/how-many-passes)を実行しますが、最終的には、このような大規模なコード変更のコンパイラ エラーは 2 つの波に来る傾向があります。

### <a name="third-party-dependency-fixes-castlewindsor"></a>サードパーティの依存関係の修正 (キャッスル.ウィンザー)

一部の移行シナリオで発生する問題の別のクラスは、依存関係の .NET Framework と .NET Core バージョン間の API の違いです。 NuGet パッケージが .NET Framework と .NET 標準または .NET Core の両方を対象としている場合でも、異なる .NET ターゲットで使用するライブラリが異なる場合があります。 これにより、パッケージは多くの異なる .NET プラットフォームをサポートでき、異なる実装が必要になる場合があります。 また、異なる .NET プラットフォームを対象とする場合、ライブラリに API の違いが小さい可能性もあります。

Bean Trader サンプルで表示される次の一連のエラーは、API`Castle.Windsor`に関連しています。 NET Core Bean Trader プロジェクトでは、.NET Framework ターゲット プロジェクト (4.1.1)`Castle.Windsor`と同じバージョンを使用しますが、これら 2 つのプラットフォームの実装は若干異なります。

この場合、修正が必要な次の問題が表示されます。

1. `Castle.MicroKernel.Registration.Classes.FromThisAssembly`は .NET Core では使用できません。 ただし、同様`Classes.FromAssemblyContaining`の API が利用できるため、 の両方の`Classes.FromThisAssembly()`使用を`Classes.FromAssemblyContaining(t)`呼び出し`t`に置き換えることができます。
1. 同様に *、Bootstrapper.cs*`Castle.Windsor.Installer.FromAssembly`で。これは .NET Core では使用できません。 代わりに、その呼び出し`FromAssembly.Containing(typeof(Bootstrapper))`を に置き換えることができます。

### <a name="updating-wcf-client-usage"></a>WCF クライアントの使用状況の更新

`Castle.Windsor`違いを修正した後、.NET Core Bean Trader プロジェクトの最後のビルド`BeanTraderServiceClient`エラーは、`DuplexClientBase`から派生するメソッドが`Open`ないということです。 これは、この移行プロセスの開始時に .NET ポータビリティ アナライザによって強調表示された API であるため、これは驚くべきことではありません。 しかし、`BeanTraderServiceClient`見て見ると、より大きな問題に注意が向きます。 この WCF クライアントは[、Svcutil.exe](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)ツールによって自動生成されました。

**Svcutil によって生成された WCF クライアントは、.NET Framework で使用するためのものです。**

svcutil で生成された WCF クライアントを使用するソリューションは、.NET Core で使用するために .NET 標準互換クライアントを再生成する必要があります。 古いクライアントが動作しない主な理由の 1 つは、WCF バインドとエンドポイントを定義するためのアプリ構成に依存していることです。 NET 標準 WCF API はクロスプラットフォーム (System.Configuration API が使用できない場合) で動作するため、.NET Core および .NET 標準シナリオの WCF クライアントでは、構成ではなく、バインディングとエンドポイントをプログラムで定義する必要があります。

実際には`<system.serviceModel>`、(Svcutil または手動で作成するかどうか) のセクションに依存する WCF クライアントの使用法を変更する必要があります.NET Core で動作します。

.NET 標準互換 WCF クライアントを自動的に生成するには、次の 2 つの方法があります。

- この`dotnet-svcutil`ツールは、Svcutil が以前に動作した方法と同様の方法で WCF クライアントを生成する .NET ツールです。
- Visual Studio は、接続されたサービス機能の[WCF Web サービス参照](../../core/additional-tools/wcf-web-service-reference-guide.md)オプションを使用して WCF クライアントを生成できます。

どちらの方法でもうまくいきます。 もちろん、WCF クライアント コードを自分で記述することもできます。 このサンプルでは、Visual Studio 接続サービス機能を使用することを選択しました。 これを行うには、Visual Studio のソリューション エクスプローラーで*BeanTraderClient.Core*プロジェクトを右クリックし、[**接続されたサービス**の**追加** > ] を選択します。 次に、WCF Web サービス参照プロバイダーを選択します。 これにより、バックエンド Bean Trader Web サービスのアドレス (`localhost:8080`サーバーをローカルで実行している場合) と、生成された型の名前空間を使用する必要がある (**たとえば BeanTrader.Service**など) を指定できるダイアログが表示されます。

![WCF Web サービス参照接続済みサービス ダイアログ](./media/convert-project-from-net-framework/connected-service-dialog.png)

**[完了]** ボタンを選択すると、新しい接続済みサービス ノードがプロジェクトに追加され、そのノードの下に Reference.cs、Bean Trader サービスにアクセスするための新しい .NET Standard WCF クライアントが含まれるファイルが追加されます。 そのファイルの`GetEndpointAddress`or`GetBindingForEndpoint`メソッドを見ると、バインドとエンドポイントが (アプリの構成ではなく) プログラムによって生成されることがわかります。 「接続されたサービスの追加」機能は、必要なすべての WCF パッケージが Microsoft.Windows.Compatibility を介して含まれているため、必要とされないプロジェクト ファイル内の System.ServiceModel パッケージへの参照を追加することもできます。 追加の System.ServiceModel`<PackageReference>`項目が追加されているかどうかを確認し、追加されている場合は削除するには、csproj を確認します。

このプロジェクトには新しい WCF クライアント クラスが *(Reference.cs)* されますが、古いクラス (BeanTrader.cs) もまだあります。 この時点で 2 つのオプションがあります。

- 新しい .NET Core ターゲット プロジェクトと共に元の .NET Framework プロジェクトをビルドできるようにする場合は、.NET `<Compile Remove="BeanTrader.cs" />` Core プロジェクトの csproj ファイル内の項目を使用して、.NET Framework バージョンと .NET Core バージョンのアプリで異なる WCF クライアントを使用できるようにします。 この方法では、既存の .NET Framework プロジェクトを変更しないという利点がありますが、生成された WCF クライアントを使用するコードは .NET Framework プロジェクトとは若干異なる必要があるため、ディレクティブを使用`#if`して、WCF クライアントの使用法 (クライアントの作成など) を条件付きでコンパイルする必要があります。

- 一方、既存の .NET Framework プロジェクト内のコード チャーンが許容される場合は *、BeanTrader.cs*をすべてまとめて削除できます。 新しい WCF クライアントは .NET 標準用に構築されているため、.NET Core と .NET Framework の両方のシナリオで動作します。 NET Framework 用に .NET Framework を構築する場合 (マルチターゲットまたは 2 つの csproj ファイルを使用して) は、両方のターゲットに対してこの新しい*Reference.cs*ファイルを使用できます。 この方法には、2 つの異なる WCF クライアントをサポートするためにコードを二分する必要がなされないという利点があります。同じコードがどこでも使用されます。 欠点は、(おそらく安定した) .NET Framework プロジェクトを変更する必要がある点です。

Bean Trader サンプルの場合、移行が容易になる場合は元のプロジェクトに小さな変更を加えることができるため、次の手順に従って WCF クライアントの使用を調整します。

01. ソリューション エクスプローラーの [既存の項目の追加] コンテキスト メニューを使用して、新しいReference.cs ファイルを .NET Framework *BeanTraderClient.csproj*プロジェクトに追加します。 C# ファイルのコピーではなく、両方のプロジェクトで同じファイルが使用されるように、必ず 'as link' を追加してください。 単一の csproj (マルチターゲティングを使用) で .NET Core と .NET Framework の両方を構築する場合、この手順は必要ありません。

01. *BeanTrader.cs*を削除します。

01. 新しい WCF クライアントは、古いクライアントと似ていますが、生成されたコード内の名前空間の数が異なります。 このため、プロジェクトを更新して、Wcf クライアントの型が BeanTrader.Service (または選択した名前空間名) から使用されるようにする必要があります。 *BeanTraderClient.Core.csproj*を構築することは、これらの変更を行う必要がある場所を特定するのに役立ちます。 修正は、C# と XAML ソース ファイルの両方で必要になります。

01. 最後に、`BeanTraderServiceClient`型に使用可能なコンストラクターが変更されたため*に、BeanTraderServiceClientFactory.cs*にエラーが発生していることがわかります。 以前は`InstanceContext`、(IoC コンテナ`CallbackHandler`からを使用して作成された) 引数`Castle.Windsor`を指定できていました。 新しいコンストラクタは新しい`CallbackHandler`s を作成します。 ただし、's 基本型には`BeanTraderServiceClient`、必要に応じコンストラクターがあります。 自動生成された WCF クライアント コードはすべて部分クラスに存在するため、簡単に拡張できます。 これを行うには *、BeanTraderServiceClient.cs*という名前の新しいファイルを作成し、同じ名前の部分クラスを作成します (BeanTrader.Service 名前空間を使用)。 次に、次に示すように、部分型に 1 つのコンストラクターを追加します。

    ```csharp
    public BeanTraderServiceClient(System.ServiceModel.InstanceContext callbackInstance) :
        base(callbackInstance, EndpointConfiguration.NetTcpBinding_BeanTraderService)
            { }
    ```

これらの変更が加えられた場合、Bean Trader サンプルは新しい .NET 標準互換 WCF クライアントを使用し、代わりに使用`Open``await OpenAsync`する呼び出し*を変更するTradingService.cs*の最終修正を行うことができます。

WCF の問題に対処すると、Bean のトレーダーサンプルの .NET Core バージョンがクリーンビルドされるようになりました。

## <a name="runtime-testing"></a>ランタイム テスト

プロジェクトが .NET Core に対してクリーンにビルドされるとすぐに移行作業が完了しないのは簡単です。 移植されたアプリをテストする時間も残しておく必要があります。 ビルドが正常に完了したら、特に .NET Framework を対象とするパッケージを使用している場合は、アプリが正常に実行され、動作することを確認します。

移植されたBeanのトレーダーアプリを起動して、何が起こるかを見てみましょう。 アプリは、次の例外で失敗する前に遠くに行かない。

```output
System.Configuration.ConfigurationErrorsException: 'Configuration system failed to initialize'

Inner Exception
ConfigurationErrorsException: Unrecognized configuration section system.serviceModel.
```

もちろん、これは理にかなっています。 WCF ではアプリ構成が使用されなくなったため、app.config ファイルの古い system.serviceModel セクションを削除する必要があることに注意してください。 更新された WCF クライアントは、コードに同じ情報をすべて含めているため、構成セクションは不要になりました。 app.config で WCF エンドポイントを構成可能にする場合は、アプリ設定として WCF クライアント コードを追加し、構成から WCF サービス エンドポイントを取得するように更新できます。

*app.config*の system.serviceModel セクションを削除すると、アプリは起動しますが、ユーザーがサインインすると別の例外で失敗します。

```output
System.PlatformNotSupportedException: 'Operation is not supported on this platform.'
```

サポートされていない API`Func<T>.BeginInvoke`は です。 [dotnet/corefx#5940](https://github.com/dotnet/corefx/issues/5940)で説明されているように、.NET Core は、`BeginInvoke`基`EndInvoke`になるリモート処理の依存関係のために、デリゲート型の メソッドと メソッドをサポートしていません。 この問題とその修正プログラムの詳細については、[移行する Delegate.BeginInvoke 呼び出](https://devblogs.microsoft.com/dotnet/migrating-delegate-begininvoke-calls-for-net-core/)`BeginInvoke`しの .NET Core ブログの投稿に説明`EndInvoke`されていますが、要点`Task.Run`は、呼び出しを (可能であれば非同期の代替) に置き換える必要があります。 ここで一般的な解決策を適用すると`BeginInvoke`、呼び出しは`Invoke`によって起動`Task.Run`された呼び出しに置き換えることができます。

```csharp
Task.Run(() =>
{
    return userInfoRetriever.Invoke();
}).ContinueWith(result =>
{
    // BeginInvoke's callback is replaced with ContinueWith
    var task = result.ConfigureAwait(false);
    CurrentTrader = task.GetAwaiter().GetResult();
}, TaskScheduler.Default);
```

使用を削除`BeginInvoke`した後、Bean Trader アプリは .NET Core で正常に実行されます。

![NET コアで実行されている Bean トレーダー](./media/convert-project-from-net-framework/running-on-core.png)

すべてのアプリが異なるため、独自のアプリを .NET Core に移行するために必要な具体的な手順は異なります。 しかし、Bean Trader サンプルは、一般的なワークフローと予想される問題の種類を示します。 また、この記事の長さにもかかわらず、.NET Core で動作させるために Bean Trader サンプルで実際に必要な変更はかなり制限されていました。 多くのアプリは、同じ方法で .NET Core に移行します。コードの変更が限られているか、あるいは必要ありません。
