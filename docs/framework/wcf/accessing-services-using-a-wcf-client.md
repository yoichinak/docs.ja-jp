---
title: WCF クライアントを使用したサービスへのアクセス
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clients [WCF], consuming services
ms.assetid: d780af9f-73c5-42db-9e52-077a5e4de7fe
ms.openlocfilehash: 97340f8583ef0900645f6db5c453475e85549c55
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54620196"
---
# <a name="accessing-services-using-a-wcf-client"></a>WCF クライアントを使用したサービスへのアクセス

サービスを作成した後、次の手順では、WCF クライアント プロキシを作成します。 クライアント アプリケーションでは、WCF クライアント プロキシを使用して、サービスと通信します。 クライアント アプリケーションは、通常、サービスを呼び出すために使用する WCF クライアント コードを生成するサービスのメタデータをインポートします。

 WCF クライアントを作成するための基本的な手順を以下に示します。

1.  サービス コードをコンパイルします。

2.  WCF クライアント プロキシを生成します。

3.  WCF クライアント プロキシをインスタンス化します。

WCF クライアント プロキシは、サービス モデル メタデータ ユーティリティ ツール (SvcUtil.exe) を使用することによって、手動で生成することができます。詳細は「[ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)」を参照してください。 Visual Studio 内で WCF クライアント プロキシを生成することもを使用して、**サービス参照の追加**機能します。 いずれかの方法で WCF クライアント プロキシを生成するには、サービスが実行中であることが必要です。 サービスが自己ホスト型の場合は、ホストを実行する必要があります。 サービスが IIS/WAS でホストされている場合、特に必要な操作はありません。

## <a name="servicemodel-metadata-utility-tool"></a>ServiceModel メタデータ ユーティリティ ツール
 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)はメタデータからコードを生成するためのコマンド ライン ツールです。 基本的な Svcutil.exe コマンドの使用例を次に示します。

```
Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
```

 また、Svcutil.exe は、ファイル システム上の Web サービス記述言語 (WSDL) ファイルや XML スキーマ定義言語 (XSD) ファイルを指定して使用することもできます。

```
Svcutil.exe <list of WSDL and XSD files on file system>
```

 サービスを呼び出すクライアント アプリケーションが使用できる WCF クライアント コードを含むコード ファイルになります。

 このツールを使用して構成ファイルを生成することもできます。

```
Svcutil.exe <file1 [,file2]>
```

 ファイル名を 1 つだけ指定した場合、それは出力ファイルの名前になります。 ファイル名を 2 つ指定した場合は、1 番目のファイルが入力構成ファイルになり、そのファイルの内容と生成された構成がマージされ、2 番目のファイルに書き出されます。 構成の詳細については、[サービスのバインドを構成する](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)を参照してください。

> [!IMPORTANT]
> セキュリティ保護されていないメタデータ要求には、すべてのセキュリティ保護されていないネットワーク要求を行うのと同じ方法で特定のリスクが発生し得る。通信しているエンドポイントが書かれているユーザーが不明な取得した情報が悪意のあるサービスからメタデータにあります。

## <a name="add-service-reference-in-visual-studio"></a>Visual Studio の "サービス参照の追加"

 サービスの実行とプロジェクトを右クリックは、WCF クライアント プロキシが含まれてし、**追加** > **サービス参照の**します。 **サービス参照の追加 ダイアログ ボックス**を呼び出すし、をクリックするサービスの URL を入力、**移動**ボタンをクリックします。 このダイアログ ボックスには、指定したアドレスで利用可能なサービスの一覧が表示されます。 サービス契約および使用可能な操作を参照してください、生成されたコードの名前空間を指定し、クリックをダブルクリックします、 **OK**ボタンをクリックします。

## <a name="example"></a>例
 サービス用に作成されたコントラクトのコード例を次に示します。

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface ICalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    // Other methods are not shown here.
}
```

```vb
' Define a service contract.
<ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _
Public Interface ICalculator
    <OperationContract()>  _
    Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
    ' Other methods are not shown here.
End Interface
```

 ServiceModel メタデータ ユーティリティ ツールと**サービス参照の追加**Visual Studio で、次の WCF クライアント クラスが生成されます。 このクラスは <xref:System.ServiceModel.ClientBase%601> ジェネリック クラスから継承されたもので、`ICalculator` インターフェイスを実装します。 このツールは、`ICalculator` インターフェイス (この例には表示されていません) も生成します。

```csharp
public partial class CalculatorClient : System.ServiceModel.ClientBase<ICalculator>, ICalculator
{
    public CalculatorClient()
    {}

    public CalculatorClient(string endpointConfigurationName) :
            base(endpointConfigurationName)
    {}

    public CalculatorClient(string endpointConfigurationName, string remoteAddress) :
            base(endpointConfigurationName, remoteAddress)
    {}

    public CalculatorClient(string endpointConfigurationName,
        System.ServiceModel.EndpointAddress remoteAddress) :
            base(endpointConfigurationName, remoteAddress)
    {}

    public CalculatorClient(System.ServiceModel.Channels.Binding binding,
        System.ServiceModel.EndpointAddress remoteAddress) :
            base(binding, remoteAddress)
    {}

    public double Add(double n1, double n2)
    {
        return base.Channel.Add(n1, n2);
    }
}
```

```vb
Partial Public Class CalculatorClient
    Inherits System.ServiceModel.ClientBase(Of ICalculator)
    Implements ICalculator

    Public Sub New()
        MyBase.New
    End Sub

    Public Sub New(ByVal endpointConfigurationName As String)
        MyBase.New(endpointConfigurationName)
    End Sub

    Public Sub New(ByVal endpointConfigurationName As String, ByVal remoteAddress As String)
        MyBase.New(endpointConfigurationName, remoteAddress)
    End Sub

    Public Sub New(ByVal endpointConfigurationName As String,
        ByVal remoteAddress As System.ServiceModel.EndpointAddress)
        MyBase.New(endpointConfigurationName, remoteAddress)
    End Sub

    Public Sub New(ByVal binding As System.ServiceModel.Channels.Binding,
        ByVal remoteAddress As System.ServiceModel.EndpointAddress)
        MyBase.New(binding, remoteAddress)
    End Sub

    Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
        Implements ICalculator.Add
        Return MyBase.Channel.Add(n1, n2)
    End Function
End Class
```

## <a name="using-the-wcf-client"></a>WCF クライアントの使用
 WCF クライアントを使用するには、WCF クライアントのインスタンスを作成し、次のコードに示すように、そのメソッドを呼び出します。

```csharp
// Create a client object with the given client endpoint configuration.
CalculatorClient calcClient = new CalculatorClient("CalculatorEndpoint"));
// Call the Add service operation.
double value1 = 100.00D;
double value2 = 15.99D;
double result = calcClient.Add(value1, value2);
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
```

```vb
' Create a client object with the given client endpoint configuration.
Dim calcClient As CalculatorClient = _
New CalculatorClient("CalculatorEndpoint")

' Call the Add service operation.
Dim value1 As Double = 100.00D
Dim value2 As Double = 15.99D
Dim result As Double = calcClient.Add(value1, value2)
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)
```

## <a name="debugging-exceptions-thrown-by-a-client"></a>クライアントによってスローされた例外のデバッグ

WCF クライアントによってスローされる多くの例外は、サービスで例外が原因です。 いくつかの例を次に示します。

-   <xref:System.Net.Sockets.SocketException>:既存の接続は、リモート ホストによって強制的に切断されました。

-   <xref:System.ServiceModel.CommunicationException>:基になる接続が予期せず閉じられました。

-   <xref:System.ServiceModel.CommunicationObjectAbortedException>:ソケット接続が中止されました。 これは、メッセージ処理時のエラー、リモート ホストでの受信タイムアウトの超過、または基になるネットワーク リソースの問題が原因で発生する可能性があります。

このような種類の例外が発生した場合、問題を解決するには、サービス側でトレースをオンにし、そこで発生した例外を特定することをお勧めします。 トレースの詳細については、[トレース](../../../docs/framework/wcf/diagnostics/tracing/index.md)と[を使用して、アプリケーションのトラブルシューティングのトレース](../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)を参照してください。

## <a name="see-also"></a>関連項目

- [方法: クライアントを作成します。](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [方法: Access Services と双方向コントラクト](../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)
- [方法: サービス操作を非同期的に呼び出す](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)
- [方法: 一方向のサービスにアクセスし、要求/応答コントラクト](../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)
- [方法: WSE 3.0 にアクセス サービス](../../../docs/framework/wcf/feature-details/how-to-access-a-wse-3-0-service-with-a-wcf-client.md)
- [生成されたクライアント コードの理解](../../../docs/framework/wcf/feature-details/understanding-generated-client-code.md)
- [方法: アプリケーション起動時間の WCF クライアント、XmlSerializer を使用して向上させる](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)
- [クライアントのランタイム動作の指定](../../../docs/framework/wcf/specifying-client-run-time-behavior.md)
- [クライアントの動作の構成](../../../docs/framework/wcf/configuring-client-behaviors.md)
