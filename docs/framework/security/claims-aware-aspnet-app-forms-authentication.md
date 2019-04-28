---
title: '方法: フォームベースの認証を使用するクレーム対応 ASP.NET アプリケーションをビルドする'
ms.date: 03/30/2017
ms.assetid: 98a3e029-1a9b-4e0c-b5d0-29d3f23f5b15
author: BrucePerlerMS
ms.openlocfilehash: ecaf1de0b806d5568d81fac2ddb2b39b697135ab
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61792751"
---
# <a name="how-to-build-claims-aware-aspnet-application-using-forms-based-authentication"></a>方法: フォームベースの認証を使用するクレーム対応 ASP.NET アプリケーションをビルドする

## <a name="applies-to"></a>対象

- Microsoft® Windows® Identity Foundation (WIF)

- ASP.NET® Web フォーム

## <a name="summary"></a>まとめ

この操作方法では、フォーム認証を使用する簡単なクレーム対応 ASP.NET Web フォーム アプリケーションを作成するための詳細な手順を示します。 また、フォーム認証を使用してユーザーがサインインするときにクレームが表示されることを確認するために、アプリケーションをテストする方法についても説明します。

## <a name="contents"></a>目次

- 目的

- 概要

- 手順の要約

- 手順 1 – 簡単な ASP.NET Web フォーム アプリケーションを作成する

- 手順 2 – フォーム認証を使用してクレーム用の ASP.NET Web フォーム アプリケーションを構成する

- 手順 3 – ソリューションをテストする

## <a name="objectives"></a>目的

- フォーム認証を使用してクレーム用の ASP.NET Web フォーム アプリケーションを構成する

- ASP.NET Web フォーム アプリケーションをテストして正しく機能することを確認する

## <a name="overview"></a>概要

.NET 4.5 には、WIF とそのクレーム ベースの認証が、Framework の不可欠な部分として組み込まれています。 以前は、ASP.NET ユーザーからのクレームが必要な場合に、WIF をインストールしてから、`Thread.CurrentPrincipal` または `HttpContext.Current.User` などのプリンシパル オブジェクトにインターフェイスをキャストする必要がありました。 現在は、これらのプリンシパル オブジェクトで自動的にクレームが処理されます。

フォーム認証では、.NET 4.5 に組み込まれている WIF による利点が得られます。フォームで認証されたすべてのユーザーには自動的にクレームが関連付けられるためです。 この操作方法で示すように、フォーム認証を使用する ASP.NET アプリケーションでは、これらのクレームの使用をすぐに開始することができます。

## <a name="summary-of-steps"></a>手順の要約

- 手順 1 – 簡単な ASP.NET Web フォーム アプリケーションを作成する

- 手順 2 – フォーム認証を使用してクレーム用の ASP.NET Web フォーム アプリケーションを構成する

- 手順 3 – ソリューションをテストする

## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>手順 1 – 簡単な ASP.NET Web フォーム アプリケーションを作成する

この手順では、新しい ASP.NET Web フォーム アプリケーションを作成します。

#### <a name="to-create-a-simple-aspnet-application"></a>簡単な ASP.NET アプリケーションを作成するには

1. Visual Studio を起動し、**[ファイル]**、**[新規作成]**、**[プロジェクト]** の順にクリックします。

2. **[新しいプロジェクト]** ウィンドウで、**[ASP.NET Web フォーム アプリケーション]** をクリックします。

3. **[名前]** で、「`TestApp`」と入力し、**[OK]** をクリックします。

## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-forms-authentication"></a>手順 2 – フォーム認証を使用してクレーム用の ASP.NET Web フォーム アプリケーションを構成する

この手順では、構成エントリを *Web.config* 構成ファイルに追加し、アカウントのクレーム情報を表示するように *Default.aspx* ファイルを編集します。

#### <a name="to-configure-aspnet-application-for-claims-using-forms-authentication"></a>フォーム認証を使用してクレーム用の ASP.NET アプリケーションを構成するには

1. *Default.aspx* ファイルの既存のマークアップを次のように置き換えます。

    ```aspx
    <%@ Page Title="Home Page" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true" CodeBehind="Default.aspx.cs" Inherits="TestApp._Default" %>

    <asp:Content runat="server" ID="BodyContent" ContentPlaceHolderID="MainContent">
        <p>
            This page displays the claims associated with a Forms authenticated user.
        </p>
        <h3>Your Claims</h3>
        <p>
            <asp:GridView ID="ClaimsGridView" runat="server" CellPadding="3">
                <AlternatingRowStyle BackColor="White" />
                <HeaderStyle BackColor="#7AC0DA" ForeColor="White" />
            </asp:GridView>
        </p>
    </asp:Content>
    ```

    この手順では、GridView コントロールを *Default.aspx* ページに追加します。このページには、フォーム認証から取得されたクレームが取り込まれます。

2. *Default.aspx* ファイルを保存し、*Default.aspx.cs* という名前の分離コード ファイルを開きます。 既存のコードを次のコードに置き換えます。

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

                if (claimsPrincipal != null)
                {
                    this.ClaimsGridView.DataSource = claimsPrincipal.Claims;
                    this.ClaimsGridView.DataBind();
                }
            }
        }
    }
    ```

    上記のコードでは、認証済みユーザー (フォーム認証で特定されたユーザーを含む) に関する要求が表示されます。

## <a name="step-3--test-your-solution"></a>手順 3 – ソリューションをテストする

この手順では、ASP.NET Web フォーム アプリケーションをテストし、ユーザーがフォーム認証を使用してサインインするときに、クレームが表示されることを確認します。

#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a>フォーム認証を使用してクレーム用の ASP.NET Web フォーム アプリケーションをテストするには

1. **F5** キーを押してアプリケーションをビルドし、実行します。 ページの右上には、**[登録]** と **[ログイン]** のリンクが表示される *Default.aspx* が表示されます。 **[登録]** をクリックします。

2. **[登録]** ページで、ユーザーアカウントを作成し、**[登録]** をクリックします。 フォーム認証を使用してアカウントが作成され、自動的にサインインされます。

3. ホーム ページにリダイレクトされたら、**Your Claims** 見出しの下の表に、アカウントに関する **Issuer**、**OriginalIssuer**、**Type**、**Value**、および **ValueType** 要求情報が表示されます。
