---
title: WCF クライアントの概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clients [WCF], architecture
ms.assetid: f60d9bc5-8ade-4471-8ecf-5a07a936c82d
ms.openlocfilehash: 4e502b9917e6a99a8526a2314136841140309083
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64582821"
---
# <a name="wcf-client-overview"></a>WCF クライアントの概要
このセクションでは、クライアント アプリケーションの処理、構成、作成、および Windows Communication Foundation (WCF) クライアントを使用する方法、およびクライアント アプリケーションをセキュリティで保護する方法について説明します。  
  
## <a name="using-wcf-client-objects"></a>WCF クライアント オブジェクトの使用  
 クライアント アプリケーションでは、別のアプリケーションと通信する WCF クライアントを使用するマネージ アプリケーションです。 クライアントを作成するには、WCF サービスのアプリケーションには、次の手順が必要です。  
  
1. サービス エンドポイントのサービス コントラクト、バインディング、およびアドレス情報を取得します。  
  
2. その情報を使用して WCF クライアントを作成します。  
  
3. 操作を呼び出します。  
  
4. WCF クライアント オブジェクトを閉じます。  
  
 この後の各セクションでは、これらの手順について詳しく説明します。また、次の内容についても簡単に説明します。  
  
- エラー処理  
  
- クライアントの構成とセキュリティ保護  
  
- 双方向サービスのコールバック オブジェクトの作成  
  
- サービスの非同期呼び出し  
  
- クライアント チャネルを使用したサービスの呼び出し  
  
## <a name="obtain-the-service-contract-bindings-and-addresses"></a>サービス コントラクト、バインディング、およびアドレスを取得する  
 WCF では、サービスとクライアントは、マネージ属性、インターフェイス、およびメソッドを使用してコントラクトをモデルします。 クライアント アプリケーションからサービスに接続するには、そのサービス コントラクトの型情報を取得する必要があります。 通常、これを行うを使用して、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)、サービスからメタデータをダウンロード、好みの言語でのマネージ ソース コード ファイルに変換し、クライアントを作成します。WCF クライアント オブジェクトを構成に使用できるアプリケーション構成ファイル。 呼び出す、WCF クライアント オブジェクトを作成する場合など、`MyCalculatorService`でそのサービスのメタデータが公開されていることがわかって`http://computerName/MyCalculatorService/Service.svc?wsdl`、次のコード例は、Svcutil.exe を使用して取得する方法を示していますその後、`ClientCode.vb`ファイル。マネージ コードでサービス コントラクトが含まれています。  
  
```  
svcutil /language:vb /out:ClientCode.vb /config:app.config http://computerName/MyCalculatorService/Service.svc?wsdl  
```  
  
 クライアント アプリケーションやクライアント アプリケーションは WCF クライアント オブジェクトを作成し、使用できる別のアセンブリに、このコントラクト コードをコンパイルできます。 構成ファイルを使用してサービスに正しく接続するクライアント オブジェクトを構成できます。  
  
 このプロセスの例は、次を参照してください。[方法。クライアントを作成する](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)します。 コントラクトの詳細については、次を参照してください。[コントラクト](../../../docs/framework/wcf/feature-details/contracts.md)します。  
  
## <a name="create-a-wcf-client-object"></a>WCF クライアント オブジェクトを作成する  
 WCF クライアントは、クライアントがリモート サービスとの通信に使用できる形式で WCF サービスを表すローカル オブジェクトです。 WCF クライアントの種類、対象サービスを実装するコントラクト、サービス操作を呼び出すには、直接クライアント オブジェクトを使用できますし、1 つ作成し、構成したときにします。 WCF ランタイム メソッドの呼び出しをメッセージに変換、サービスに送信、応答をリッスンおよび戻り値として、WCF クライアント オブジェクトにこれらの値を返しますまたは`out`または`ref`パラメーター。  
  
 接続してサービスを使用して WCF クライアント チャネル オブジェクトを使用することもできます。 詳細については、次を参照してください。 [WCF クライアント アーキテクチャ](../../../docs/framework/wcf/feature-details/client-architecture.md)します。  
  
#### <a name="creating-a-new-wcf-object"></a>新しい WCF オブジェクトの作成  
 サービスアプリケーションから次の簡単なサービス コントラクトが生成されていることを前提に、<xref:System.ServiceModel.ClientBase%601> クラスの使用方法を説明します。  
  
> [!NOTE]
>  場合は、WCF クライアントを作成する Visual Studio を使用するオブジェクトに読み込まれます自動的にオブジェクト ブラウザーをプロジェクトにサービス参照を追加する場合。  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 Visual Studio を使用していない場合を拡張する型を検索するコントラクトの生成されたコードを調べる<xref:System.ServiceModel.ClientBase%601>とサービス コントラクト インターフェイス`ISampleService`します。 この場合、この型は次のようなコードになります。  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 このクラスを、コンストラクターの 1 つを使用してローカル オブジェクトとして作成し、構成して、型 `ISampleService` のサービスへの接続に使用できます。  
  
 最初に、WCF クライアント オブジェクトを作成し、それを使用して閉じて、1 つの try/catch ブロック内でお勧めします。 使用しないようにする、`using`ステートメント (`Using` Visual Basic で) 特定のエラー モードでの例外をマスクする場合があるためです。 詳細については、次のセクションを参照してください。 だけでなく[使用終了、中止 WCF クライアントのリソースを解放する](../../../docs/framework/wcf/samples/use-close-abort-release-wcf-client-resources.md)します。  
  
### <a name="contracts-bindings-and-addresses"></a>コントラクト、バインディング、およびアドレス  
 WCF クライアント オブジェクトを作成するには、クライアント オブジェクトを構成する必要があります。 具体的には、サービスがあります*エンドポイント*を使用します。 エンドポイントは、サービス コントラクト、バインディング、およびアドレスの組み合わせです  (エンドポイントの詳細については、次を参照してください。[エンドポイント。アドレス、バインディング、およびコントラクト](../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md))。通常、この情報にある、 [\<エンドポイント >](../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md) Svcutil.exe ツールを生成して、クライアントを作成するときに自動的に読み込まれますなど、クライアントのアプリケーション構成ファイル内の要素オブジェクト。 WCF クライアントの両方の種類では、プログラムでこの情報を指定するためのオーバー ロードもあります。  
  
 たとえば、上記の例で使用した `ISampleService` 用に生成された構成ファイルには、次のエンドポイント情報が含まれます。  
  
 [!code-xml[C_GeneratedCodeFiles#19](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/common/client.exe.config#19)]  
  
 この構成ファイルの `<client>` 要素には、ターゲット エンドポイントが指定されます。 詳細については、複数のターゲット エンドポイントを使用して、次を参照してください。、<xref:System.ServiceModel.ClientBase%601.%23ctor%2A?displayProperty=nameWithType>または<xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A?displayProperty=nameWithType>コンス トラクター。  
  
## <a name="calling-operations"></a>操作の呼び出し  
 1 回クライアント オブジェクトを作成し、構成するには、try/catch ブロックを作成、オブジェクトは、ローカルの場合と同じ方法で操作を呼び出しておよび WCF クライアント オブジェクトを閉じます。 クライアント アプリケーションが最初の操作を呼び出すと WCF は、基になるチャネルを自動的に開き、オブジェクトをリサイクルするときに、基になるチャネルが閉じられます。 (また、他の操作を呼び出す前後にチャネルを明示的に開いたり閉じたりすることもできます)。  
  
 たとえば、次のようなサービス コントラクトを使用する場合があります。  
  
```csharp  
namespace Microsoft.ServiceModel.Samples  
{  
    using System;  
    using System.ServiceModel;  
  
    [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
    public interface ICalculator  
   {  
        [OperationContract]  
        double Add(double n1, double n2);  
        [OperationContract]  
        double Subtract(double n1, double n2);  
        [OperationContract]  
        double Multiply(double n1, double n2);  
        [OperationContract]  
        double Divide(double n1, double n2);  
    }  
}  
```  
  
```vb  
Namespace Microsoft.ServiceModel.Samples  
  
    Imports System  
    Imports System.ServiceModel  
  
    <ServiceContract(Namespace:= _  
    "http://Microsoft.ServiceModel.Samples")> _   
   Public Interface ICalculator  
        <OperationContract> _   
        Function Add(n1 As Double, n2 As Double) As Double  
        <OperationContract> _   
        Function Subtract(n1 As Double, n2 As Double) As Double  
        <OperationContract> _   
        Function Multiply(n1 As Double, n2 As Double) As Double  
        <OperationContract> _   
     Function Divide(n1 As Double, n2 As Double) As Double  
End Interface  
```  
  
 WCF クライアント オブジェクトを作成する操作を呼び出すことができ、次のコード例として、そのメソッドを呼び出すことを示します。 開始タグを呼び出しと WCF クライアント オブジェクトの終了が 1 つの try/catch ブロック内で発生することに注意してください。 詳細については、次を参照してください。[にアクセスするサービスの WCF クライアントを使用して](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md)と[使用終了、中止 WCF クライアントのリソースを解放する](../../../docs/framework/wcf/samples/use-close-abort-release-wcf-client-resources.md)します。  
  
 [!code-csharp[C_GeneratedCodeFiles#20](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#20)]  
  
## <a name="handling-errors"></a>エラー処理  
 基になるクライアント チャネルを開いたとき (明示的に開いた場合、または操作を呼び出すことによって自動的に開いた場合)、クライアントまたはチャネル オブジェクトを使用して操作を呼び出したとき、基になるクライアント チャネルを閉じたときときに、クライアント アプリケーションで例外が発生する可能性があります。 少なくともアプリケーションでは、操作から返される SOAP エラーの結果としてスローされる <xref:System.TimeoutException?displayProperty=nameWithType> オブジェクトに加え、可能性のある <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType> 例外と <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> 例外を処理することをお勧めします。 操作コントラクトで指定されている SOAP エラーは、<xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> としてクライアント アプリケーションに送信されます。ここで、型パラメーターは SOAP エラーの詳細な型です。 クライアント アプリケーションでエラー状態の処理の詳細については、次を参照してください。 [Sending and Receiving Faults](../../../docs/framework/wcf/sending-and-receiving-faults.md)します。 詳細な例に示すクライアントでのエラーを処理する方法を参照してください。[予想例外](../../../docs/framework/wcf/samples/expected-exceptions.md)します。  
  
## <a name="configuring-and-securing-clients"></a>クライアントの構成とセキュリティ保護  
 クライアントを構成するには、まず、そのクライアントまたはチャネル オブジェクトに必要なターゲット エンドポイント情報を読み込みます。通常は構成ファイルから読み込みますが、クライアント コンストラクターとプロパティを使用してプログラムで読み込むこともできます。 ただし、特定のクライアントの動作を有効にし、多くのセキュリティ シナリオに対応するには、追加の構成手順が必要です。  
  
 たとえば、サービス コントラクトのセキュリティ要件はサービス コントラクト インターフェイスに宣言します。Svcutil.exe で構成ファイルを作成した場合、通常そのファイルにはサービスのセキュリティ要件に対応できるバインディングが含まれています。 ただし、クライアント資格情報の構成など、さらに多くのセキュリティ構成が必要な場合もあります。 WCF クライアントのセキュリティの構成については、次を参照してください。[クライアントのセキュリティで保護する](../../../docs/framework/wcf/securing-clients.md)します。  
  
 また、カスタム ランタイム動作など、クライアント アプリケーションでいくつかのカスタム変更を有効にすることもできます。 カスタム クライアント動作を構成する方法の詳細については、次を参照してください。[クライアントの動作を構成する](../../../docs/framework/wcf/configuring-client-behaviors.md)します。  
  
## <a name="creating-callback-objects-for-duplex-services"></a>双方向サービスのコールバック オブジェクトの作成  
 双方向サービスには、コントラクトの要件に従って呼び出すサービスのコールバック オブジェクトを提供するために、クライアント アプリケーションが実装する必要のあるコールバック コントラクトを指定します。 コールバック オブジェクトは完全なサービスではありません (たとえば、コールバック オブジェクトを使用してチャネルを初期化できません) が、実装と構成という目的においては、一種のサービスとして考えることができます。  
  
 双方向サービスのクライアントでは、以下の処理を行う必要があります。  
  
- コールバック コントラクト クラスを実装します。  
  
- コールバック コントラクト実装クラスのインスタンスを作成し、使用して作成する、 <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> WCF クライアント コンス トラクターに渡すオブジェクト。  
  
- 操作を呼び出し、操作のコールバックを処理します。  
  
 双方向の WCF クライアント オブジェクトの関数などの対応する双方向コールバック サービスの構成など、コールバックをサポートするために必要な機能を公開する例外を使用します。  
  
 たとえば、コールバック クラスの <xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType> 属性のプロパティを使用して、コールバック オブジェクトの実行時の動作のさまざまな局面を制御できます。 また、別の例として、<xref:System.ServiceModel.Description.CallbackDebugBehavior?displayProperty=nameWithType> クラスを使用して、例外情報をコールバック オブジェクトを呼び出したサービスに返すこともできます。 詳細については、次を参照してください。[双方向サービス](../../../docs/framework/wcf/feature-details/duplex-services.md)します。 完全なサンプルを参照してください。[双方向](../../../docs/framework/wcf/samples/duplex.md)します。  
  
 インターネット インフォメーション サービス (IIS) 5.1 を実行する Windows XP コンピューターの場合、双方向クライアントでは <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> クラスを使用してクライアントのベース アドレスを指定する必要があります。そうしない場合は例外がスローされます。 次のコード例は、コードでこれを指定する方法を示します。  
  
 [!code-csharp[S_DualHttp#8](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#8)]
 [!code-vb[S_DualHttp#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_dualhttp/vb/module1.vb#8)]  
  
 次のコードは、構成ファイルでこれを指定する方法を示します。  
  
 [!code-csharp[S_DualHttp#134](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#134)]  
  
## <a name="calling-services-asynchronously"></a>サービスの非同期呼び出し  
 操作の呼び出し方法は、クライアント開発者に完全に依存します。 これは、操作を構成するメッセージは、マネージ コードで表現するときに同期メソッドまたは非同期メソッドのどちらかにマップできるためです。 したがって、操作を非同期に呼び出すクライアントを作成する場合、Svcutil.exe の `/async` オプションを使用して非同期クライアント コードを生成できます。 詳細については、「[方法 :サービス操作を非同期的に呼び出す](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)します。  
  
## <a name="calling-services-using-wcf-client-channels"></a>WCF クライアント チャネルを使用したサービスの呼び出し  
 WCF クライアントの型を拡張<xref:System.ServiceModel.ClientBase%601>から派生した<xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>基になるチャネル システムを公開するインターフェイス。 ターゲットのサービス コントラクトと <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> クラスを使用して、サービスを呼び出すことができます。 詳細については、次を参照してください。 [WCF クライアント アーキテクチャ](../../../docs/framework/wcf/feature-details/client-architecture.md)します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>
