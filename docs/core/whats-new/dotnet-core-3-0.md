---
title: .NET Core 3.0 の新機能
description: .NET Core 3.0 の新機能について説明します。
dev_langs:
- csharp
- vb
author: thraka
ms.author: adegeo
ms.date: 12/31/2018
ms.openlocfilehash: e9a69c61df574ea391622ebb709c14948c71014d
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59341726"
---
# <a name="whats-new-in-net-core-30-preview-2"></a>.NET Core 3.0 (Preview 2) の新機能

この記事では、.NET Core 3.0 (Preview 2) の新機能について説明します。 最も大きな強化点の 1 つは、Windows デスクトップ アプリケーションのサポートです (Windows のみ)。 Windows デスクトップという .NET Core 3.0 SDK コンポーネントを利用して、Windows フォームおよび Windows Presentation Foundation (WPF) アプリケーションを移植することができます。 誤解のないように言うと、Windows Desktop コンポーネントは Windows でのみサポートされており、Windows にのみ含まれています。 詳細については、以下の「[Windows デスクトップ](#windows-desktop)」セクションを参照してください。

.NET Core 3.0 では C# 8.0 のサポートが追加されています。

[.NET Core 3.0 Preview 2 を今すぐダウンロード](https://aka.ms/netcore3download)して Windows、Mac、Linux 上で使い始めましょう。 リリースの詳細については、[.NET Core 3.0 Preview 2 のリリース ノート](https://aka.ms/netcore3releasenotes)を参照してください。

各バージョンでリリースされた内容の詳細については、次の発表を参照してください。

- [.NET Core 3.0 Preview 1 の発表](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/)
- [.NET Core 3.0 Preview 2 の発表](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-2/)

## <a name="c-8"></a>C# 8

.NET Core 3.0 では C# 8 をサポートしており、.NET Core 3.0 Preview 2 からは、次の新機能がサポートされます。 C# 8.0 機能の詳細については、次のブログ記事を参照してください。

- [C# 8.0 でのパターンの有効活用](https://devblogs.microsoft.com/dotnet/do-more-with-patterns-in-c-8-0/)
- [C# 8.0 を使ってみる](https://devblogs.microsoft.com/dotnet/take-c-8-0-for-a-spin/)
- [C# 8.0 のビルド](https://devblogs.microsoft.com/dotnet/building-c-8-0/)

### <a name="ranges-and-indices"></a>範囲とインデックス

新しい `Index` 型はインデックス作成に使用できます。 先頭からカウントする `int` か、末尾からカウントするプレフィックス `^` 演算子 (C#) を使用して作成することができます。

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

また、`Range` 型もあります。これは開始値と終了値の 2 つの `Index` 値から構成され、`x..y` の範囲式 (C#) で記述できます。 これで、スライスを生成するために `Range` を使用してインデックスを作成することができます。

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

### <a name="async-streams"></a>非同期ストリーム

`IAsyncEnumerable<T>` 型は、`IEnumerable<T>` の新しい非同期バージョンです。 この言語では、その要素を使用するために `IAsyncEnumerable<T>` よりも `await foreach` を行い、要素を生成するために `yield return` を使用することができます。

非同期ストリームの生成の両方の使用例を次に示します。 `foreach` ステートメントは非同期であり、`yield return` を使用して呼び出し元の非同期ストリームを生成します。 (`yield return` を使用する) このパターンは、非同期ストリームを生成するモデルに推奨されます。

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result; 
    }
}
```

`await foreach` を実行できるだけでなく、非同期反復子を作成することもできます。たとえば、`await` と`yield` の両方を行うことができる `IAsyncEnumerable/IAsyncEnumerator` を返す反復子です。 破棄する必要があるオブジェクトの場合は、`Stream` や `Timer` など、さまざまな BCL 型が実装する `IAsyncDisposable` を使用できます。

> [!NOTE]
> Visual Studio 2019 または [Visual Studio Code 用の C# 拡張機能](https://github.com/OmniSharp/omnisharp-vscode/releases/tag/v1.18.0-beta5)の最新のプレビューのいずれかを使用して開発を行う場合、非同期ストリームを使用するには、NET Core 3.0 Preview 2 が必要です。 コマンドラインで .NET Core 3.0 Preview 2 を使用する場合、すべて期待どおりに機能します。

### <a name="using-declarations"></a>using 宣言

*using 宣言*は、オブジェクが適切に破棄されることを保証するための新しい方法です。 *using 宣言*は、オブジェクトがスコープ内にある間は、オブジェクトをアクティブに保ちます。 オブジェクトがスコープ外になると、そのオブジェクトは自動的に破棄されます。 これにより入れ子になった *using ステートメント*が削減され、コードが簡潔になります。

```csharp
static void Main(string[] args)
{
    using var options = Parse(args);
    if (options["verbose"]) { WriteLine("Logging..."); }

} // options disposed here
```

### <a name="switch-expressions"></a>switch 式

*switch 式*は、*switch ステートメント*を実行するためのより簡潔な方法ですが、式なので値が返されます。 また、*switch 式*はパターン マッチングに完全に統合されており、破棄パターン `_` を使用して `default` 値を表します。

*switch 式*の構文は、次の例で確認できます。

```csharp
static string Display(object o) => o switch
{
    Point { X: 0, Y: 0 }         => "origin",
    Point { X: var x, Y: var y } => $"({x}, {y})",
    _                            => "unknown"
};
```

この例では、2 つのパターンが使われています。 `o` では最初に `Point` "*型パターン*" が照合され、次に *{中かっこ}* 内の"*プロパティ パターン*" が照合されます。 `_` は `discard pattern` を表します。これは *switch ステートメント*の `default` と同じです。

パターンを使用すると、意図のテストを実装する手続き型コードではなく、意図をキャプチャする宣言型コードを記述できます。 コンパイラによって、面倒な手続き型コードが実装されるようになり、それが常に正しく実行されることが保証されます。

*switch 式*よりも *switch ステートメント*の方が適しているケースは今後もあり、パターンはどちらの構文スタイルでも使用できます。

詳細については、「[Do more with patterns in C# 8.0](https://devblogs.microsoft.com/dotnet/do-more-with-patterns-in-c-8-0/)」 (C# 8.0 でのパターンの有効活用) を参照してください。

## <a name="ieee-floating-point-improvements"></a>IEEE 浮動小数点の改良

浮動ポイント API は、[IEEE 754-2008 リビジョン](https://en.wikipedia.org/wiki/IEEE_754-2008_revision)に準拠するように更新中です。 これらの変更の目的は、すべての "必要な" 操作を公開し、それらの動作が IEEE 仕様に準拠していることを保証することです。

解析および書式設定の修正:

* 任意の長さの入力を正しく解析して丸める。
* 負のゼロを正しく解析して書式設定する。
* 大文字と小文字を区別しないチェックを実行し、可能な場合には省略可能な先行の `+` を許可することで、無限大と NaN を正しく解析する。

新しい Math API には、次のものがあります。

* `BitIncrement/BitDecrement`\
`nextUp` および `nextDown` の IEEE 演算に相当します。 入力よりも大きいか小さいかを比較する最小の浮動小数点をそれぞれ返します。 たとえば、`Math.BitIncrement(0.0)` は `double.Epsilon` を返します。

* `MaxMagnitude/MinMagnitude`\
`maxNumMag` および `minNumMag` の IEEE 演算に相当します。2 つの入力の大きさがより大きいまたはより小さい値をそれぞれ返します。 たとえば、`Math.MaxMagnitude(2.0, -3.0)` は `-3.0` を返します。

* `ILogB`\
整数値を返す `logB` IEEE 演算に相当します。入力パラメーターの 2 を底とする積分対数を返します。 これは実質的に `floor(log2(x))` と同じですが、最小限の丸め誤差で実行されます。

* `ScaleB`\
整数値を受け取る `scaleB` IEEE 演算に相当します。これは実質的に `x * pow(2, n)` と同じですが、最小限の丸め誤差で実行されます。

* `Log2`\
`log2` IEEE 演算に相当します。2 を底とする対数を返します。 丸め誤差を最小限に抑えます。

* `FusedMultiplyAdd`\
`fma` IEEE 演算に相当します。融合型積和演算を実行します。 つまり、単一操作として `(x * y) + z` を実行することで、丸め誤差を最小限に抑えます。 例では、`FusedMultiplyAdd(1e308, 2.0, -1e308)` は `1e308` を返します。 正規の `(1e308 * 2.0) - 1e308` は `double.PositiveInfinity` を返します。

* `CopySign`\
`copySign` IEEE 演算に相当します。`x` の値を返しますが、`y` の符号と共に返されます。

## <a name="net-platform-dependent-intrinsics"></a>.NET プラットフォーム依存性

特定のパフォーマンス指向 CPU 命令 (**SIMD** や **ビット操作命令**セット) にアクセスできるようにする API が追加されました。 これらの命令は、データを並列で効率的に処理するといった、特定のシナリオでパフォーマンスを大幅に向上するのに役立ちます。 プログラムで使用する API の公開に加え、.NET ライブラリでパフォーマンスを向上させるためにこれらの命令が使用されるようになりました。

次の CoreCLR PR は、実装または使用によるいくつかの組み込みを示しています。

* [SSE2 ハードウェアの単純な組み込みの実装](https://github.com/dotnet/coreclr/pull/15585)
* [SSE ハードウェアの組み込みの実装](https://github.com/dotnet/coreclr/pull/15538)
* [Arm64 ベース HW の組み込み](https://github.com/dotnet/coreclr/pull/16822)
* [Locate{First|Last}Found{Byte|Char} に TZCNT と LZCNT を使用する](https://github.com/dotnet/coreclr/pull/21073)

詳細については、[.NET プラットフォーム依存性](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md)のセクションを参照してください。ここでは、このハードウェア インフラストラクチャを定義するための方法を定義して、Microsoft、チップ ベンダー、またはその他の企業や個人が、.NET コードに公開する必要があるハードウェア/チップ API を定義できるようにします。

## <a name="default-executables"></a>既定の実行可能ファイル

.NET Core では、既定で[フレームワーク依存の実行可能ファイル](../deploying/index.md#framework-dependent-executables-fde)が作成されるようになります。 これは、グローバルにインストールされているバージョンの .NET Core を使用するアプリケーションの新機能です。 これまでは、[自己完結型のデプロイ](../deploying/index.md#self-contained-deployments-scd)でのみ実行可能ファイルが生成されました。

`dotnet build` または `dotnet publish` の実行中に、使用している SDK の環境およびプラットフォームと一致する実行可能ファイルが作成されます。 これらの実行可能ファイルでは、次のような他のネイティブ実行可能ファイルと同じことを期待できます。

* 実行可能ファイルはダブルクリックすることができます。
* Windows では `myapp.exe`、Linux と macOS では`./myapp` など、コマンド プロンプトからアプリケーションを直接起動できます。

## <a name="build-copies-dependencies"></a>ビルドによる依存関係のコピー

`dotnet build` では、アプリケーションの NuGet 依存関係が NuGet キャッシュからビルド出力フォルダーにコピーされるようになりました。 以前は、依存関係のコピーは `dotnet publish` の一部としてのみ行われていました。 

リンクや razor ページの発行など、まだ発行が必要な操作がいくつかあります。

## <a name="local-dotnet-tools"></a>ローカルの dotnet ツール

>[!WARNING]
>.NET Core のローカル ツールは、.NET Core 3.0 Preview 1 と .NET Core 3.0 Preview 2 の間で変更されました。  `dotnet tool restore` や `dotnet tool install` のようなコマンドを実行して、Preview 1 でローカル ツールを試した場合は、Preview 2 でローカル ツールが正しく動作するためには、事前にローカル ツールのキャッシュ フォルダーを削除する必要があります。 このフォルダーは次の場所にあります。
>
>Mac、Linux の場合: `rm -r $HOME/.dotnet/toolResolverCache`
>
>Windows の場合: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`
>
>このフォルダーを削除しないと、エラーが表示されます。

.NET Core 2.1 はグローバル ツールをサポートしていましたが、.NET Core 3.0 にはローカル ツールが追加されました。 ローカル ツールはグローバル ツールに似ていますが、ディスク上の特定の場所に関連付けられています。 これで、プロジェクト単位およびリポジトリ単位のツールが可能になります。 ローカルにインストールされたツールはいずれも、グローバルでは使用できません。 ツールは、NuGet パッケージとして配布されます。

ローカル ツールは、現在のディレクトリ内のマニフェスト ファイル名 `dotnet-tools.json` に依存しています。 このマニフェスト ファイルは、ツールをそのフォルダー下で使用できるように定義します。 リポジトリのルートにこのマニフェスト ファイルを作成することで、コードを複製したすべての人が、コードを正常に処理するために必要なツールを復元し、使用できるようになります。

`dotnet-tools.json` マニフェスト ファイルを作成するには、次を使用します。

```console
dotnet new tool-manifest
```

次を使用してローカル マニフェストに新しいツールを追加します。

```console
dotnet tool install <packageId>
```

次を使用してローカル マニフェストに含まれるツールの一覧を表示することもできます。

```console
dotnet tool list
```

どのようなツールがグローバルにインストールされているかを表示するには、次を使用します。

```console
dotnet tool list -g
```

ローカル ツール マニフェスト ファイルは使用できるが、マニフェストで定義されたツールがインストールされていない場合は、次のコマンドを使用して、自動的にこれらのツールをダウンロードしてインストールします。

```console
dotnet tool restore
```

次のコマンドでローカル ツールを実行します。

```console
dotnet tool run <tool-command-name>
```

ローカル ツールが実行されると、dotnet で現在のディレクトリ構造内のマニフェストが検索されます。 ツール マニフェスト ファイルが見つかると、要求されたツールが検索されます。 キャッシュではなくマニフェスト内にツールが見つかった場合は、エラーが表示され、ユーザーは `dotnet tool restore` を実行する必要があります。

ローカル ツール マニフェスト ファイルからツールを削除するには、次のコマンドを実行します。

```console
dotnet tool uninstall <packageId>
```

ツール マニフェスト ファイルは、手動で編集できるように設計されています。そのため、リポジトリを操作するために必要なバージョンを更新することができます。 `dotnet-tools.json` ファイルの例を次に示します。

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {
    "dotnetsay": {
      "version": "2.1.4",
      "commands": [
        "dotnetsay"
      ]
    },
    "t-rex": {
      "version": "1.0.103",
      "commands": [
        "t-rex"
      ]
    }
  }
}
```

グローバル ツールとローカル ツールの両方で、ランタイムの互換バージョンが必要です。 現在 NuGet.org 上にある多くのツールは、.NET Core Runtime 2.1 をターゲットとしています。 グローバルにまたはローカルにそれらをインストールするには、[NET Core 2.1 ランタイム](https://dotnet.microsoft.com/download/dotnet-core/2.1)をインストールする必要があります。

## <a name="windows-desktop"></a>Windows デスクトップ

.NET Core 3.0 Preview 1 以降では、WPF および Windows フォームを使用して Windows デスクトップ アプリケーションを構築できます。 これらのフレームワークでは、Windows UI XAML ライブラリ (WinUI) の最新のコントロールと Fluent スタイルを [XAML Islands](/windows/uwp/xaml-platform/xaml-host-controls) 経由で使用することもできます。

Windows デスクトップ コンポーネントは、Windows .NET Core 3.0 SDK の一部です。

次の `dotnet` コマンドを使用して、新しい WPF または Windows フォーム アプリケーションを作成できます。

```console
dotnet new wpf
dotnet new winforms
```

Visual Studio 2019 では、.NET Core 3.0 Windows フォームと WPF 用に、**新しいプロジェクト** テンプレートが追加されました。 デザイナーは、まだサポートされていません。 また、これらのプロジェクトは、Visual Studio 2019 で開いたり、起動したり、デバッグしたりすることができます。

Visual Studio 2017 15.9 では、[.NET Core のプレビューを有効にする](https://devblogs.microsoft.com/dotnet/net-core-tooling-update-for-visual-studio-2017-version-15-9/)機能が追加されていますが、この機能をオンにする必要があり、これはサポートされているシナリオではありません。

新しいプロジェクトは既存の .NET Core プロジェクトと同じですが、いくつかの追加もあります。 基本的な .NET Core コンソール プロジェクトと基本的な Windows フォームおよび WPF プロジェクトとの比較を次に示します。

.NET Core コンソール プロジェクトでは、`Microsoft.NET.Sdk` SDK が使用され、`netcoreapp3.0` ターゲット フレームワークを介して .NET Core 3.0 への依存関係が宣言されます。 Windows デスクトップ アプリを作成するには、`Microsoft.NET.Sdk.WindowsDesktop` SDK を使用し、使用する UI フレームワークを選択します。

```diff
-<Project Sdk="Microsoft.NET.Sdk">
+<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
+   <UseWPF>true</UseWPF>
  </PropertyGroup>
</Project>
```

WPF でなく Windows フォームを選択するには、`UseWPF` の代わりに `UseWindowsForms` を設定します。

```diff
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
-   <UseWPF>true</UseWPF>
+   <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>
</Project>
```

Windows フォーム ダイアログが WPF コントロールをホストしている場合など、アプリが両方のフレームワークを使用する場合は、`UseWPF` および `UseWindowsForms` の両方を `true` に設定できます。

[dotnet/winforms](https://github.com/dotnet/winforms/issues)、[dotnet/wpf](https://github.com/dotnet/wpf/issues)、[dotnet/core](https://github.com/dotnet/core/issues) リポジトリに関するフィードバックをお寄せください。

## <a name="msix-deployment-for-windows-desktop"></a>Windows Desktop への MSIX の展開

[MSIX](https://docs.microsoft.com/windows/msix/) は Windows アプリの新しいパッケージ形式です。 これは、Windows 10 に .NET Core 3.0 のデスクトップ アプリケーションを展開するために使用できます。

[Windows アプリケーション パッケージ プロジェクト](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net)は、Visual Studio 2019 で使用でき、[自己完結型](../deploying/index.md#self-contained-deployments-scd)の .NET Core アプリケーションを使用して、MSIX パッケージを作成することができます。

>メモ:.NET Core プロジェクト ファイルの `<RuntimeIdentifiers>` プロパティで、サポートされているランタイムを指定する必要があります。
```xml
<RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
```

## <a name="fast-built-in-json-support"></a>高速な組み込み JSON のサポート

.NET エコシステムは、[**Json.NET**](https://www.newtonsoft.com/json) や他のよく使われている JSON ライブラリに依存しています。これは今後も推奨されます。 **Json.NET** では .NET の文字列が基本のデータ型 (内部的には UTF-16) として使用されます。

新しい組み込みの JSON サポートは、高パフォーマンス、低割り当てで、`Span<byte>` に基づいています。 3 つの新しい JSON 関連の主な型が、.NET Core 3.0 の `System.Text.Json` 名前空間に追加されました。

### <a name="utf8jsonreader"></a>Utf8JsonReader

`System.Text.Json.Utf8JsonReader` は、UTF-8 でエンコードされた JSON テキスト用の、高パフォーマンス、低割り当て、順方向専用のリーダーです。`ReadOnlySpan<byte>` から読み取られます。 `Utf8JsonReader` は基本的で低レベルの型であり、カスタム パーサーとデシリアライザーを構築するために利用できます。 新しい `Utf8JsonReader` を使用して JSON ペイロードを読み取る処理は、**Json.NET** のリーダーを使用する場合より 2 倍高速です。 JSON トークンを (UTF-16) 文字列として実現する必要が出てくるまでは割り当てられません。

この新しい API には、次のコンポーネントが含まれています。

* Preview 1:JSON リーダー (シーケンシャル アクセス)
* 次の予定:JSON ライター、DOM (ランダム アクセス)、poco シリアライザー、poco デシリアライザー

出発点として使用できる `Utf8JsonReader` の基本的なリーダー ループを次に示します。

```csharp
using System.Text.Json;

public static void Utf8JsonReaderLoop(ReadOnlySpan<byte> dataUtf8)
{
    var json = new Utf8JsonReader(dataUtf8, isFinalBlock: true, state: default);

    while (json.Read())
    {
        JsonTokenType tokenType = json.TokenType;
        ReadOnlySpan<byte> valueSpan = json.ValueSpan;
        switch (tokenType)
        {
            case JsonTokenType.StartObject:
            case JsonTokenType.EndObject:
                break;
            case JsonTokenType.StartArray:
            case JsonTokenType.EndArray:
                break;
            case JsonTokenType.PropertyName:
                break;
            case JsonTokenType.String:
                string valueString = json.GetStringValue();
                break;
            case JsonTokenType.Number:
                if (!json.TryGetInt32Value(out int valueInteger))
                {
                    throw new FormatException();
                }
                break;
            case JsonTokenType.True:
            case JsonTokenType.False:
                bool valueBool = json.GetBooleanValue();
                break;
            case JsonTokenType.Null:
                break;
            default:
                throw new ArgumentException();
        }
    }

    dataUtf8 = dataUtf8.Slice((int)json.BytesConsumed);
    JsonReaderState state = json.CurrentState;
}
```

### <a name="utf8jsonwriter"></a>Utf8JsonWriter

`System.Text.Json.Utf8JsonWriter` では、`String`、`Int32`、`DateTime` のような一般的な .NET 型から UTF-8 でエンコードされた JSON テキストを書き込むための、高パフォーマンス、非キャッシュ、順方向専用の方法が提供されます。 リーダーと同様に、ライターは基本的で低レベルの型であり、カスタム シリアライザーを構築するために利用できます。 新しい `Utf8JsonWriter` を使用して JSON ペイロードを書き込むと、**Json.NET** からライターを使用するよりも 30 - 80% 高速になり、割り当てが行われません。

出発点として使用できる `Utf8JsonWriter` の使用例を次に示します。

```csharp
static int WriteJson(IBufferWriter<byte> output, long[] extraData)
{
    var json = new Utf8JsonWriter(output, state: default);

    json.WriteStartObject();

    json.WriteNumber("age", 15, escape: false);
    json.WriteString("date", DateTime.Now);
    json.WriteString("first", "John");
    json.WriteString("last", "Smith");

    json.WriteStartArray("phoneNumbers", escape: false);
    json.WriteStringValue("425-000-1212", escape: false);
    json.WriteStringValue("425-000-1213");
    json.WriteEndArray();

    json.WriteStartObject("address");
    json.WriteString("street", "1 Microsoft Way");
    json.WriteString("city", "Redmond");
    json.WriteNumber("zip", 98052);
    json.WriteEndObject();

    json.WriteStartArray("ExtraArray");
    for (var i = 0; i < extraData.Length; i++)
    {
        json.WriteNumberValue(extraData[i]);
    }
    json.WriteEndArray();

    json.WriteEndObject();

    json.Flush(isFinalBlock: true);

    return (int)json.BytesWritten;
}
```

`Utf8JsonWriter` は、json データを同期的に書き込む出力場所として `IBufferWriter<byte>` を受け入れ、呼び出し元のユーザーは具象実装を提供する必要があります。 プラットフォームには現在、このインターフェイスの実装が含まれていません。 `IBufferWriter<byte>` の例については、[https://gist.github.com/ahsonkhan/c76a1cc4dc7107537c3fdc0079a68b35](https://gist.github.com/ahsonkhan/c76a1cc4dc7107537c3fdc0079a68b35) を参照してください。

### <a name="jsondocument"></a>JsonDocument

`System.Text.Json.JsonDocument` は、`Utf8JsonReader` に基づいています。 `JsonDocument` は、JSON データを解析し、ランダム アクセスと列挙型をサポートするためにクエリできる読み取り専用ドキュメント オブジェクト モデル (DOM) をビルドする機能を提供します。 データを作成する JSON 要素には、`RootElement` というプロパティとして `JsonDocument` によって公開される `JsonElement` 型を使用してアクセスできます。 `JsonElement` には、JSON 配列とオブジェクト列挙子とともに、JSON テキストを一般的な .NET 型に変換する API が含まれています。 一般的な JSON ペイロードを解析し、`JsonDocument` を使用してそのメンバーすべてにアクセスすると、適度にサイズ指定された (つまり 1 MB 未満) データに対する割り当てがごくわずかしかない **Json.NET** よりも 2 - 3 倍高速になります。

出発点として使用できる `JsonDocument` および `JsonElement` の使用例を次に示します。

```csharp
static double ParseJson()
{
    const string json = " [ { \"name\": \"John\" }, [ \"425-000-1212\", 15 ], { \"grades\": [ 90, 80, 100, 75 ] } ]";

    double average = -1;

    using (JsonDocument doc = JsonDocument.Parse(json))
    {
        JsonElement root = doc.RootElement;
        JsonElement info = root[1];

        string phoneNumber = info[0].GetString();
        int age = info[1].GetInt32();

        JsonElement grades = root[2].GetProperty("grades");

        double sum = 0;
        foreach (JsonElement grade in grades.EnumerateArray())
        {
            sum += grade.GetInt32();
        }

        int numberOfCourses = grades.GetArrayLength();
        average = sum / numberOfCourses;
    }

    return average;
}
```

## <a name="assembly-unloadability"></a>アセンブリのアンローダビリティ

アセンブリのアンローダビリティは、`AssemblyLoadContext` の新機能です。 この新機能は、API の観点からはきわめて透過的で、いくつかの新しい API で公開されます。 これによりローダー コンテキストをアンロードできるようにして、インスタンス化された型、静的フィールド、およびアセンブリ自体に対してすべてのメモリを解放します。 メモリ リークが発生することなく、アプリケーションは、このメカニズムを使用して永遠にアセンブリを読み込みおよびアンロードできる必要があります。

この新機能は、次のようなシナリオに使用できます。

* 動的プラグインの読み込みとアンロードが必要なプラグイン シナリオ。 
* コードを動的にコンパイルし、実行し、フラッシュする。 Web サイト、スクリプト エンジンなどに便利。
* イントロスペクション (ReflectionOnlyLoad など) のアセンブリの読み込み。ただし多くの場合、(Preview 1 でリリースされた) [MetadataLoadContext](#type-metadataloadcontext) の方が適しています。

詳細については、[アンローダビリティの使用](https://github.com/dotnet/coreclr/pull/22221)に関するドキュメントをご覧ください。

アセンブリのアンロードには、ローダー コンテキストの外部からマネージド オブジェクトへのすべての参照が理解され、管理されるようにするため、細心の注意が必要です。 ローダー コンテキストがアンロードされるように要求されると、ローダー コンテキストがそれ自体に対してのみ自己矛盾がないように、すべての外部参照が参照解除されている必要があります。

アセンブリのアンローダビリティは、.NET Core でサポートされていないアプリケーション ドメイン (AppDomains) によって、.NET Framework で提供されました。 この新しいモデルと比べて、AppDomains には利点と制限事項がありました。 AppDomains と比べて、この新しいローダー モデルがより柔軟で高いパフォーマンスになるように検討します。

## <a name="windows-native-interop"></a>Windows のネイティブ相互運用機能

Windows では、フラット C API、COM、および WinRT の形式で、質の高いネイティブ API を提供しています。 **P/Invoke** は .NET Core 1.0 以降でサポートされています。 .NET Core 3.0 では、**CoCreate COM API** と **WinRT API をアクティブ化**する機能のサポートが追加されました。

[Excel デモのソース コード](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo)での COM の使用例を確認できます。

## <a name="type-sequencereader"></a>型:SequenceReader

.NET Core 3.0 には、`ReadOnlySequence<T>` のリーダーとして使用できる `System.Buffers.SequenceReader` が追加されました。 これにより、バッキング バッファーを複数回通過できる `System.IO.Pipelines` データの簡単、高パフォーマンスな、低割り当ての解析が可能になります。 

次の例では、入力 `Sequence` を有効な `CR/LF` 区切りの行に分割します。

```csharp
private static ReadOnlySpan<byte> CRLF => new byte[] { (byte)'\r', (byte)'\n' };

public static void ReadLines(ReadOnlySequence<byte> sequence)
{
    SequenceReader<byte> reader = new SequenceReader<byte>(sequence);

    while (!reader.End)
    {
        if (!reader.TryReadToAny(out ReadOnlySpan<byte> line, CRLF, advancePastDelimiter:false))
        {
            // Couldn't find another delimiter
            // ...
        }

        if (!reader.IsNext(CRLF, advancePast: true))
        {
            // Not a good CR/LF pair
            // ...
        }

        // line is valid, process
        ProcessLine(line);
    }
}
```

## <a name="type-metadataloadcontext"></a>型:MetadataLoadContext

呼び出し元のアプリケーション ドメインに影響を与えることなく、アセンブリ メタデータを読み取ることができる `MetadataLoadContext` 型が追加されました。 現在の運用環境とは異なるアーキテクチャおよびプラットフォーム向けに構築されたアセンブリなど、アセンブリはデータとして読み込まれます。 `MetadataLoadContext` は <xref:System.Reflection.Assembly.ReflectionOnlyLoad*> と重複しています。これは .NET Framework でのみ使用できます。

`MetdataLoadContext` は、[System.Reflection.MetadataLoadContext パッケージ](https://www.nuget.org/packages/System.Reflection.MetadataLoadContext)で使用できます。 これは .NET Standard 2.0 パッケージです。

`MetadataLoadContext` は、<xref:System.Runtime.Loader.AssemblyLoadContext> 型に似ていますがその型に基づいていない API を公開しています。 <xref:System.Runtime.Loader.AssemblyLoadContext> と同様に、`MetadataLoadContext` を使用すると、分離したアセンブリの読み込み中にアセンブリを読み込むことができます。 `MetdataLoadContext` API から <xref:System.Reflection.Assembly> オブジェクトが返され、使い慣れたリフレクション API を使用できるようになります。 [MethodBase.Invoke](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/src/System/Reflection/TypeLoading/Methods/RoMethod.cs#L127) などの実行指向の API は使用できず、InvalidOperationException がスローされます。

次のサンプルは、特定のインターフェイスを実装するアセンブリ内で具象型を検索する方法を示しています。

```csharp
var paths = new string[] {@"C:\myapp\mscorlib.dll", @"C:\myapp\myapp.dll"};
var resolver = new PathAssemblyResolver(paths);
using (var lc = new MetadataLoadContext(resolver))
{
    Assembly a = lc.LoadFromAssemblyName("myapp");
    Type myInterface = a.GetType("MyApp.IPluginInterface");
    foreach (Type t in a.GetTypes())
    {
        if (t.IsClass && myInterface.IsAssignableFrom(t))
            Console.WriteLine($"Class {t.FullName} implements IPluginInterface");
    }
}
```

`MetadataLoadContext` のシナリオには、一連のアセンブリをデータとして検査し、検査の実行後にすべてのファイル ロックとメモリを解放する必要がある、設計時の機能、ビルド時のツール、およびランタイムのライトアップ機能が含まれます。

`MetadataLoadContext` には、コンストラクターに渡されるリゾルバー クラスがあります。 リゾルバーのジョブは、`AssemblyName` が指定された `Assembly` の読み込みです。 リゾルバー クラスは、抽象 `MetadataAssemblyResolver` クラスから派生します。 パスベースのシナリオの場合、リゾルバーの実装は `PathAssemblyResolver` で提供されています。

[MetadataLoadContext テスト](https://github.com/dotnet/corefx/tree/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests)は多数のユース ケースを示しています。 [アセンブリ テスト](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests/Assembly/AssemblyTests.cs)から始めることをお勧めします。

## <a name="tls-13--openssl-111-on-linux"></a>Linux 上の TLS 1.3 と OpenSSL 1.1.1

現在、.NET Core では、特定の環境で使用できるようになったら、[OpenSSL 1.1.1 の TLS 1.3 のサポート](https://www.openssl.org/blog/blog/2018/09/11/release111/)を利用する予定です。 [OpenSSL チーム](https://www.openssl.org/blog/blog/2018/09/11/release111/)によると、TLS 1.3 には複数の利点があります。

* クライアントとサーバー間に必要なラウンド トリップ回数の減少による接続時間の改善。

* さまざまな非推奨で安全ではない暗号化アルゴリズムの削除と、より多くの接続ハンドシェイクの暗号化によるセキュリティの向上。

.NET Core 3.0 Preview 1 では、**OpenSSL 1.1.1**、**OpenSSL 1.1.0**、または **OpenSSL 1.0.2** を利用することができます (Linux システム上で検出された任意の最適なバージョン)。  **OpenSSL 1.1.1** を使用可能で、クライアントとサーバーの両方が **TLS 1.3** をサポートしている場合、`SslProtocols.None` (システムの既定のプロトコル) を使用するときに、SslStream 型と HttpClient 型は **TLS 1.3** を使用します。

次のサンプルは、<https://www.cloudflare.com> に接続している Ubuntu 18.10 上の .NET Core 3.0 Preview 1 を示しています。

```csharp
using System;
using System.Net.Security;
using System.Net.Sockets;
using System.Threading.Tasks;

namespace tlstest
{
    class Program
    {
        static async Task Main()
        {
            using (TcpClient tcpClient = new TcpClient())
            {
                string targetHost = "www.cloudflare.com";

                await tcpClient.ConnectAsync(targetHost, 443);

                using (SslStream sslStream = new SslStream(tcpClient.GetStream()))
                {
                    await sslStream.AuthenticateAsClientAsync(targetHost);
                    await Console.Out.WriteLineAsync($"Connected to {targetHost} with {sslStream.SslProtocol}");
                }
            }
        }
    }
}
```

```console
user@comp-ubuntu1810:~/tlstest$ dotnet run
Connected to www.cloudflare.com with Tls13
user@comp-ubuntu1810:~/tlstest$ openssl version
OpenSSL 1.1.1  11 Sep 2018
```

>[!IMPORTANT]
>Windows と macOS はまだ **TLS 1.3** をサポートしていません。 サポートされるようになったら、.NET Core 3.0 はこれらのオペレーティング システムで **TLS 1.3** をサポートする予定です。

## <a name="cryptography"></a>暗号

`System.Security.Cryptography.AesGcm` および `System.Security.Cryptography.AesCcm` で実装された **AES-GCM** および **AES-CCM** 暗号のサポートが追加されました。 これらのアルゴリズムは、[Authenticated Encryption with Association Data (AEAD) アルゴリズム](https://en.wikipedia.org/wiki/Authenticated_encryption) であり、.NET Core に追加された最初の Authenticated Encryption (AE) アルゴリズムでもあります。

次のコードは、**AesGcm** 暗号を使用してランダム データの暗号化と復号化を行う例です。

**AesCcm** のコードは、ほぼ同じになります (クラスの変数名のみが異なります)。

```csharp
// key should be: pre-known, derived, or transported via another channel, such as RSA encryption
byte[] key = new byte[16];
RandomNumberGenerator.Fill(key);

byte[] nonce = new byte[12];
RandomNumberGenerator.Fill(nonce);

// normally this would be your data
byte[] dataToEncrypt = new byte[1234];
byte[] associatedData = new byte[333];
RandomNumberGenerator.Fill(dataToEncrypt);
RandomNumberGenerator.Fill(associatedData);

// these will be filled during the encryption
byte[] tag = new byte[16];
byte[] ciphertext = new byte[dataToEncrypt.Length];

using (AesGcm aesGcm = new AesGcm(key))
{
    aesGcm.Encrypt(nonce, dataToEncrypt, ciphertext, tag, associatedData);
}

// tag, nonce, ciphertext, associatedData should be sent to the other part

byte[] decryptedData = new byte[ciphertext.Length];

using (AesGcm aesGcm = new AesGcm(key))
{
    aesGcm.Decrypt(nonce, ciphertext, tag, decryptedData, associatedData);
}

// do something with the data
// this should always print that data is the same
Console.WriteLine($"AES-GCM: Decrypted data is{(dataToEncrypt.SequenceEqual(decryptedData) ? "the same as" : "different than")} original data.");
```

## <a name="cryptographic-key-importexport"></a>暗号化キーのインポート/エクスポート

.NET Core 3.0 Preview 1 は、標準形式からの非対称の公開キーと秘密キーのインポートとエクスポートをサポートしています。X.509 証明書を使用する必要はありません。

すべてのキーの種類 (RSA、DSA、ECDsa、ECDiffieHellman) は、公開キー用の **X.509 SubjectPublicKeyInfo** 形式と、秘密キー用の **PKCS#8 PrivateKeyInfo** および **PKCS#8 EncryptedPrivateKeyInfo** 形式をサポートしています。 RSA は、さらに **PKCS#1 RSAPublicKey** および **PKCS#1 RSAPrivateKey** をサポートしています。 いずれのエクスポートメソッドからも、DER でエンコードされたバイナリ データが生成され、インポート メソッドもそのようなデータを期待します。 キーがテキストに適した PEM 形式で格納されている場合、呼び出し元は import メソッドを呼び出す前にコンテンツを base64 でデコードする必要があります。

```csharp
using System;
using System.IO;
using System.Security.Cryptography;

namespace rsakeyprint
{
    class Program
    {
        static void Main(string[] args)
        {
            using (RSA rsa = RSA.Create())
            {
                byte[] keyBytes = File.ReadAllBytes(args[0]);
                rsa.ImportRSAPrivateKey(keyBytes, out int bytesRead);
 
                Console.WriteLine($"Read {bytesRead} bytes, {keyBytes.Length-bytesRead} extra byte(s) in file.");
                RSAParameters rsaParameters = rsa.ExportParameters(true);
                Console.WriteLine(BitConverter.ToString(rsaParameters.D));
            }
        }
    }
}
```

```console
user@comp-ubuntu1810:~/rsakeyprint$ echo Making a small key to save on screen space.
Making a small key to save on screen space.
user@comp-ubuntu1810:~/rsakeyprint$ openssl genrsa 768 | openssl rsa -outform der -out rsa.key
Generating RSA private key, 768 bit long modulus (2 primes)
..+++++++
........+++++++
e is 65537 (0x010001)
writing RSA key
user@comp-ubuntu1810:~/rsakeyprint$ dotnet run rsa.key
Read 461 bytes, 0 extra byte(s) in file.
0F-D0-82-34-F8-13-38-4A-7F-C7-52-4A-F6-93-F8-FB-6D-98-7A-6A-04-3B-BC-35-8C-7D-AC-A5-A3-6E-AD-C1-66-30-81-2C-2A-DE-DA-60-03-6A-2C-D9-76-15-7F-61-97-57-
79-E1-6E-45-62-C3-83-04-97-CB-32-EF-C5-17-5F-99-60-92-AE-B6-34-6F-30-06-03-AC-BF-15-24-43-84-EB-83-60-EF-4D-3B-BD-D9-5D-56-26-F0-51-CE-F1
user@comp-ubuntu1810:~/rsakeyprint$ openssl rsa -in rsa.key -inform der -text -noout | grep -A7 private
privateExponent:
    0f:d0:82:34:f8:13:38:4a:7f:c7:52:4a:f6:93:f8:
    fb:6d:98:7a:6a:04:3b:bc:35:8c:7d:ac:a5:a3:6e:
    ad:c1:66:30:81:2c:2a:de:da:60:03:6a:2c:d9:76:
    15:7f:61:97:57:79:e1:6e:45:62:c3:83:04:97:cb:
    32:ef:c5:17:5f:99:60:92:ae:b6:34:6f:30:06:03:
    ac:bf:15:24:43:84:eb:83:60:ef:4d:3b:bd:d9:5d:
    56:26:f0:51:ce:f1
```

PKCS#8 ファイルは `System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo` クラスで検査できます。

PFX/PKCS#12 ファイルは、それぞれ `System.Security.Cryptography.Pkcs.Pkcs12Info` および `System.Security.Cryptography.Pkcs.Pkcs12Builder` を使用して検査および操作できます。

## <a name="serialport-for-linux"></a>Linux 用 SerialPort

.NET Core 3.0 は Linux 上で <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> をサポートするようになりました。

以前の .NET Core では、Windows 上の `SerialPort` 型の使用のみをサポートしていました。

## <a name="more-bcl-improvements"></a>その他の BCL の機能強化

.NET Core 2.1 で導入された `Span<T>`、`Memory<T>`、および関連する型は、.NET Core 3.0 で最適化されました。 スパン構築、スライス、解析、書式設定などの一般的な操作がより効率的になりました。 

さらに、`String` のような型が内部的に改善され、`Dictionary<TKey, TValue>` やその他のコレクションのキーとして使用した場合の効率が改善されました。 これらの機能強化を利用するためにコードを変更する必要はありません。

.NET Core 3 Preview 1 では、次の機能強化も追加されました。

* HttpClient に組み込まれた Brotli のサポート
* ThreadPool.UnsafeQueueWorkItem(IThreadPoolWorkItem)
* Unsafe.Unbox
* CancellationToken.Unregister
* 複合算術演算子
* TCP のキープ アライブのためのソケット API
* StringBuilder.GetChunks
* IPEndPoint の解析
* RandomNumberGenerator.GetInt32

## <a name="tiered-compilation"></a>階層型コンパイル

.NET Core 3.0 では、[階層型コンパイル](https://devblogs.microsoft.com/dotnet/tiered-compilation-preview-in-net-core-2-1/)が既定で有効になりました。 起動時とスループットの最大化の両方でパフォーマンスを向上するために、状況に応じてランタイムが Just-In-Time (JIT) コンパイラを使用できるようにする機能です。

この機能は、[.NET Core 2.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-1/) のオプトイン機能として追加され、[.NET Core 2.2 Preview 2](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-2-preview-2/) で既定で有効になっています。 その後、.NET Core 2.2 リリースではオプトイン機能に戻りました。

## <a name="arm64-linux-support"></a>ARM64 Linux のサポート

ARM64 for Linux のサポートが追加されました。 現在、ARM64 の主なユース ケースは、IoT シナリオを使用しています。

Alpine、Debian、Ubuntu [Docker イメージは .NET Core for ARM64](https://hub.docker.com/r/microsoft/dotnet/) で使用できます。

詳細については、「[.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82)」(.NET Core Runtime ARM64 の状態) を確認してください。

>[!NOTE]
> **ARM64** Windows のサポートはまだ使用できません。

## <a name="install-net-core-30-previews-on-linux-with-snap"></a>スナップを使用して、Linux に .NET Core 3.0 のプレビューをインストールする

スナップは、[スナップをサポートする Linux ディストリビューション](https://docs.snapcraft.io/installing-snapd/6735)に .NET Core のプレビューをインストールして試すための推奨方法です。

お使いのシステムにスナップを構成したら、次のコマンドを実行して [.NET Core SDK 3.0 Preview SDK](https://snapcraft.io/dotnet-sdk) をインストールします。

```console
sudo snap install dotnet-sdk --beta --classic
```
 
スナップ パッケージを使用して .NET Core をインストールすると、既定の .NET Core コマンドは、単なる `dotnet` ではなく、`dotnet-sdk.dotnet` になります。 名前空間で指定したコマンドの利点は、グローバルにインストールされている可能性がある .NET Core バージョンと競合しないことです。 このコマンドは、次を使用して、`dotnet` のエイリアスにすることができます。

```console
sudo snap alias dotnet-sdk.dotnet dotnet
```

一部のディストリビューションでは、SSL 証明書へのアクセスを有効にするため、追加の手順が必要です。 詳細については、[Linux のセットアップ](https://github.com/dotnet/core/blob/master/Documentation/linux-setup.md)を参照してください。

## <a name="gpio-support-for-raspberry-pi"></a>Raspberry Pi の GPIO サポート

GPIO プログラミングで使用することができる 2 つの新しいパッケージが NuGet にリリースされました。

* [System.Device.Gpio](https://www.nuget.org/packages/System.Device.Gpio/0.1.0-prerelease.19078.2)
* [Iot.Device.Bindings](https://www.nuget.org/packages/Iot.Device.Bindings/0.1.0-prerelease.19078.2)

GPIO パッケージには、GPIO、SPI、I2C および PWM デバイス用の API が含まれています。 IoT バインド パッケージには、さまざまなチップとセンサーのための[デバイス バインド](https://github.com/dotnet/iot/blob/master/src/devices/README.md)が含まれています。これは [dotnet/iot - src/devices](https://github.com/dotnet/iot/tree/master/src/devices) で入手可能なものと同じです。

.NET Core 3.0 Preview 1 の一部として発表された更新されたシリアル ポート API は、これらのパッケージには含まれていませんが、.NET Core プラットフォームの一部として使用できます。

## <a name="platform-support"></a>プラットフォームのサポート

.NET Core 3 は、次のオペレーティング システムでサポートされます。

* Windows クライアント:7、8.1、10 (1607 以降)
* Windows Server:2012 R2 SP1 以降
* macOS:10.12+
* RHEL:6+
* Fedora:26+
* Ubuntu:16.04+
* Debian:9+
* SLES:12+
* openSUSE:42.3+
* Alpine:3.8+

チップのサポートは次のとおりです。

* Windows、macOS および Linux 上の x64
* Windows 上の x86
* Windows および Linux 上の ARM32
* Linux 上の ARM64

Linux の場合、ARM32 は Debian 9 以降および Ubuntu 16.04 以降でサポートされます。 ARM64 の場合、Alpine 3.8 を追加した ARM32 と同じです。 これらは、X64 でサポートされているため、これらのディストリビューションの同じバージョンです。

.NET Core 3.0 用の Docker イメージは、[Docker Hub の microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) で入手できます。 Microsoft は現在、[Microsoft コンテナー レジストリ (MCR)](https://cloudblogs.microsoft.com/opensource/2019/01/17/improved-discovery-experience-microsoft-containers-docker-hub/) の採用プロセスの最中で、最終的な .NET Core 3.0 イメージは MCR にのみ公開することを想定しています。
