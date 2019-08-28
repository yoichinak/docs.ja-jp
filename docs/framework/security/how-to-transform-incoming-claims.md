---
title: '方法: 入力方向の要求の変換'
ms.date: 03/30/2017
ms.assetid: 2831d514-d9d8-4200-9192-954bb6da1126
author: BrucePerlerMS
ms.openlocfilehash: ce99b97007bf7608856345d6da87cd9e422d2266
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2019
ms.locfileid: "70041477"
---
# <a name="how-to-transform-incoming-claims"></a>方法: 入力方向の要求の変換

## <a name="applies-to"></a>適用対象

- Microsoft® Windows® Identity Foundation (WIF)

- ASP.NET® Web フォーム

## <a name="summary"></a>Summary

この操作方法では、単純なクレーム対応 ASP.NET Web フォーム アプリケーションを作成、受信した要求を変換する詳細な手順を示します。 また、アプリケーションの実行中に変換されたクレームが表示されることを確認するためにアプリケーションをテストする方法についても説明します。

## <a name="contents"></a>目次

- 目的

- 概要

- 手順の要約

- 手順 1 – 簡単な ASP.NET Web フォーム アプリケーションを作成する

- 手順 2 – カスタム ClaimsAuthenticationManager を使用してクレーム変換を実装する

- 手順 3 – ソリューションをテストする

## <a name="objectives"></a>目的

- クレーム ベースの認証用の ASP.NET Web フォーム アプリケーションを構成します。

- 管理者ロールのクレームを追加することによって、受信したクレームを変換します。

- ASP.NET Web フォーム アプリケーションをテストして正しく機能することを確認する

## <a name="overview"></a>概要

WIF が <xref:System.Security.Claims.ClaimsAuthenticationManager> という名前のクラスを公開し、これを使用してユーザーは、クレームが利用者 (RP) アプリケーションに表示される前に、クレームを変更できます。 <xref:System.Security.Claims.ClaimsAuthenticationManager> は、認証と基になるアプリケーション コードの間での問題の分離に役立ちます。 次の例は、RP で必要になる場合がある着信 <xref:System.Security.Claims.ClaimsPrincipal> 内のクレームにロールを追加する方法を示しています。

## <a name="summary-of-steps"></a>手順の要約

- 手順 1 – 簡単な ASP.NET Web フォーム アプリケーションを作成する

- 手順 2 – カスタム ClaimsAuthenticationManager を使用してクレーム変換を実装する

- 手順 3 – ソリューションをテストする

## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>手順 1 – 簡単な ASP.NET Web フォーム アプリケーションを作成する

この手順では、新しい ASP.NET Web フォーム アプリケーションを作成します。

#### <a name="to-create-a-simple-aspnet-application"></a>簡単な ASP.NET アプリケーションを作成するには

1. システム特権のあるモードで管理者として Visual Studio を起動します。

2. Visual Studio で、 **[ファイル]** 、 **[新規作成]** 、 **[プロジェクト]** の順にクリックします。

3. **[新しいプロジェクト]** ウィンドウで、 **[ASP.NET Web フォーム アプリケーション]** をクリックします。

4. **[名前]** で、「`TestApp`」と入力し、 **[OK]** を押します。

5. **ソリューション エクスプローラー**で **[TestApp]** プロジェクトを右クリックし、 **[Identity and Access]** を選択します。

6. **[Identity and Access]** ウィンドウが表示されます。 **[Providers]** で **[Test your application with the Local Development STS]** を選択し、 **[Apply]** をクリックします。

7. *Default.aspx* ファイルの既存のマークアップを次のものに置き換え、ファイルを保存します。

    ```aspx-csharp
    <%@ Page Title="Home Page" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true"
        CodeBehind="Default.aspx.cs" Inherits="TestApp._Default" %>

    <asp:Content runat="server" ID="BodyContent" ContentPlaceHolderID="MainContent">
          <h3>Your Claims</h3>
        <p>
            <asp:GridView ID="ClaimsGridView" runat="server" CellPadding="3">
                <AlternatingRowStyle BackColor="White" />
                <HeaderStyle BackColor="#7AC0DA" ForeColor="White" />
            </asp:GridView>
        </p>
    </asp:Content>
    ```

8. *Default.aspx.cs* という名前の分離コード ファイルを開きます。 既存のコードを次のコードに置き換え、ファイルを保存します。

    ```csharp
    using System;
    using System.Web.UI;
    using System.Security.Claims;

    namespace TestApp
    {
        public partial class _Default : Page
        {
            protected void Page_Load(object sender, EventArgs e)
            {
                ClaimsPrincipal claimsPrincipal = Page.User as ClaimsPrincipal;
                this.ClaimsGridView.DataSource = claimsPrincipal.Claims;
                this.ClaimsGridView.DataBind();
            }
        }
    }
    ```

## <a name="step-2--implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a>手順 2 – カスタム ClaimsAuthenticationManager を使用してクレーム変換を実装する

この手順では、<xref:System.Security.Claims.ClaimsAuthenticationManager> クラスの既定の機能をオーバーライドし、受信プリンシパルに管理者ロールを追加します。

#### <a name="to-implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a>カスタム ClaimsAuthenticationManager を使用してクレーム変換を実装するには

1. Visual Studio でソリューションを右クリックし、 **[追加]** をクリックして **[新しいプロジェクト]** をクリックします。

2. **[新しいプロジェクトの追加]** ウィンドウで、 **[Visual C#]** テンプレート一覧から **[クラス ライブラリ]** を選択し、「`ClaimsTransformation`」と入力して **[OK]** をクリックします。 新しいプロジェクトがソリューション フォルダーに作成されます。

3. **[ClaimsTransformation]** プロジェクトの下の **[参照]** を右クリックし、 **[参照の追加]** をクリックします。

4. **参照マネージャー** ウィンドウで、**System.IdentityModel** を選択し、 **[OK]** をクリックします。

5. **Class1.cs** を開くか、存在しない場合は **ClaimsTransformation** を右クリックして、 **[追加]** をクリックし、 **[クラス]** をクリックします。

6. ディレクティブを使用して以下をコード ファイルに追加します。

    ```csharp
    using System.Security.Claims;
    using System.Security.Principal;
    ```

7. 次のクラスとメソッドをコード ファイルに追加します。

    > [!WARNING]
    > 次のコードは、デモの目的でのみ使用します。実稼働コードで、目的のアクセス許可を確認してください。

    ```csharp
    public class ClaimsTransformationModule : ClaimsAuthenticationManager
    {
        public override ClaimsPrincipal Authenticate(string resourceName, ClaimsPrincipal incomingPrincipal)
        {
            if (incomingPrincipal != null && incomingPrincipal.Identity.IsAuthenticated == true)
            {
               ((ClaimsIdentity)incomingPrincipal.Identity).AddClaim(new Claim(ClaimTypes.Role, "Admin"));
            }

            return incomingPrincipal;
        }
    }
    ```

8. ファイルを保存し、**ClaimsTransformation** プロジェクトをビルドします。

9. **TestApp** ASP.NET プロジェクトで、[参照] を右クリックし、 **[参照の追加]** をクリックします。

10. **参照マネージャー** ウィンドウで、左側のメニューから **[ソリューション]** を選択し、設定されたオプションから **ClaimsTransformation** を選択し、 **[OK]** をクリックします。

11. ルートの **Web.config**ファイルで、 **\<system.identityMode >** エントリに移動します。 **\<identityConfiguration >** 要素内で、次の行を追加し、ファイルを保存します。

    ```xml
    <claimsAuthenticationManager type="ClaimsTransformation.ClaimsTransformationModule, ClaimsTransformation" />
    ```

## <a name="step-3--test-your-solution"></a>手順 3 – ソリューションをテストする

この手順では、ASP.NET Web フォーム アプリケーションをテストし、ユーザーがフォーム認証を使用してサインインするときに、クレームが表示されることを確認します。

#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a>フォーム認証を使用してクレーム用の ASP.NET Web フォーム アプリケーションをテストするには

1. **F5** キーを押してアプリケーションをビルドし、実行します。 *Default.aspx* が表示されます。

2. *Default.aspx* ページで、**Your Claims** 見出しの下の表に、アカウントに関する **Issuer**、**OriginalIssuer**、**Type**、**Value**、および**ValueType** クレーム情報が表示されます。 最後の行は、次のように表示されます。

    ||||||
    |-|-|-|-|-|
    |LOCAL AUTHORITY|LOCAL AUTHORITY|`http://schemas.microsoft.com/ws/2008/06/identity/claims/role`|管理|<https://www.w3.org/2001/XMLSchema#string>|
