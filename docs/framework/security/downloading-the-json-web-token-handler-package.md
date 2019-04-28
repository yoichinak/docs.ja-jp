---
title: JSON Web トークン ハンドラー パッケージのダウンロード
ms.date: 10/10/2018
ms.assetid: d12b3f5b-f1f1-4a9d-a159-0c13e5976c90
ms.openlocfilehash: 8f878d23afd76488de7da03f16f72cbfa43c17d7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61792757"
---
# <a name="download-the-json-web-token-handler-package"></a>JSON Web トークン ハンドラー パッケージをダウンロードします。

このトピックでは、JSON Web トークン ハンドラーをダウンロードしてプロジェクトで使用する方法について説明します。

JSON Web トークン ハンドラー拡張機能は、プロジェクトに必要なアセンブリと参照を追加する NuGet パッケージとして入手できます。 まだ NuGet がインストールされていない場合は、[nuget.org](https://nuget.org) にアクセスしてインストールしてください。 ページ NuGet にアクセスして、拡張機能のバージョン履歴を確認できます。[NuGet での JSON Web トークン ハンドラー](https://www.nuget.org/packages/System.IdentityModel.Tokens.Jwt/)

## <a name="use-the-package-manager-gui"></a>パッケージ マネージャー GUI を使用します。

1. Visual Studio の**ソリューション エクスプローラー**でプロジェクトを右クリックし、**[NuGet パッケージの管理]** を選択します。

2. **[NuGet パッケージの管理]** ウィンドウで、検索ボックスをクリックし、「`JWT Token Handler`」と入力して **Enter** キーを押します。

3. 結果ペインから、最初の結果の **[インストール]** をクリックします。

4. パッケージのダウンロードが開始されます。 プロジェクトに追加される前に、[License Acceptance] ダイアログ ボックスが表示されます。 ライセンス条項に同意する場合は、**[I Accept]** をクリックします。

5. 最新の JSON Web トークン ハンドラー アセンブリがダウンロードされ、プロジェクトに追加されます。

## <a name="use-the-package-manager-console"></a>パッケージ マネージャー コンソールを使用してください。

1. Visual Studio で、次のようにクリックします。**ツール** > **NuGet パッケージ マネージャー** > **パッケージ マネージャー コンソール**します。

2. **[パッケージ マネージャー コンソール]** が表示されます。 次のテキストを入力し、**Enter** キーを押します。

    ```powershell
    Install-Package System.IdentityModel.Tokens.Jwt
    ```

3. 最新の JSON Web トークン ハンドラー アセンブリがダウンロードされ、プロジェクトに追加されます。