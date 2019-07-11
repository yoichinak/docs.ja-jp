---
title: '方法: WIF を使用してサインイン状態を表示する'
ms.date: 03/30/2017
ms.assetid: 4d1174e4-5397-4962-9a5f-3b1ad7b3fc14
author: BrucePerlerMS
ms.openlocfilehash: 6d81bd2023886799f939fc9851db516a00aa92df
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742456"
---
# <a name="how-to-display-signed-in-status-using-wif"></a>方法: WIF を使用してサインイン状態を表示する
## <a name="applies-to"></a>対象  
  
- Microsoft® Windows® Identity Foundation (WIF) 4.5  
  
- ASP.NET® Web フォーム  
  
## <a name="summary"></a>まとめ  
 このトピックでは、WIF 対応 ASP.NET アプリケーションでサインイン状態を表示する方法について説明します。 WIF には、アプリケーションでクレームが認識されるようにする機能、およびアプリケーション リソースの認証と承認を管理する機能があります。  
  
## <a name="contents"></a>目次  
  
- 概要  
  
- 手順の要約  
  
- 手順 1 – Identity and Access 拡張機能をインストールする  
  
- 手順 2 – 証明書利用者の ASP.NET アプリケーションの作成  
  
- 手順 3 – ユーザー認証のためのローカル開発用 STS の有効化  
  
- 手順 4 – ASP.NET アプリケーションを変更してサインイン状態を表示する  
  
- 手順 5 – WIF と ASP.NET アプリケーション間の統合のテスト  
  
## <a name="overview"></a>概要  
 このトピックでは、WIF を使用して簡単なクレーム対応アプリケーションを作成する方法と、ユーザーがサインインしているかどうかを簡単に表示する方法について説明します。 次の手順では、Visual Studio の Identity and Access 拡張機能に含まれるローカル開発用 STS を使用します。 ローカル開発用 STS は、アプリケーションにクレームを統合する簡単な方法を提供する目的で、テストおよび開発環境向けに用意されたものです。 これは、実際の認証を行わず、資格情報も不要なため、稼動環境で使用しないでください。 ただし、次の手順の命令型コードは、実際の認証を使用した運用環境で使用できるアプリケーションの場合と同じです。  
  
## <a name="summary-of-steps"></a>手順の要約  
  
- 手順 1 – Identity and Access 拡張機能をインストールする  
  
- 手順 2 – 証明書利用者の ASP.NET アプリケーションの作成  
  
- 手順 3 – ユーザー認証のためのローカル開発用 STS の有効化  
  
- 手順 4 – ASP.NET アプリケーションを変更してサインイン状態を表示する  
  
- 手順 5 – WIF と ASP.NET アプリケーション間の統合のテスト  
  
## <a name="step-1--install-the-identity-and-access-extension"></a>手順 1 – Identity and Access 拡張機能をインストールする  
 この手順では、Identity and Access 拡張機能を Visual Studio 2012 用に構成する方法を説明します。 この拡張機能により、STS エンドポイントと通信するようにアプリケーションを構成するプロセスが自動化されます。  
  
### <a name="to-install-the-identity-and-access-extension"></a>Identity and Access 拡張機能をインストールするには  
  
1. システム特権のあるモードで管理者として Visual Studio を起動します。  
  
2. Visual Studio で、 **[ツール]** 、 **[拡張機能マネージャー]** の順にクリックします。 **[拡張機能マネージャー]** ウィンドウが表示されます。  
  
3. **拡張機能マネージャー**の左側のメニューで **[オンラインの拡張機能]** をクリックしてから、 **[Visual Studio ギャラリー]** を選択します。  
  
4. **拡張機能マネージャー**の右上隅で、*Identity and Access* を検索します。  
  
5. **Identity and Access** の項目が検索結果に表示されます。 それをクリックしてから、 **[ダウンロード]** をクリックします。  
  
6. **[ダウンロードとインストール]** ダイアログ ボックスが表示されます。 ライセンス条項に同意する場合は、 **[インストール]** をクリックします。  
  
7. **Identity and Access** の拡張機能のインストールが終了したら、管理者モードで Visual Studio を再起動します。  
  
## <a name="step-2--create-a-relying-party-aspnet-application"></a>手順 2 – 証明書利用者の ASP.NET アプリケーションの作成  
 この手順では、WIF と統合する証明書利用者の ASP.NET Web フォーム アプリケーションを作成する方法について説明します。  
  
### <a name="to-create-a-simple-aspnet-application"></a>簡単な ASP.NET アプリケーションを作成するには  
  
1. Visual Studio を起動し、 **[ファイル]** 、 **[新規作成]** 、 **[プロジェクト]** の順にクリックします。  
  
2. **[新しいプロジェクト]** ウィンドウで、 **[ASP.NET Web フォーム アプリケーション]** をクリックします。  
  
3. **[名前]** で、「`TestApp`」と入力し、 **[OK]** を押します。  
  
## <a name="step-3--enable-local-development-sts-to-authenticate-users"></a>手順 3 – ユーザー認証のためのローカル開発用 STS の有効化  
 この手順では、アプリケーションでローカル開発用 STS を有効にする方法について説明します。 ローカル開発用 STS は、Visual Studio 用の Identity and Access 拡張機能を使用することによって有効になります。  
  
### <a name="to-enable-local-development-sts-in-your-aspnet-application"></a>ASP.NET アプリケーションでローカル開発用 STS を有効にするには  
  
1. Visual Studio の**ソリューション エクスプローラー**で **[TestApp]** プロジェクトを右クリックし、 **[Identity and Access]** を選択します。  
  
2. **[Identity and Access]** ウィンドウが表示されます。 **[Providers]** で **[Test your application with the Local Development STS]** を選択し、 **[Apply]** をクリックします。  
  
## <a name="step-4--modify-your-aspnet-application-to-display-sign-in-status"></a>手順 4 – ASP.NET アプリケーションを変更してサインイン状態を表示する  
 この手順では、現在のユーザーがサインインしているかどうかを動的に表示するように ASP.NET アプリケーションを変更する方法について説明します。 STS プロバイダーを構成すると、WIF は受信クレームを処理します。 次に、認証の結果を表示するために、アプリケーション コードを構成する必要があります。  
  
### <a name="to-display-sign-in-status"></a>サインイン状態を表示するには  
  
1. Visual Studio で、 **[TestApp]** プロジェクトの下にある **Default.aspx** ファイルを開きます。  
  
2. **Default.aspx** ファイルの既存のマークアップを次のマークアップに置き換えます。  
  
    ```  
    <%@ Page Language="C#" AutoEventWireup="true" CodeFile="Default.aspx.cs" Inherits="_Default" %>  
  
    <!DOCTYPE html>  
  
    <html>  
    <head runat="server">  
        <title>Logged In Status</title>  
    </head>  
    <body>  
        <asp:label ID="myLabel" runat="server" />  
    </body>  
    </html>  
    ```  
  
3. **Default.aspx** を保存してから、**Default.aspx.cs** という名前の分離コード ファイルを開きます。  
  
    > [!NOTE]
    >  **Default.aspx.cs** は、ソリューション エクスプローラーで **Default.aspx** の下に隠れていることがあります。 **Default.aspx.cs** が表示されない場合は、**Default.aspx** の横の三角形をクリックして展開します。  
  
4. **Default.aspx.cs** の既存のコードを次のコードに置き換えます。  
  
    ```csharp  
    using System;  
    using System.Web.UI;  
    using System.Security.Claims;  
  
    namespace TestApp  
    {  
        protected void Page_Load(object sender, EventArgs e)  
        {  
            ClaimsPrincipal claimsPrincipal = Thread.CurrentPrincipal as ClaimsPrincipal;  
  
            if (claimsPrincipal != null)  
            {  
                myLabel.Text = "You are signed in.";  
            }  
            else  
            {  
                myLabel.Text = "You are not signed in.";  
            }  
        }  
    }  
    ```  
  
5. **Default.aspx.cs** を保存し、アプリケーションをビルドします。  
  
## <a name="step-5--test-the-integration-between-wif-and-your-aspnet-application"></a>手順 5 – WIF と ASP.NET アプリケーション間の統合のテスト  
 この手順では、WIF と ASP.NET アプリケーション間の統合をテストする方法について説明します。  
  
### <a name="to-test-the-integration-between-wif-and-aspnet"></a>WIF と ASP.NET 間の統合をテストするには  
  
1. Visual Studio で **F5** キーを押して、アプリケーションのデバッグを開始します。 エラーがなければ、新しいブラウザー ウィンドウが開きます。  
  
2. ブラウザーが STS に自動的に要求をリダイレクトし、Default.aspx ページが開きます。 WIF が正しく構成されている場合は、次のテキストを表示するサイトが表示されます。 **"You are signed"** します。
