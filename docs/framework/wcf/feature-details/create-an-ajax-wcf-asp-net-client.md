---
title: Visual Studio で、AJAX 対応 WCF サービスと ASP.NET クライアントを作成します。
ms.date: 08/17/2018
ms.assetid: 95012df8-2a66-420d-944a-8afab261013e
ms.openlocfilehash: 06fa3a9d0151f3b4b865c421f9960854ef471377
ms.sourcegitcommit: 89fcad7e816c12eb1299128481183f01c73f2c07
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "63807886"
---
# <a name="how-to-create-an-ajax-enabled-wcf-service-and-an-aspnet-client-that-accesses-the-service"></a>方法: サービスにアクセスする、AJAX 対応 WCF サービスと ASP.NET クライアントを作成します。

このトピックでは、Visual Studio を使用して、AJAX 対応の Windows Communication Foundation (WCF) サービスと、サービスにアクセスする ASP.NET クライアントを作成する方法を示します。

## <a name="create-an-aspnet-web-app"></a>ASP.NET Web アプリを作成する

1. Visual Studio を開きます。

1. **ファイル**メニューの **新規** > **プロジェクト**

1. **新しいプロジェクト**ダイアログ ボックスで、展開、**インストール済み** > **Visual c#** > **Web**カテゴリ、し、選択**ASP.NET Web アプリケーション (.NET Framework)** します。

1. プロジェクトに名前を**SandwichServices**  をクリック**OK**します。

1. **新しい ASP.NET Web アプリケーション**ダイアログ ボックスで、**空**選び**OK**。

   ![Visual Studio で ASP.NET web アプリの種類のダイアログ](media/create-an-ajax-wcf-asp-net-client/new-asp-net-web-app-type.png)

## <a name="add-a-web-form"></a>Web フォームを追加します。

1. SandwichServices プロジェクトを右クリックして**ソリューション エクスプ ローラー**選択**追加** > **新しい項目の**します。

1. **新しい項目の追加**ダイアログ ボックスで、展開、**インストール済み** > **Visual c#** > **Web**カテゴリ、し、選択、 **Web フォーム**テンプレート。

1. 既定の名前 (**WebForm1**)、し、**追加**します。

   *WebForm1.aspx*で開きます**ソース**ビュー。

1. 内で次のマークアップを追加、 **\<本文 >** タグ。

   ```html
   <input type="button" value="Price of 3 sandwiches" onclick="Calculate()"/>
   <br />
   <span id="additionResult"></span>
   ```

## <a name="create-an-ajax-enabled-wcf-service"></a>AJAX 対応 WCF サービスを作成します。

1. SandwichServices プロジェクトを右クリックして**ソリューション エクスプ ローラー**選択**追加** > **新しい項目の**します。

1. **新しい項目の追加**ダイアログ ボックスで、展開、**インストール済み** > **Visual c#** > **Web**カテゴリ、し、選択、 **(AJAX 対応) WCF サービス**テンプレート。

   ![Visual Studio での WCF サービス (AJAX 対応) の項目テンプレート](media/create-an-ajax-wcf-asp-net-client/add-wcf-service.png)

1. サービスの名前を付けます**CostService**選び**追加**。

   *CostService.svc.cs*エディターで開きます。

1. サービスの操作を実装します。 サンドイッチの量のコストを計算する CostService クラスには、次のメソッドを追加します。

    ```csharp
    [OperationContract]
    public double CostOfSandwiches(int quantity)
    {
        return 1.25 * quantity;
    }
    ```

## <a name="configure-the-client-to-access-the-service"></a>サービスにアクセスするクライアントを構成します。

1. 開く、 *WebForm1.aspx*選択ファイルを開き、**デザイン**ビュー。

2. **ビュー**メニューの **ツールボックス**します。

3. 展開、 **AJAX Extensions**ノードやドラッグ アンド ドロップ、 **ScriptManager**フォーム上にします。

4. 戻り、**ソース**間に次のコードを追加、表示、  **\<ScriptManager >** WCF サービスへのパスを指定するタグ。

    ```xml
    <Services>
       <asp:ServiceReference Path="~/CostService.svc" />
    </Services>
    ```

5. Javascript 関数のコードを追加`Calculate()`します。 次のコードを配置、**ヘッド**web フォームのセクション。

    ```html
    <script type="text/javascript">

        function Calculate() {
            CostService.CostOfSandwiches(3, onSuccess);
        }

        function onSuccess(result) {
            var myres = $get("additionResult");
            myres.innerHTML = result;
        }

    </script>
    ```

   このコードの 3 つのサンドイッチの価格を計算する CostService メソッドを呼び出すしと呼ばれる範囲内に結果を表示**しくみが**します。

## <a name="run-the-program"></a>プログラムを実行する

確認します*WebForm1.aspx*にフォーカスがあり、キーを押します**開始**web クライアントを起動するボタンをクリックします。 ボタンが緑色の三角形とような**IIS Express (Microsoft Edge)** します。 または、キーを押して**F5**します。 をクリックして、 **3 sandwiches の価格**ある「3.75」想定される出力を生成するボタンをクリックします。

## <a name="example-code"></a>コード例

完全なコードを次に、 *CostService.svc.cs*ファイル。

```csharp
using System.ServiceModel;
using System.ServiceModel.Activation;

namespace SandwichServices
{
    [ServiceContract(Namespace = "")]
    [AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]
    public class CostService
    {
        [OperationContract]
        public double CostOfSandwiches(int quantity)
        {
            return 1.25 * quantity;
        }
    }
}
```

すべての内容を次に、 *WebForm1.aspx*ページ。

```aspx-csharp
<%@ Page Language="C#" AutoEventWireup="true" CodeBehind="WebForm1.aspx.cs" Inherits="SandwichServices.WebForm1" %>

<!DOCTYPE html>

<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
    <title></title>
    <script type="text/javascript">

        function Calculate() {
            CostService.CostOfSandwiches(3, onSuccess);
        }

        function onSuccess(result) {
            var myres = $get("additionResult");
            myres.innerHTML = result;
        }

    </script>
</head>
<body>
    <form id="form1" runat="server">
        <div>
        </div>
        <asp:ScriptManager ID="ScriptManager1" runat="server">
            <Services>
                <asp:ServiceReference Path="~/CostService.svc" />
            </Services>
        </asp:ScriptManager>

        <input type="button" value="Price of 3 sandwiches" onclick="Calculate()" />
        <br />
        <span id="additionResult"></span>
    </form>
</body>
</html>
```
