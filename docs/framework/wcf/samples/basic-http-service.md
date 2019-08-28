---
title: 基本的な HTTP サービス
ms.date: 03/30/2017
ms.assetid: 27048b43-8a54-4f2a-9952-594bbfab10ad
ms.openlocfilehash: ec716b41efb3dde6e5afdb386d797e402d924b56
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045160"
---
# <a name="basic-http-service"></a>基本的な HTTP サービス

このサンプルでは、Windows Communication Foundation (WCF) REST プログラミングモデルを使用して、"POX" (Plain Old XML) サービスと呼ばれる HTTP ベースの RPC ベースのサービスよくを実装する方法を示します。 このサンプルは、自己ホスト型 WCF HTTP サービス (Service.cs) と、サービスを作成して呼び出しを行うコンソールアプリケーション (Program.cs) という2つのコンポーネントで構成されています。

## <a name="sample-details"></a>サンプルの詳細

WCF サービスは、と`EchoWithGet` `EchoWithPost`という2つの操作を公開します。これらの操作は、入力として渡された文字列を返します。

`EchoWithGet` 操作には、この操作で HTTP <xref:System.ServiceModel.Web.WebGetAttribute> 要求が処理されることを示す、`GET` という注釈が付いています。 <xref:System.ServiceModel.Web.WebGetAttribute> では明示的に <xref:System.UriTemplate> を指定しないため、操作には `s` という名前のクエリ文字列パラメーターを使用して渡される入力文字列が必要です。 サービスが要求する URI の形式は、<xref:System.ServiceModel.Web.WebGetAttribute.UriTemplate%2A> プロパティを使用してカスタマイズすることができます。

`EchoWithPost` 操作には、これが `GET` 操作ではなく、副作用があることを示す、<xref:System.ServiceModel.Web.WebInvokeAttribute> という注釈が付いています。 <xref:System.ServiceModel.Web.WebInvokeAttribute> では明示的に `Method` を指定しないため、この操作は、要求本文に文字列が含まれる HTTP `POST` 要求を処理します (XML 形式など)。 HTTP メソッド、要求の URI の形式は、それぞれ <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> プロパティ、<xref:System.ServiceModel.Web.WebInvokeAttribute.UriTemplate> プロパティを使用して、カスタマイズすることができます。

App.config ファイルでは、<xref:System.ServiceModel.Description.WebHttpEndpoint> に設定されている <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> プロパティを持つ既定の `true` を使用して、WCF サービスを構成します。 その結果、WCF インフラストラクチャによって、サービスへの http 要求を`http://localhost:8000/Customers/help`作成する方法とサービスの http 応答を使用する方法に関する情報を提供する、の自動 HTML ベースのヘルプページが作成されます。

Program.cs は、WCF チャネルファクトリを使用してサービスへの呼び出しを行い、応答を処理する方法を示しています。 これは、WCF サービスにアクセスする 1 つの方法にすぎません。 <xref:System.Net.HttpWebRequest> や <xref:System.Net.WebClient> などの他の .NET Framework クラスを使用して、サービスにアクセスすることも可能です。

このサンプルは、コンソール アプリケーション内で実行される自己ホスト型サービスとクライアントで構成されています。 コンソール アプリケーションが実行されると、クライアントはサービスに要求を発行し、応答からの適切な情報をコンソール ウィンドウに書き込みます。

#### <a name="to-use-this-sample"></a>このサンプルを使用するには

1. 基本的な HTTP サービス サンプルのソリューションを開きます。 Visual Studio 2012 を起動する場合、サンプルを正常に実行するには、管理者としてを実行する必要があります。 これを行うには、Visual Studio 2012 アイコンを右クリックし、コンテキストメニューから **[管理者として実行]** を選択します。

2. Ctrl キーと Shift キーを押しながら B キーを押してソリューションをビルドし、Ctrl キーを押しながら F5 キーを押してコンソール アプリケーションを、デバッグを行わずに実行します。 コンソール ウィンドウが表示されて、実行中のサービスの URI および実行中のサービスの HTML ヘルプ ページの URI が示されます。 ブラウザーでヘルプ ページの URI を入力することで、いつでも HTML ヘルプ ページを表示することができます。 サンプルが実行されると、クライアントは現在のアクティビティのステータスを書き込みます。

3. 任意のキーを押して、サンプルを終了します。

> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780)にアクセスして、すべての[!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (wcf) とサンプルをダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\BasicHttpService`
