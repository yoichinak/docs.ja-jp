---
title: Get のトラブルシューティングでは、Windows Communication Foundation のチュートリアルを開始
ms.date: 01/25/2019
ms.assetid: 69a21511-0871-4c41-9a53-93110e84d7fd
ms.openlocfilehash: 8089e0fee262d07be591069982b1aacfbeae2521
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2019
ms.locfileid: "58410499"
---
# <a name="troubleshoot-the-get-started-with-windows-communication-foundation-tutorials"></a>Get のトラブルシューティングでは、Windows Communication Foundation のチュートリアルを開始

この記事では、最も一般的な問題とエラーで手順を実行した場合に発生する可能性がありますソリューションを提供します、[チュートリアル。Windows Communication Foundation アプリケーションの概要](getting-started-tutorial.md)します。 
  
## <a name="common-problems"></a>一般的な問題

**ハード ドライブ上のプロジェクト ファイルが見つからない**

 Visual Studio でプロジェクト ファイルを保存する*C:\Users\\&lt;ユーザー名&gt;\source\repos*します。  

**見つからない、 *App.config*によって生成されたファイル*Svcutil.exe*します。**

 Visual Studio で、**既存項目の追加**ウィンドウでは、既定では、次の拡張子を持つファイルのみが表示されます。 
- *.cs* 
- *.resx* 
- *.settings*
- *.xsd* 
- *.wsdl*

すべてのファイルの種類を表示するには、次のように選択します**すべてのファイル (\*。\*)。** の右上隅にあるドロップダウン リストで、**既存項目の追加**ウィンドウ。  
  
## <a name="common-errors"></a>一般的なエラー

### <a name="compile-the-service-application"></a>サービス アプリケーションをコンパイルします。 

**エラー BC30420 'GettingStartedHost.Module1' で ' Sub Main' が見つかりませんでした。**

Visual Basic アプリケーションのエントリ ポイントが正しくないです。 次の変更を行います。

   1. **ソリューション エクスプ ローラー**ウィンドウで、 **GettingStartedHost**フォルダー、および選択**プロパティ**ショートカット メニューから。
    a.  **GettingStartedHost**  ウィンドウの**スタートアップ オブジェクト**を選択します**Service.Program** (または、特定のアプリケーションのエントリ ポイント) の一覧から。 
    b.  メイン メニューで、次のように選択します。**ファイル** > **すべて保存**します。

### <a name="run-the-service-application"></a>サービス アプリケーションを実行します。 

**HTTP は URL を登録できませんでした ' http:\//+: 8000/GettingStarted/CalculatorService '。プロセスにこの名前空間へのアクセス権がありません。** 

 適切なアクセスの場合に、管理者特権で Windows Communication Foundation (WCF) サービスをホストしているプロセスを開始します。
- For Visual Studio:Visual Studio のプログラムを選択して、**開始**] メニューの [クリックして**詳細** > **管理者として実行**ショートカット メニューから。
- コンソール ウィンドウ。選択**コマンド プロンプト**で、**開始**] メニューの [クリックして**詳細** > **管理者として実行**ショートカットからメニュー。
- Windows explorer:実行可能ファイルを選択し、選択**管理者として実行**ショートカット メニューから。

### <a name="compile-the-client-application"></a>クライアント アプリケーションをコンパイルします。

**'CalculatorClient' の定義を含まない '\<メソッド名 >' 拡張メソッド'\<メソッド名 >' 型 'CalculatorClient' が見つかりませんでしたの最初の引数を受け付ける (が存在することを使用して、ディレクティブ、またはアセンブリ参照。)**  

マークする方法だけ、`ServiceOperationAttribute`属性が一般公開されています。 省略した場合、`ServiceOperationAttribute`のメソッドからの属性、`ICalculator`インターフェイス、コンパイル時にこのエラー メッセージが表示されます。  

**型または名前空間名 'CalculatorClient' が見つかりませんでした (が存在することを使用して、ディレクティブまたはアセンブリ参照)。**

 追加しない場合にこのエラーが発生する、 *generatedProxy.cs* (または*generatedProxy.vb*) ファイルをクライアント プロジェクトでそれらを生成したときに、 *Svcutil.exe*ツール.  

### <a name="run-the-client-application"></a>クライアント アプリケーションを実行します。

**未処理の例外:System.servicemodel.endpointnotfoundexception::接続できませんでした ' http:\//localhost:8000 GettingStarted/CalculatorService '。TCP エラー コード 10061:接続は行われません、ターゲット コンピューターによって拒否されたためです。**

このエラーは、最初にサービスを開始せず、クライアント アプリケーションを実行する場合に発生します。 最初に、サービスを開始するホスト アプリケーションを実行し、クライアント アプリケーションを実行します。

### <a name="use-the-svcutilexe-tool"></a>Svcutil.exe ツールを使用します。
   
**'Svcutil' は内部または外部コマンド、operable program,、またはバッチ ファイルとして認識されていません。**

 *Svcutil.exe*システム パスである必要があります。 最も簡単なソリューションでは、Visual Studio コマンド プロンプトを使用します。 **開始**メニューの 、 **Visual Studio\<バージョン >** ディレクトリを選択して**開発者コマンド プロンプト for VS\<バージョン >**. このコマンド プロンプトでは、Visual Studio の一部として出荷されるすべてのツールの正しい場所をシステム パスを設定します。  
  
### <a name="run-the-service-and-client-applications"></a>サービスとクライアント アプリケーションを実行します。

**System.ServiceModel.Security.SecurityNegotiationException:SOAP セキュリティ ネゴシエーション 'http:\//localhost:8000 GettingStarted/CalculatorService' ターゲット 'http:\//localhost:8000 GettingStarted/CalculatorService' に失敗しました**  

ネットワーク接続がないドメインに参加しているコンピューターでこのエラーが発生します。 コンピューターをネットワークに接続します。 または、サービスとクライアントの両方のセキュリティをオフにします。 

セキュリティを無効にします。

- サービスの交換を作成するコード、`WSHttpBinding`を次のコード。  
  
    ```csharp
    // Step 3: Add a service endpoint.
    selfhost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(SecurityMode.None), "CalculatorService");  
    ```

- 構成ファイルで、クライアントは、更新、 **\<セキュリティ >** の下の要素、 **\<バインド >** 要素として次のとおりです。  
  
    ```xml
    <binding name="WSHttpBinding_ICalculator" security mode="None" />
    ```  

## <a name="see-also"></a>関連項目  
 [WCF アプリケーションを概要します。](getting-started-tutorial.md)  
 [WCF トラブルシューティング クイック スタート](wcf-troubleshooting-quickstart.md)  
 [セットアップ問題のトラブルシューティング](troubleshooting-setup-issues.md)
