---
title: Visual Studio 2017 を使用して C# .NET Standard ライブラリを構築する
description: Visual Studio 2017 を使用して C# で記述された .NET Standard クラス ライブラリを作成する方法について説明します。
author: BillWagner
ms.author: wiwagn
ms.date: 08/07/2017
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: 440ef2ed398b22262923422efd7f1259e3ee9b74
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633691"
---
# <a name="build-a-net-standard-library-with-c-and-the-net-core-sdk-in-visual-studio-2017"></a>Visual Studio 2017 の C# と .NET Core を使用して .NET Standard ライブラリを構築する

"*クラス ライブラリ*" は、アプリケーションから呼び出される型とメソッドを定義します。 .NET Standard 2.0 をターゲットとするクラス ライブラリでは、お使いのライブラリを、そのバージョンの .NET Standard をサポートする任意の .NET 実装によって呼び出すことができます。 クラス ライブラリを完了させたら、サードパーティ製のコンポーネントとして配布するかどうか、あるいは 1 つまたは複数のアプリケーションにバンドルされたコンポーネントとして含めるかどうかを決定できます。

> [!NOTE]
> .NET Standard のバージョンとサポート対象のプラットフォームの一覧は、[「.NET Standard」](../../standard/net-standard.md)を参照してください。

このトピックでは、1 つの文字列処理メソッドを含む簡単なユーティリティ ライブラリを作成します。 それを[拡張メソッド](../../csharp/programming-guide/classes-and-structs/extension-methods.md)として実装し、<xref:System.String> クラスのメンバーと同じように呼び出すことができるようにします。

## <a name="creating-a-class-library-solution"></a>クラス ライブラリのソリューションを作成する

最初に、クラス ライブラリ プロジェクトとその関連プロジェクトのソリューションを作成します。 1 つの Visual Studio のソリューションは、1 つまたは複数のプロジェクトのコンテナーとして機能します。 このソリューションは次のように作成します。

1. Visual Studio のメニュー バーで、**[ファイル]** > **[新規作成]** > **[プロジェクト]** の順に選びます。

1. **[新しいプロジェクト]** ダイアログの **[その他のプロジェクトの種類]** ノードを展開し、**[Visual Studio ソリューション]** を選びます。 ソリューションの名前を "ClassLibraryProjects" にして、**[OK]** ボタンを選びます。

   ![新しい空のソリューションが強調表示されている [新しいプロジェクト] ダイアログ](./media/library-with-visual-studio/new-project-dialog.png)

## <a name="creating-the-class-library-project"></a>クラス ライブラリ プロジェクトの作成

クラス ライブラリ プロジェクトを作成します。

1. **ソリューション エクスプローラー**で **ClassLibraryProjects** ソリューション ファイルを右クリックし、コンテキスト メニューから **[追加]** > **[新しいプロジェクト]** の順に選びます。

1. **[新しいプロジェクトの追加]** ダイアログで、**[Visual C#]** ノードを展開し、**[.NET Standard]** ノードを選択し、**[クラス ライブラリ (.NET Standard)]** プロジェクト テンプレートを選択します。 **[名前]** テキスト ボックスに、プロジェクト名として「StringLibrary」と入力します。 **[OK]** を選んでクラス ライブラリ プロジェクトを作成します。

   ![新しいライブラリ プロジェクトの追加ダイアログ](./media/library-with-visual-studio/add-new-library-project.png)

   Visual Studio 開発環境でコード ウィンドウが開きます。

   ![既定のクラス ライブラリ テンプレート コードが表示された Visual Studio アプリケーション ウィンドウ](./media/library-with-visual-studio/string-library-project.png)

1. ライブラリが正しいバージョンの .NET Standard をターゲットにしていることを確認します。 **ソリューション エクスプローラー** ウィンドウで、ライブラリ プロジェクトを右クリックし、**[プロパティ]** を選択します。 **[ターゲット フレームワーク]** テキスト ボックスに、.NET Standard 2.0 がターゲットになっていることが示されています。

   ![クラス ライブラリのプロジェクト プロパティ](./media/library-with-visual-studio/library-project-properties.png)

1. コード ウィンドウ内のコードを次のコードに置き換えて、ファイルを保存します。

   [!CODE-csharp[ClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs)]

   クラス ライブラリ `UtilityLibraries.StringLibrary` には `StartsWithUpper` という名前のメソッドが含まれており、これによって、現在の文字列のインスタンスが大文字で始まるかどうかを示す <xref:System.Boolean> 値が返されます。 Unicode 規格では、大文字と小文字が区別されます。 <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> メソッドは文字が大文字の場合に `true` を返します。

1. メニュー バーで **[ビルド]** > **[ソリューションのビルド]** の順に選択します。 プロジェクトはエラーなしでコンパイルされます。

   ![ビルドが成功したことを示す出力ペイン](./media/library-with-visual-studio/output-pane-successful-build.png)

## <a name="next-step"></a>次のステップ

ライブラリを正常に作成できました。 そのメソッドの呼び出しをまだ行っていないので、期待どおりに動作するかわかりません。 ライブラリ開発の次のステップでは、[単体テスト プロジェクト](testing-library-with-visual-studio.md)を使ってライブラリをテストします。
