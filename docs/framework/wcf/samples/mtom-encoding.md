---
title: MTOM エンコーディング
ms.date: 03/30/2017
ms.assetid: 820e316f-4ee1-4eb5-ae38-b6a536e8a14f
ms.openlocfilehash: 6cf9606896b153fea2bc70b4d0b1a04a64ece598
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59198102"
---
# <a name="mtom-encoding"></a>MTOM エンコーディング
このサンプルでは、WSHttpBinding で Message Transmission Optimization Mechanism (MTOM) メッセージ エンコーディングを使用する方法を示します。 MTOM は、大きなサイズのバイナリ添付データを、SOAP メッセージを使用して未処理のバイトとして転送するための機構です。これにより、メッセージのサイズを縮小できます。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MTOM`  
  
 既定では、WSHttpBinding はメッセージを標準のテキスト XML として送受信します。 MTOM メッセージの送受信を有効にするには、バインディングの構成で `messageEncoding` 属性を設定するか (次のコード サンプルを参照)、または `MessageEncoding` プロパティを使用して、バインディング上で直接有効にします。 これにより、サービスまたはクライアントで MTOM メッセージを送受信できるようになります。  
  
```xml  
<wsHttpBinding>  
  <binding name="WSHttpBinding_IUpload" messageEncoding="Mtom" />  
</wsHttpBinding>  
```  
  
 MTOM エンコーダでは、バイト配列とストリームを最適化できます。 このサンプルでは、操作に `Stream` パラメータを使用して、最適化できるようにします。  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
  public interface IUpload  
  {  
      [OperationContract]  
      int Upload(Stream data);  
  }  
```
  
 このサンプル用に選択されたコントラクトは、バイナリ データをサービスに転送し、アップロードされたバイト数を戻り値として受け取ります。 サービスをインストールしてクライアントを実行すると、数字の 1000 が出力されます。これは、合計 1,000 バイトのデータが受信されたことを示します。 出力の残りの部分には、さまざまなペイロードの最適化されたメッセージのサイズと最適化されなかったメッセージのサイズが表示されます。  
  
```  
Output:  
1000  
  
Text encoding with a 100 byte payload: 433  
MTOM encoding with a 100 byte payload: 912  
  
Text encoding with a 1000 byte payload: 1633  
MTOM encoding with a 1000 byte payload: 2080  
  
Text encoding with a 10000 byte payload: 13633  
MTOM encoding with a 10000 byte payload: 11080  
  
Text encoding with a 100000 byte payload: 133633  
MTOM encoding with a 100000 byte payload: 101080  
  
Text encoding with a 1000000 byte payload: 1333633  
MTOM encoding with a 1000000 byte payload: 1001080  
  
Press <ENTER> to terminate client.  
```  
  
 MTOM を使用する目的は、大きいサイズのバイナリ ペイロードの転送を最適化することです。 MTOM を使用して SOAP メッセージを送信すると、小さなサイズのバイナリ ペイロードでオーバーヘッドが顕著に表れますが、数千バイトを越すようになるとオーバーヘッドは大きく減少します。 この理由は、標準のテキスト XML が Base64 を使用してバイナリ データをエンコードするためです。このエンコードには 3 バイトごとに 4 文字が必要で、データのサイズは 3 分の 1 増加します。 MTOM はバイナリ データを未処理のバイトとして転送できます。これによりエンコードとデコードの時間が節約でき、その結果メッセージのサイズが小さくなります。 数千バイトというしきい値は、現在のビジネス ドキュメントやデジタル写真のサイズを考えると小さい値です。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  次のコマンドを使用して、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 をインストールします。  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  実行したことを確認、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)します。  
  
3.  ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
4.  1 つまたは複数コンピュータ構成では、サンプルを実行する手順については、 [Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)します。  
