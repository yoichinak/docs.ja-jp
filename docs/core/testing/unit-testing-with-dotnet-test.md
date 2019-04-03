---
title: dotnet テストと xUnit を使用した .NET Core での単体テスト C# コード
description: dotnet テストおよび xUnit を使用したサンプル ソリューションを段階的に構築していく対話型エクスペリエンスを通じて、C# および .NET Core の単体テストの概念について説明します。
author: ardalis
ms.author: wiwagn
ms.date: 11/29/2017
ms.custom: seodec18
ms.openlocfilehash: 97cf42c78154375ce06639d4a3029ed87b993ced
ms.sourcegitcommit: 8258515adc6c37ab6278e5a3d102d593246f8672
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58504354"
---
# <a name="unit-testing-c-in-net-core-using-dotnet-test-and-xunit"></a>dotnet テストと xUnit を使用した .NET Core での単体テスト C#

このチュートリアルでは、単体テストの概念について学習するためにサンプル ソリューションを段階的に構築する対話型のエクスペリエンスを示します。 構築済みのソリューションを使用してチュートリアルに従う場合は、開始する前に[サンプル コードを参照またはダウンロード](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/)してください。 ダウンロード方法については、「[サンプルおよびチュートリアル](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)」を参照してください。

## <a name="creating-the-source-project"></a>ソース プロジェクトの作成

シェル ウィンドウを開きます。 ソリューションを保持するための *unit-testing-using-dotnet-test* というディレクトリを作成します。
この新しいディレクトリ内で [`dotnet new sln`](../tools/dotnet-new.md) を実行して、ソリューションを新たに作成します。 ソリューションを用意すると、クラス ライブラリと単体テスト プロジェクトの両方を管理しやすくなります。
ソリューションのディレクトリ内で、*PrimeService* ディレクトリを作成します。 現時点のディレクトリとファイルの構造は次のようになっています。

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
```

*PrimeService* を現在のディレクトリにし、[`dotnet new classlib`](../tools/dotnet-new.md) を実行してソース プロジェクトを作成します。 *Class1.cs* の名前を *PrimeService.cs* に変更します。 最初に、`PrimeService` クラスのエラーが発生する実装を作成します。

```csharp
using System;

namespace Prime.Services
{
    public class PrimeService
    {
        public bool IsPrime(int candidate)
        {
            throw new NotImplementedException("Please create a test first");
        }
    }
}
```

*unit-testing-using-dotnet-test* ディレクトリに戻ります。

[dotnet sln](../tools/dotnet-sln.md) コマンドを実行して、クラス ライブラリ プロジェクトをソリューションに追加します。

```
dotnet sln add ./PrimeService/PrimeService.csproj
```

## <a name="creating-the-test-project"></a>テスト プロジェクトの作成

次に、*PrimeService.Tests* ディレクトリを作成します。 次の一覧はディレクトリ構造を示したものです。

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

*PrimeService.Tests* ディレクトリを現在のディレクトリにし、[`dotnet new xunit`](../tools/dotnet-new.md) を使用して新しいプロジェクトを作成します。 このコマンドによって、テスト ライブラリとして [xUnit](https://xunit.github.io/) を使用するテスト プロジェクトが作成されます。 生成されたテンプレートで、*PrimeServiceTests.csproj* ファイルのテスト ランナーが構成されます。次のようなコードです。

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

テスト プロジェクトには、単体テストを作成して実行するための、他のパッケージが必要です。 前の手順の `dotnet new` によって、xUnit と xUnit ランナーが追加されています。 ここで、プロジェクトに別の依存関係として `PrimeService` クラス ライブラリを追加します。 次の [`dotnet add reference`](../tools/dotnet-add-reference.md) コマンドを使用します。

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

全体のファイルは GitHub の[サンプル リポジトリ](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj)で確認できます。

ソリューションの最終的なレイアウトは次のようになります。

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.csproj
```

テスト プロジェクトをソリューションに追加するには、*unit-testing-using-dotnet-test* ディレクトリで [dotnet sln](../tools/dotnet-sln.md) コマンドを実行します。

```
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
```

## <a name="creating-the-first-test"></a>最初のテストの作成

失敗するテストを 1 つ作成してそれを合格させる、というプロセスを繰り返します。 *PrimeService.Tests* ディレクトリから *UnitTest1.cs* を削除し、*PrimeService_IsPrimeShould.cs* という名前の新しい C# ファイルを作成します。 次のコードを追加します。

```csharp
using Xunit;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    public class PrimeService_IsPrimeShould
    {
        private readonly PrimeService _primeService;

        public PrimeService_IsPrimeShould()
        {
            _primeService = new PrimeService();
        }

        [Fact]
        public void ReturnFalseGivenValueOf1()
        {
            var result = _primeService.IsPrime(1);

            Assert.False(result, "1 should not be prime");
        }
    }
}
```

`[Fact]` 属性は、テスト ランナーによって実行されるテスト メソッドを表します。 *PrimeService.Tests* フォルダーから、[`dotnet test`](../tools/dotnet-test.md) を実行してテストとクラス ライブラリをビルドし、それからテストを実行します。 xUnit テスト ランナーには、テストを実行するためのプログラムのエントリ ポイントが含まれています。 `dotnet test` を実行すると、作成した単体テスト プロジェクトを使用してテスト ランナーが開始されます。

テストが失敗します。 実装はまだ作成していません。 最もシンプルな動作のコードを `PrimeService` クラスに記述して、このテストが成功するようにします。 既存の `IsPrime` メソッド実装を次のコードに置き換えます。

```csharp
public bool IsPrime(int candidate)
{
    if (candidate == 1)
    {
        return false;
    }
    throw new NotImplementedException("Please create a test first");
}
```

*PrimeService.Tests* ディレクトリで、`dotnet test` をもう一度実行します。 `dotnet test` コマンドは `PrimeService` プロジェクトのビルドを実行してから、`PrimeService.Tests` プロジェクトのビルドを実行します。 両方のプロジェクトをビルドすると、この単一テストが実行されます。 成功します。

## <a name="adding-more-features"></a>他の機能の追加

テストが成功したので、他のテストも記述してみましょう。 素数に関する、いくつかの単純なケースが他にもあります(0、-1)。 `[Fact]` 属性を使用すると、これらの例を新しいテストとして追加できますが、すぐに煩雑になります。 一連の類似のテストを記述できるようになる、他の xUnit 属性があります。

- `[Theory]` は同じコードを実行するものの、異なる入力引数が含まれる一連のテストを表します。

- `[InlineData]` 属性は、これらの入力の値を指定します。

新しいテストを作成するのではなく、この 2 つの属性、`[Theory]` と `[InlineData]` を適用することで *PrimeService_IsPrimeShould.cs* ファイルに 1 つの理論を作成できます。 その理論とは、複数の 2 未満の値を調べて、もっとも小さい素数を特定するという手法です。

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

`dotnet test` をもう一度実行します。これらのテストのうち、2 つが失敗するはずです。 すべてのテストを成功させるために、*PrimeService.cs* ファイルで `IsPrime` メソッドの先頭にある `if` 句を変更します。

```csharp
if (candidate < 2)
```

他のテスト、理論、コードをメイン ライブラリに追加して、反復を続けます。 [テストの最終版](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs)ができ、[ライブラリの完全な実装](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs)が完了しました。

### <a name="additional-resources"></a>その他の技術情報

- [xUnit.net の公式サイト](https://xunit.github.io)
- [ASP.NET Core のコントローラー ロジックをテストする](/aspnet/core/mvc/controllers/testing)
