---
title: 発行者名レジストリの検証パッケージのダウンロード
ms.date: 10/10/2018
ms.assetid: ff8b0014-c5d4-4614-90f0-13fcc0ba777a
ms.openlocfilehash: 833a0722fdd27df4e488ed7fac99444c6d9b8905
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940583"
---
# <a name="download-the-validating-issuer-name-registry-package"></a>発行者名レジストリの検証パッケージをダウンロードします。

このトピックでは、Validating Issuer Name Registry (VINR) をダウンロードしてプロジェクトで使用する方法について説明します。

VINR は、プロジェクトに必要なアセンブリと参照を追加する NuGet パッケージとして入手できます。 まだ NuGet がインストールされていない場合は、[nuget.org](https://nuget.org) にアクセスしてインストールしてください。 ページ NuGet にアクセスして、拡張機能のバージョン履歴を確認できます。[Microsoft が NuGet で発行者名レジストリの検証](https://nuget.org/packages/System.IdentityModel.Tokens.ValidatingIssuerNameRegistry/)

## <a name="use-the-package-manager-gui"></a>パッケージ マネージャー GUI を使用します。

1. Visual Studio の**ソリューション エクスプローラー**でプロジェクトを右クリックし、**[NuGet パッケージの管理]** を選択します。

2. **[NuGet パッケージの管理]** ウィンドウで、検索ボックスをクリックし、「`ValidatingIssuerNameRegistry`」と入力して **Enter** キーを押します。

3. 結果ペインから、最初の結果の **[インストール]** をクリックします。

4. パッケージのダウンロードが開始されます。 プロジェクトに追加される前に、[License Acceptance] ダイアログ ボックスが表示されます。 ライセンス条項に同意する場合は、**[I Accept]** をクリックします。

5. 最新の VINR アセンブリがダウンロードされ、プロジェクトに追加されます。

## <a name="use-the-package-manager-console"></a>パッケージ マネージャー コンソールを使用してください。

1. Visual Studio で、次のようにクリックします。**ツール** > **NuGet パッケージ マネージャー** > **パッケージ マネージャー コンソール**します。

2. **[パッケージ マネージャー コンソール]** が表示されます。 次のテキストを入力し、**Enter** キーを押します。

    ```powershell
    Install-Package System.IdentityModel.Tokens.ValidatingIssuerNameRegistry
    ```

3. 最新の VINR アセンブリがダウンロードされ、プロジェクトに追加されます。