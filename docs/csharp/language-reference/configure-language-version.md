---
title: C# 言語のバージョンの選択 - C# ガイド
description: 特定のコンパイラ バージョンを使用して構文の検証を実行するコンパイラを構成します。
ms.date: 02/28/2019
ms.openlocfilehash: 6d31a757171bd2eecdcc1fbd3da765dcb3fe45c0
ms.sourcegitcommit: 79066169e93d9d65203028b21983574ad9dcf6b4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/01/2019
ms.locfileid: "57212028"
---
# <a name="select-the-c-language-version"></a>C# 言語のバージョンの選択

C# コンパイラでは、プロジェクトのターゲット フレームワーク (1 つまたは複数) に基づいて既定の言語バージョンが決定されます。 ご自分のプロジェクトが、対応するプレビュー バージョンの言語を持つプレビュー フレームワークをターゲットにしている場合、使用される言語バージョンはプレビュー バージョンの言語です。 ご自分のプロジェクトがプレビュー フレームワークをターゲットにしていない場合、使用される言語バージョンは最新のマイナー バージョンです。

たとえば、.NET Core 3.0 のプレビュー期間中は、`netcoreapp3.0` または `netstandard2.1` (両方ともプレビュー段階) をターゲットにするすべてのプロジェクトで C# 8.0 言語 (これもプレビュー段階) が使用されます。 リリース バージョンをターゲットにするプロジェクトでは、C# 7.3 (最新リリース バージョン) が使用されます。 この動作は、.NET Framework をターゲットにするすべてのプロジェクトで最新 (C# 7.3) が使用されることを意味しています。 

この機能によって、開発環境に新しいバージョンの SDK とツールをインストールすることの決定と新しい言語機能をプロジェクトに組み込むことの決定が別になります。 ビルド コンピューターに最新の SDK とツールをインストールできます。 特定バージョンの言語をビルドに使用するように各プロジェクトを構成できます。 既定の動作は、新しい型や CLR の新しい動作に依存する言語機能が、プロジェクトでそれらのフレームワークをターゲットにしている場合にのみ有効になることを意味しています。

言語バージョンを指定することで、既定の動作をオーバーライドできます。 言語バージョンを設定する方法はいくつかあります。

- [Visual Studio のクイック アクション](#visual-studio-quick-action)を利用する。
- [Visual Studio UI](#set-the-language-version-in-visual-studio) で言語バージョンを設定する。
- [**.csproj** ファイルを手動で編集する](#edit-the-csproj-file)。
- [サブディレクトリ内の複数のプロジェクトに対して](#configure-multiple-projects)言語バージョンを設定する。
- [`-langversion` コンパイラ オプション](#set-the-langversion-compiler-option)を構成する。

## <a name="visual-studio-quick-action"></a>Visual Studio のクイック アクション

Visual Studio は、必要な言語バージョンを判断するのに役立ちます。 現在構成されているバージョンで使用できない言語機能を使用する場合、Visual Studio は、プロジェクトの言語バージョンを更新する可能性のある修正プログラムを示します。

## <a name="set-the-language-version-in-visual-studio"></a>Visual Studio で言語バージョンを設定する

Visual Studio のバージョンを設定できます。 ソリューション エクスプローラーでプロジェクト ノードを右クリックして、**[プロパティ]** を選択します。 **[ビルド]** タブを選択し、**[詳細設定]** ボタンを選択します。 ドロップダウン リストで、バージョンを選択します。 次の図は "最新の" 設定を示しています。

![言語バージョンを指定できる高度なビルド設定のスクリーン ショット](./media/configure-language-version/advanced-build-settings.png)

> [!NOTE]
> Visual Studio IDE を使用して csproj ファイルを更新する場合、IDE によって、ビルド構成ごとにノードが作成されます。 一般的に、すべてのビルド構成で同じように値を設定しますが、ビルド構成ごとに明示的に設定する必要があります。あるいは、この設定を変更するとき、"すべての構成" を選択します。 csproj ファイルに次が表示されます。
>
>```xml
> <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|AnyCPU'">
>  <LangVersion>latest</LangVersion>
></PropertyGroup>
>
> <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|AnyCPU'">
>  <LangVersion>latest</LangVersion>
> </PropertyGroup>
> ```
>

## <a name="edit-the-csproj-file"></a>csproj ファイルを編集する

**.csproj** ファイルで言語バージョンを設定できます。 次のような要素を追加します。

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

値 `latest` は、C# 言語の最新のマイナー バージョンを使用します。 次の値を指定できます。

|[値]|説明|
|------------|-------------|
|preview|コンパイラは、最新のプレビュー バージョンの有効な言語構文をすべて受け入れます。|
|latest|コンパイラは、最新リリース バージョンのコンパイラ (マイナー バージョンを含む) の構文を受け入れます。|
|latestMajor|コンパイラは、最新リリースのメジャー バージョンのコンパイラの構文を受け入れます。|
|8.0|コンパイラは、C# 8.0 以下に含まれている構文のみを受け入れます。|
|7.3|コンパイラは、C# 7.3 以下に含まれている構文のみを受け入れます。|
|7.2|コンパイラは、C# 7.2 以下に含まれている構文のみを受け入れます。|
|7.1|コンパイラは、C# 7.1 以下に含まれている構文のみを受け入れます。|
|7|コンパイラは、C# 7.0 以下に含まれている構文のみを受け入れます。|
|6|コンパイラは、C# 6.0 以下に含まれている構文のみを受け入れます。|
|5|コンパイラは、C# 5.0 以下に含まれている構文のみを受け入れます。|
|4|コンパイラは、C# 4.0 以下に含まれている構文のみを受け入れます。|
|3|コンパイラは、C# 3.0 以下に含まれている構文のみを受け入れます。|
|ISO-2|コンパイラは、ISO/IEC 23270:2006 C# (2.0) に含まれている構文のみを受け入れます。 |
|ISO-1|コンパイラは、ISO/IEC 23270:2003 C# (1.0/1.2) に含まれている構文のみを受け入れます。 |

## <a name="configure-multiple-projects"></a>複数のプロジェクトを構成する

複数のディレクトリを構成する `<LangVersion>` 要素を含む **Directory.build.props** ファイルを作成することができます。 この操作は通常、ソリューション ディレクトリで実行します。 ソリューション ディレクトリ内の **Directory.build.props** ファイルに以下を追加します。

```xml
<Project>
 <PropertyGroup>
   <LangVersion>7.3</LangVersion>
 </PropertyGroup>
</Project>
```

これで、そのファイルを含むディレクトリのすべてのサブディレクトリ内のビルドで、C# バージョン 7.3 構文が使用されます。 詳しくは、「[ビルドのカスタマイズ](/visualstudio/msbuild/customize-your-build)」を参照してください。

## <a name="set-the-langversion-compiler-option"></a>言語コンパイラ オプションを設定する

`-langversion` コマンド ライン オプションを使用することができます。 詳しくは、[-langversion](../language-reference/compiler-options/langversion-compiler-option.md) コンパイラ オプションに関する記事を参照してください。 「`csc -langversion:?`」と入力して、有効な値の一覧を確認できます。
