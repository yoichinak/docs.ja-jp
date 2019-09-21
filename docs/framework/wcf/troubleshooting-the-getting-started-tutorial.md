---
title: Windows Communication Foundation チュートリアルの開始に関するトラブルシューティング
ms.date: 01/25/2019
ms.assetid: 69a21511-0871-4c41-9a53-93110e84d7fd
ms.openlocfilehash: 10a2f8f718d802a7aab067b882f0d5cf3dc28dca
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928574"
---
# <a name="troubleshoot-the-get-started-with-windows-communication-foundation-tutorials"></a>Windows Communication Foundation チュートリアルの開始に関するトラブルシューティング

この記事で[は、チュートリアルの手順を実行する際に直面する可能性がある最も一般的な問題とエラーの解決策を示します。Windows Communication Foundation アプリケーション](getting-started-tutorial.md)の概要」をご覧ください。 
  
## <a name="common-problems"></a>一般的な問題

**ハードドライブにプロジェクトファイルが見つかりません。**

 Visual Studio では、プロジェクトファイルは *\\C:\Users&gt;&lt;のユーザー名 \ ソース*に保存されます。  

***Svcutil.exe*によって生成された*app.config*ファイルが見つかりません。**

 Visual Studio では、 **[既存項目の追加]** ウィンドウには、既定で次の拡張子を持つファイルのみが表示されます。 

- *.cs* 
- *.resx* 
- *. 設定*
- *.xsd* 
- *.wsdl*

すべてのファイルの種類を表示するには、 **[既存項目の追加]** ウィンドウの右下隅にあるドロップダウンリストで [**すべてのファイル (\*.\*)** ] を選択します。  
  
## <a name="common-errors"></a>一般的なエラー

### <a name="compile-the-service-application"></a>サービスアプリケーションをコンパイルする 

**エラー BC30420 ' Sub Main ' が ' Getting ' に見つかりませんでした。**

Visual Basic アプリケーションのエントリポイントが正しくありません。 次のように変更します。

   1. **[ソリューションエクスプローラー]** ウィンドウで、[ **Getting] ホスト**フォルダーを選択し、ショートカットメニューの **[プロパティ]** をクリックします。
    a. **[Gettingstartup ホスト]** ウィンドウで、 **[スタートアップオブジェクト]** の一覧から **[Service. プログラム]** (または特定のアプリケーションのエントリポイント) を選択します。 
    b. メインメニューから、[**ファイル** > ] **[すべてを保存]** を選択します。

### <a name="run-the-service-application"></a>サービスアプリケーションを実行する 

**Http は URL ' http:\//+: 8000/gettingstarted/計算 atorservice ' を登録できませんでした。プロセスにこの名前空間へのアクセス権がありません。** 

 適切なアクセスを行うには、管理者特権で Windows Communication Foundation (WCF) サービスをホストするプロセスを開始します。

- Visual Studio の場合: **[スタート]** メニューで Visual Studio プログラムを選択し、ショートカットメニューの [**管理者として実行** **] を** > クリックします。
- コンソールウィンドウの場合: **[スタート]** メニューの **[コマンドプロンプト]** を選択し、ショートカットメニューから [**管理者として実行** **] を選択** > します。
- エクスプローラーの場合:実行可能ファイルを選択し、ショートカットメニューから **[管理者として実行]** を選択します。

### <a name="compile-the-client-application"></a>クライアントアプリケーションをコンパイルする

**' 電卓 atorclient ' に '\<method name > ' の定義が含まれていません。また、' 電卓 atorclient ' 型の最初の引数を受け付ける拡張メソッド '\<method name > ' が見つかりませんでした。 using ディレクティブが指定されていないか、アセンブリ参照)**  

`ServiceOperationAttribute`属性でマークしたメソッドだけがパブリックに公開されます。 `ICalculator`インターフェイスのメソッドから`ServiceOperationAttribute`属性を省略すると、コンパイル中にこのエラーメッセージが表示されます。  

**型または名前空間の名前 ' 電卓 Atorclient ' が見つかりませんでした。 using ディレクティブまたはアセンブリ参照が指定されていないことを確認してください。**

 *GeneratedProxy.cs* (または生成された *.vb*) ファイルを*svcutil.exe*ツールで生成したときに、クライアントプロジェクトに追加しない場合、このエラーが発生します。  

### <a name="run-the-client-application"></a>クライアントアプリケーションを実行する

**ハンドルされない例外:EndpointNotFoundException:' Http:\//localhost: 8000/gettingstarted/電卓 atorservice ' に接続できませんでした。TCP エラーコード 10061:ターゲットコンピューターがアクティブに拒否したため、接続できませんでした。**

このエラーは、最初にサービスを開始せずにクライアントアプリケーションを実行した場合に発生します。 最初に、ホストアプリケーションを実行してサービスを開始し、クライアントアプリケーションを実行します。

### <a name="use-the-svcutilexe-tool"></a>Svcutil.exe ツールを使用する
   
**' Svcutil ' は、内部コマンド、外部コマンド、操作可能なプログラム、またはバッチファイルとして認識されません。**

 *Svcutil.exe*はシステムパスになければなりません。 最も簡単な解決策は、Visual Studio コマンドプロンプトを使用することです。 **[スタート]** メニューから [ **Visual Studio \<バージョン >** ディレクトリ] を選択し、[ **VS \<バージョン >** ] で [開発者コマンドプロンプト] を選択します。 このコマンドプロンプトでは、Visual Studio の一部として出荷されたすべてのツールの正しい場所にシステムパスを設定します。  
  
### <a name="run-the-service-and-client-applications"></a>サービスとクライアントアプリケーションを実行する

**System.servicemodel.security.securitynegotiationexception の場合:ターゲット ' http:\/\//localhost: 8000/gettingstarted/計算 atorservice ' に対する ' http:/localhost: 8000/gettingstarted/計算 atorservice ' による SOAP セキュリティネゴシエーションが失敗しました**  

このエラーは、ネットワークに接続されていないドメインに参加しているコンピューターで発生します。 コンピューターをネットワークに接続するか、サービスとクライアントの両方のセキュリティをオフにします。 

セキュリティをオフにするには:

- サービスの場合は、を作成`WSHttpBinding`するコードを次のコードに置き換えます。  
  
    ```csharp
    // Step 3: Add a service endpoint.
    selfhost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(SecurityMode.None), "CalculatorService");  
    ```

- クライアントの構成ファイルで、次のように、  **\<binding >** 要素の下の **\<セキュリティ >** 要素を更新します。  
  
    ```xml
    <binding name="WSHttpBinding_ICalculator" security mode="None" />
    ```  

## <a name="see-also"></a>関連項目  
 [WCF アプリケーションを使ってみる](getting-started-tutorial.md)  
 [WCF トラブルシューティングクイックスタート](wcf-troubleshooting-quickstart.md)  
 [セットアップに関する問題のトラブルシューティング](troubleshooting-setup-issues.md)
