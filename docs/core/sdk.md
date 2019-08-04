---
title: .NET Core SDK の概要
description: .NET Core プロジェクトの作成に使用するライブラリとツールのセットである .NET Core SDK について説明します。
ms.date: 07/31/2019
ms.technology: dotnet-cli
ms.openlocfilehash: 0231c08f780455c4956c044815a2e80cef4d827e
ms.sourcegitcommit: 8c6426a3d2adff5fbcbe1fed0f28eda718c15351
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/02/2019
ms.locfileid: "68733388"
---
# <a name="net-core-sdk-overview"></a>.NET Core SDK の概要

.NET Core ソフトウェア開発キット (SDK) は一連のライブラリとツールであり、開発者はこれを利用して .NET Core のアプリケーションやライブラリを作成できます。 それには、アプリケーションのビルドと実行に使用される次のコンポーネントが含まれています。

- .NET Core CLI ツール。
- .NET Core ライブラリとランタイム。
- `dotnet` [ドライバー](tools/index.md#driver)。

## <a name="acquiring-the-net-core-sdk"></a>.NET Core SDK を入手する

他のツールと同様に、最初にコンピューターにツールをインストールする必要があります。 シナリオに応じて、次のいずれかの方法で SDK をインストールできます。

- ネイティブ インストーラーを使う。
- インストール シェル スクリプトを使う。

開発者のコンピューターでは、ネイティブ インストーラーが利用されることが多いです。 SDK はサポートされるプラットフォームのネイティブ インストール メカニズムにより配信されます。たとえば、Ubuntu の場合は DEB パッケージ、Windows の場合は MSI バンドルです。 これらのインストーラーでは、インストール直後に、ユーザーが SDK を使うために必要な環境がインストールされて設定されます。 ただし、コンピューター上で管理者特権も必要になります。 インストールする SDK は、[.NET ダウンロード](https://dotnet.microsoft.com/download) ページで見つけることができます。

一方、インストール スクリプトでは、管理者特権は必要ありません。 ただし、いかなる前提条件もコンピューターにインストールされません。前提条件はすべてユーザーが手動でインストールする必要があります。 スクリプトは、通常、管理者特権なしでツールをインストールするとき、ビルド サーバーを設定するために利用されます (上の前提条件警告に注意してください)。 詳しくは、[インストール スクリプト リファレンス](tools/dotnet-install-script.md)に関する記事をご覧ください。 お使いの CI ビルド サーバーで SDK を設定する方法について関心がある場合は、「[継続的インテグレーション (CI) で .NET Core SDK とツールを使用する](tools/using-ci-with-cli.md)」をご覧ください。

既定では、SDK のインストールは "side-by-side" (SxS) 方式で行われるため、複数のバージョンの CLI ツールが 1 台のコンピューターにいつでも共存できます。 CLI コマンドを実行したときにバージョンが選択される方法について詳しくは、「[使用する .NET Core のバージョンを選択する](versions/selection.md)」記事をご覧ください。

## <a name="see-also"></a>関連項目

- [.NET Core CLI](tools/index.md)
- [.NET Core のバージョン管理の概要](versions/index.md)
- [.NET Core ランタイムと SDK を削除する方法](versions/remove-runtime-sdk-versions.md)
- [使用する .NET Core のバージョンを選択する](versions/selection.md)
