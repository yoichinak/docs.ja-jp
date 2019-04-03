---
title: 汎用性のあるクラス ライブラリを使用したプラットフォーム間の開発
ms.date: 09/17/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- Portable Class Library [.NET Framework]
- targeting multiple platforms
- multiple platforms, targeting
ms.assetid: c31e1663-c164-4e65-b66d-d3aa8750a154
author: mairaw
ms.author: mairaw
ms.openlocfilehash: afaa8e118bb21e5c1e4f1c53b1d0d29ca6bb3bf5
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48030841"
---
# <a name="cross-platform-development-with-the-portable-class-library"></a>ポータブル クラス ライブラリを使用したクロス プラットフォーム開発

Visual Studio でポータブル クラス ライブラリ プロジェクトの種類を使用して、迅速かつ簡単に、クロス プラットフォーム アプリとライブラリの Microsoft プラットフォームを構築できます。

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

ポータブル クラス ライブラリにより、コードの開発とテストにかかる時間とコストを削減できます。 このプロジェクトの種類を使用して、書き込みし、ポータブルの .NET Framework アセンブリをビルドし、.NET Framework、iOS、またはファルダなどの複数のプラットフォームを対象とするアプリからこれらのアセンブリを参照

Visual Studio でポータブル クラス ライブラリ プロジェクトを作成し、プロジェクトの開発を開始した後でも、ターゲット プラットフォームを変更できます。 Visual Studio では、コードにする必要がある変更の特定に役立てることにより、新しいアセンブリでは、ライブラリをコンパイルします。

## <a name="create-a-portable-class-library-project"></a>ポータブル クラス ライブラリ プロジェクトを作成します。

ポータブル クラス ライブラリを作成するには、Visual Studio で提供されているテンプレートを使用します。 新しいプロジェクトを作成 (**ファイル** > **新しいプロジェクト**)、および、**新しいプロジェクト** ダイアログ ボックスを使用するプログラミング言語 (Visual C# または Visual Basic) を選択します。 次に、選択、**クラス ライブラリ (レガシ ポータブル)** テンプレート。 プロジェクトの名前を入力し、選択**OK**します。

**ポータブル クラス ライブラリの追加** ダイアログ ボックスが表示されます。 2 つ以上のターゲットを選択し、 **OK**します。

![Visual Studio でのポータブル クラス ライブラリのターゲットを追加します。](media/add-portable-class-library.png)

## <a name="change-targets"></a>ターゲットを変更します。

作成するときに、または開発を開始した後は、ポータブル クラス ライブラリ プロジェクトのターゲット プラットフォームを変更できます。 プロジェクトを作成した後、ターゲットを変更したい場合**ソリューション エクスプ ローラー**(ソリューションではなく)、ポータブル クラス ライブラリ プロジェクトのショートカット メニューを開き、選択し、**プロパティ**. プロジェクトのプロパティ ページ、**ライブラリ** タブは、プロジェクトが現在対象とするプラットフォームを示します。

![Visual Studio でポータブル クラス ライブラリのプロジェクトのプロパティ](media/pcl-project-properties.png)

追加またはターゲットの削除、選択、**変更** ボタンを選択して、該当するチェック ボックスをオフにします。

ターゲットを変更すると、変更後のターゲットに合わせて、プロジェクトの開発に使用できる API が変更されます。 Visual Studio は、ターゲットを変更したことで発生する可能性があるエラーと警告を報告します。

Visual Studio で変更を加える前に、アセンブリの移植性を評価する場合は、使用することができます、 [.NET Portability Analyzer](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b)します。

## <a name="supported-types-and-members"></a>サポートされている型とメンバー

ポータブル クラス ライブラリのプロジェクトで使用できる型とメンバーは、互換性に関するいくつかの要因による制約を受けます。

-   選択したターゲット間で共有される必要があります。

-   それらのターゲット間で同様に動作する必要があります。

-   廃止候補であってはなりません。

-   特にサポートしているメンバーがポータブルでない場合は、ポータブルな環境に意味がある必要があります。

メンバーがポータブル クラス ライブラリでサポートされており、選択したターゲットのメンバーである場合、IntelliSense でプロジェクトにこのメンバーが表示されます。 ただし、API がポータブル クラス ライブラリでサポートされている可能性があります。API を使用できるかどうかは、選択したターゲットによって異なります。

## <a name="api-differences-in-the-portable-class-library"></a>ポータブル クラス ライブラリでの API の相違点

サポートされるすべてのプラットフォームでポータブル クラス ライブラリ アセンブリの互換性を確保するために、ポータブル クラス ライブラリでは一部のメンバーが若干変更されています。

## <a name="use-the-portable-class-library"></a>ポータブル クラス ライブラリを使用します。

ポータブル クラス ライブラリ プロジェクトをビルドしたら、他のプロジェクトからそのプロジェクトを参照します。 プロジェクトを参照することも、アクセスする必要のあるクラスを含む特定のアセンブリを参照することもできます。

ポータブル クラス ライブラリ アセンブリを参照するアプリを実行するには、ターゲット プラットフォームの必要なバージョン (またはそれ以上のバージョン) がコンピューターにインストールされている必要があります。 Visual Studio には必要なすべてのフレームワークが含まれるため、さらに変更を加えることなく、アプリケーションの開発に使用したコンピューターでアプリケーションを実行できます。

### <a name="deploy-a-universal-windows-app"></a>ユニバーサル Windows アプリをデプロイします。

ユニバーサル Windows アプリを作成するときに、ポータブル クラス ライブラリ アセンブリを参照して、アプリ パッケージに含まれているアプリを展開する必要があるすべてが以降の手順は必要ありません。

### <a name="deploy-a-net-framework-app"></a>デプロイを .NET Framework アプリ

ポータブル クラス ライブラリ アセンブリを参照する .NET Framework アプリを配置するときは、.NET Framework の正しいバージョンに対する依存関係を指定する必要があります。 この依存関係を指定することで、必要なバージョンがアプリケーションと共に確実にインストールされます。

-   ClickOnce 配置で依存関係を作成する: で**ソリューション エクスプ ローラー**、発行するプロジェクトのプロジェクト ノードを選択します。 (これは、ポータブル クラス ライブラリ プロジェクトを参照するプロジェクトです。)メニュー バーで、**プロジェクト** > **プロパティ**を選択し、**発行**タブ。**発行**ページで、選択**の前提条件**します。 必須コンポーネントとして、必要な .NET Framework のバージョンを選択します。

-   セットアップ プロジェクトの依存関係を作成する: で**ソリューション エクスプ ローラー**、セットアップ プロジェクトを選択します。 メニュー バーで、**プロジェクト** > **プロパティ** > **の前提条件**します。 必須コンポーネントとして、必要な .NET Framework のバージョンを選択します。

.NET Framework アプリの展開についての詳細については、[開発者向け配置ガイド](../../../docs/framework/deployment/deployment-guide-for-developers.md)を参照してください。

## <a name="see-also"></a>関連項目

- [MVVM を利用した汎用性のあるクラス ライブラリの使用](../../../docs/standard/cross-platform/using-portable-class-library-with-model-view-view-model.md)
- [複数のプラットフォームを対象とするライブラリのアプリケーション リソース](../../../docs/standard/cross-platform/app-resources-for-libraries-that-target-multiple-platforms.md)
- [.NET portability Analyzer](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)
- [Windows ストア アプリおよび Windows ランタイムのための .NET Framework サポート](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
- [配置](../../../docs/framework/deployment/net-framework-applications.md)
