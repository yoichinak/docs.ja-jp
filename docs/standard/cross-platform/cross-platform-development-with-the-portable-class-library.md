---
title: 汎用性のあるクラス ライブラリを使用したプラットフォーム間の開発
ms.date: 09/17/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- Portable Class Library [.NET Framework]
- targeting multiple platforms
- multiple platforms, targeting
ms.assetid: c31e1663-c164-4e65-b66d-d3aa8750a154
ms.openlocfilehash: 7caddd7361b8f364762fb4357e35cb918ae99263
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242804"
---
# <a name="cross-platform-development-with-the-portable-class-library"></a>ポータブル クラス ライブラリを使用したクロスプラットフォーム開発

Visual Studio のポータブル クラス ライブラリ プロジェクトの種類を使用すると、Microsoft プラットフォーム向けのクロスプラットフォーム アプリやライブラリをすばやく簡単にビルドできます。

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

ポータブル クラス ライブラリにより、コードの開発とテストにかかる時間とコストを削減できます。 このプロジェクトの種類を使用して、ポータブル .NET Framework アセンブリを作成およびビルドし、.NET Framework、iOS、Mac などの複数のプラットフォームを対象とするアプリからこれらのアセンブリを参照します。

Visual Studio でポータブル クラス ライブラリ プロジェクトを作成し、プロジェクトの開発を開始した後でも、ターゲット プラットフォームを変更できます。 Visual Studio は、新しいアセンブリを使用してライブラリをコンパイルします。

## <a name="create-a-portable-class-library-project"></a>ポータブル クラス ライブラリ プロジェクトを作成する

ポータブル クラス ライブラリを作成するには、Visual Studio で提供されているテンプレートを使用します。 新しいプロジェクト (**ファイル** > **の新しいプロジェクト**) を作成し、[**新しいプロジェクト**] ダイアログ ボックスで、プログラミング言語 (Visual C# または Visual Basic) を選択します。 次に、**クラス ライブラリ (レガシ ポータブル)** テンプレートを選択します。 プロジェクトの名前を入力し **、[OK]** をクリックします。

[**ポータブル クラス ライブラリの追加**] ダイアログ ボックスが表示されます。 複数のターゲットを選択し **、[OK]** をクリックします。

![Visual Studio でポータブル クラス ライブラリ ターゲットを追加する](media/add-portable-class-library.png)

## <a name="change-targets"></a>ターゲットの変更

ポータブル クラス ライブラリ プロジェクトのターゲット プラットフォームは、作成時または開発開始後に変更できます。 プロジェクトを作成した後にターゲットを変更する場合は、**ソリューション エクスプローラー**で、ポータブル クラス ライブラリ プロジェクトのショートカット メニュー (ソリューションではなく) を開き、[**プロパティ]** を選択します。 プロジェクトのプロパティ ページの [**ライブラリ**] タブには、プロジェクトが現在対象としているプラットフォームが表示されます。

![Visual Studio のポータブル クラス ライブラリのプロジェクト プロパティ](media/pcl-project-properties.png)

ターゲットを追加または削除するには、[**変更**] ボタンを選択し、該当するチェック ボックスをオンまたはオフにします。

ターゲットを変更すると、変更後のターゲットに合わせて、プロジェクトの開発に使用できる API が変更されます。 Visual Studio は、ターゲットを変更したことで発生する可能性があるエラーと警告を報告します。

Visual Studio で変更を加える前にアセンブリの移植性を評価する場合は[、.NET 移植性アナライザ](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)ー を使用できます。

## <a name="supported-types-and-members"></a>サポートされている型とメンバー

ポータブル クラス ライブラリのプロジェクトで使用できる型とメンバーは、互換性に関するいくつかの要因による制約を受けます。

- 選択したターゲット間で共有される必要があります。

- それらのターゲット間で同様に動作する必要があります。

- 廃止候補であってはなりません。

- 特にサポートしているメンバーがポータブルでない場合は、ポータブルな環境に意味がある必要があります。

メンバーがポータブル クラス ライブラリでサポートされており、選択したターゲットのメンバーである場合、IntelliSense でプロジェクトにこのメンバーが表示されます。 ただし、API がポータブル クラス ライブラリでサポートされている可能性があります。API を使用できるかどうかは、選択したターゲットによって異なります。

## <a name="api-differences-in-the-portable-class-library"></a>ポータブル クラス ライブラリでの API の相違点

サポートされるすべてのプラットフォームでポータブル クラス ライブラリ アセンブリの互換性を確保するために、ポータブル クラス ライブラリでは一部のメンバーが若干変更されています。

## <a name="use-the-portable-class-library"></a>ポータブル クラス ライブラリを使用する

ポータブル クラス ライブラリ プロジェクトをビルドしたら、他のプロジェクトからそのプロジェクトを参照します。 プロジェクトを参照することも、アクセスする必要のあるクラスを含む特定のアセンブリを参照することもできます。

ポータブル クラス ライブラリ アセンブリを参照するアプリを実行するには、ターゲット プラットフォームの必要なバージョン (またはそれ以上のバージョン) がコンピューターにインストールされている必要があります。 Visual Studio には必要なすべてのフレームワークが含まれるため、さらに変更を加えることなく、アプリケーションの開発に使用したコンピューターでアプリケーションを実行できます。

### <a name="deploy-a-universal-windows-app"></a>ユニバーサル Windows アプリを展開する

ポータブル クラス ライブラリ アセンブリを参照するユニバーサル Windows アプリを作成する場合、アプリパッケージにアプリを展開するために必要なものはすべてアプリ パッケージに含まれ、それ以上の手順は必要ありません。

### <a name="deploy-a-net-framework-app"></a>.NET Framework アプリを展開する

ポータブル クラス ライブラリ アセンブリを参照する .NET Framework アプリを配置するときは、.NET Framework の正しいバージョンに対する依存関係を指定する必要があります。 この依存関係を指定することで、必要なバージョンがアプリケーションと共に確実にインストールされます。

- ClickOnce 配置を使用して依存関係を作成するには、**ソリューション エクスプローラー**で、発行するプロジェクトのプロジェクト ノードを選択します。 (これは、ポータブル クラス ライブラリ プロジェクトを参照するプロジェクトです)。メニュー バーで [**プロジェクト** > **のプロパティ]** をクリックし、[**発行**] タブを選択します。[**発行**] ページで、[**必須コンポーネント**] を選択します。 必須コンポーネントとして、必要な .NET Framework のバージョンを選択します。

- セットアップ プロジェクトとの依存関係を作成するには、**ソリューション エクスプローラー**でセットアップ プロジェクトを選択します。 メニュー バーで、[**プロジェクト** > **のプロパティの** > **前提条件**] を選択します。 必須コンポーネントとして、必要な .NET Framework のバージョンを選択します。

NET Framework アプリの展開の詳細については、「[開発者向けの展開ガイド](../../../docs/framework/deployment/deployment-guide-for-developers.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [MVVM を利用した汎用性のあるクラス ライブラリの使用](using-portable-class-library-with-model-view-view-model.md)
- [複数のプラットフォームを対象とするライブラリのアプリ リソース](app-resources-for-libraries-that-target-multiple-platforms.md)
- [.NET Portability Analyzer](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)
- [Windows ストア アプリおよび Windows ランタイムのための .NET Framework サポート](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
- [デプロイ](../../../docs/framework/deployment/net-framework-applications.md)
