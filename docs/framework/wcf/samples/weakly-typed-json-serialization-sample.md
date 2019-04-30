---
title: 弱い型指定の JSON のシリアル化のサンプル
ms.date: 03/30/2017
ms.assetid: 0b30e501-4ef5-474d-9fad-a9d559cf9c52
ms.openlocfilehash: b0e9617ad5d616e8921fbf142085f2758f3e0cd4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62006357"
---
# <a name="weakly-typed-json-serialization-sample"></a>弱い型指定の JSON のシリアル化のサンプル
特定のワイヤ形式にユーザー定義型をシリアル化するときや、ユーザー定義型にワイヤ形式を逆シリアル化するときは、そのユーザー定義型がサービスとクライアントの両方で使用可能である必要があります。 通常、これを実現するために、 <xref:System.Runtime.Serialization.DataContractAttribute> 属性がこのユーザー定義型に適用され、 <xref:System.Runtime.Serialization.DataMemberAttribute> 属性がそのメンバに適用されます。 このメカニズムも適用されます、JavaScript Object Notation (JSON) オブジェクトを使用する場合、トピックの説明に従って[方法。および JSON データを逆シリアル化](../../../../docs/framework/wcf/feature-details/how-to-serialize-and-deserialize-json-data.md)します。  
  
 一部のシナリオで、Windows Communication Foundation (WCF) サービスまたはクライアントは、サービスまたは開発者のコントロールの外側にあるクライアントによって生成された JSON オブジェクトにアクセスする必要があります。 その他の Web サービスは、JSON Api をパブリックに公開、WCF 開発者がローカルのユーザー定義型を任意の JSON オブジェクトを逆シリアル化を構築するため実用的でないになることができます。 このサンプルでは、ユーザー定義型を作成せずに、逆シリアル化された、任意の JSON オブジェクトを使用する WCF の開発者を有効にするメカニズムを提供します。 このしくみは、JSON オブジェクトが逆シリアル化される型がコンパイル時に不明なため、JSON オブジェクトの *弱い型指定のシリアル化* と呼ばれます。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 たとえば、パブリック Web サービスの API によって、このサービスのユーザーに関する情報の一部を記述した次の JSON オブジェクトが返されるとします。  
  
```json  
{"personal": {"name": "Paul", "age": 23, "height": 1.7, "isSingle": true, "luckyNumbers": [5,17,21]}, "favoriteBands": ["Band ABC", "Band XYZ"]}  
```  
  
 このオブジェクトを逆シリアル化するには、WCF クライアントは次のユーザー定義型を実装する必要があります。  
  
```  
[DataContract]  
 public class MemberProfile  
 {  
     [DataMember]  
     public PersonalInfo personal;  
  
     [DataMember]  
     public string[] favoriteBands;  
 }  
  
 [DataContract]  
 public class PersonalInfo  
 {  
     [DataMember]  
     public string name;  
  
     [DataMember]  
     public int age;  
  
     [DataMember]  
     public double height;  
  
     [DataMember]  
     public bool isSingle;  
  
     [DataMember]  
     public int[] luckyNumbers;  
 }  
```  
  
 この手順は、特にクライアントが複数の型の JSON オブジェクトを処理する必要がある場合に、複雑になる可能性があります。  
  
 このサンプルで示す `JsonObject` 型では、逆シリアル化された JSON オブジェクトの弱い型指定の表現を使用します。 `JsonObject` は、JSON オブジェクトと [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ディクショナリ間の自然な割り当て、および JSON 配列と [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 配列間の割り当てに依存しています。 `JsonObject` 型のコードを次に示します。  
  
```  
// Instantiation of JsonObject json omitted  
  
string name = json["root"]["personal"]["name"];  
int age = json["root"]["personal"]["age"];  
double height = json["root"]["personal"]["height"];  
bool isSingle = json["root"]["personal"]["isSingle"];  
int[] luckyNumbers = {  
                                     json["root"]["personal"]["luckyNumbers"][0],  
                                     json["root"]["personal"]["luckyNumbers"][1],  
                                     json["root"]["personal"]["luckyNumbers"][2]   
                                 };  
string[] favoriteBands = {  
                                        json["root"]["favoriteBands"][0],  
                                        json["root"]["favoriteBands"][1]  
                                    };  
```  
  
 コンパイル時に型を宣言せずに、JSON オブジェクトと配列を "参照" できます。 トップレベルの `["root"]` オブジェクトの詳細については、「 [Mapping Between JSON and XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md)」トピックで説明されているように、JavaScript Object Notation (JSON) オブジェクトを使用する場合にも適用されます。  
  
> [!NOTE]
>  `JsonObject` クラスは、例としてのみ提供されています。 テストが完全には行われていないため、運用環境では使用しないでください。 弱い型指定の JSON のシリアル化の明確な影響の 1 つは、 `JsonObject`の使用時にタイプ セーフがなくなることです。  
  
 `JsonObject` 型を使用するには、クライアント操作コントラクトで <xref:System.ServiceModel.Channels.Message> を戻り値の型として使用する必要があります。  
  
```  
[ServiceContract]  
    interface IClientSideProfileService  
    {  
        // There is no need to write a DataContract for the complex type returned by the service.  
        // The client will use a JsonObject to browse the JSON in the received message.  
  
        [OperationContract]  
        [WebGet(ResponseFormat = WebMessageFormat.Json)]  
        Message GetMemberProfile();  
    }  
```  
  
 次のコードに示すように、 `JsonObject` がインスタンス化されます。  
  
```  
// Code to instantiate IClientSideProfileService channel omitted…  
  
// Make a request to the service and obtain the Json response  
XmlDictionaryReader reader = channel.GetMemberProfile().GetReaderAtBodyContents();  
  
// Go through the Json as though it is a dictionary. There is no need to map it to a .NET CLR type.  
JsonObject json = new JsonObject(reader);  
```  
  
 `JsonObject` コンストラクタは、 <xref:System.Xml.XmlDictionaryReader>メソッドを使用して取得される <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> を受け取ります。 リーダーには、クライアントによって受信された JSON メッセージの XML 表現が含まれています。 詳細については、トピックを参照してください。 [Mapping Between JSON and XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md)します。  
  
 このプログラムの出力は、次のようになります。  
  
```  
Service listening at http://localhost:8000/.  
To view the JSON output from the sample, navigate to http://localhost:8000/GetMemberProfile  
This is Paul's page. I am 23 years old and I am 1.7 meters tall.  
I am single.  
My lucky numbers are 5, 17, and 21.  
My favorite bands are Band ABC and Band XYZ.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1. 実行したことを確認、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)します。  
  
2. 「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の説明に従って、ソリューション WeaklyTypedJson.sln をビルドします。  
  
3. ソリューションを実行します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Ajax\WeaklyTypedJson`  
