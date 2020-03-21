---
title: サンプルをインポートします。
ms.date: 03/30/2017
ms.assetid: 3c2c4747-7510-4bdf-b4fe-64f98428ef4a
ms.openlocfilehash: d3456582d73640f1802c17d7f29f4931a6f920b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144631"
---
# <a name="datacontractjsonserializer-sample"></a>サンプルをインポートします。

> [!NOTE]
> このサンプルは、<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>用です。 JSON のシリアル化と逆シリアル化を伴うほとんどのシナリオでは、 [System.Text.Json 名前空間](../../../standard/serialization/system-text-json-overview.md)の API をお勧めします。

<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> では、<xref:System.Runtime.Serialization.DataContractSerializer> と同じ型をサポートしています。 JSON データ形式は、特に Asynchronous JavaScript and XML (AJAX) スタイルの Web アプリケーションを作成するときに便利です。 Windows コミュニケーション ファウンデーション (WCF) での AJAX サポートは、スクリプト マネージャー コントロールを介して ASP.NET AJAX で使用するために最適化されています。 ASP.NET AJAX で Windows 通信基盤 (WCF) を使用する方法の例については、 [AJAX のサンプル](ajax.md)を参照してください。  
  
このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
このサンプルでは、シリアル化および逆シリアル化を示すために、`Person` データ コントラクトを使用しています。  

```csharp
[DataContract]
class Person
{
    [DataMember]
    internal string name;

    [DataMember]
    internal int age;
}
```

 `Person` 型のインスタンスを JSON にシリアル化するには、最初に <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> を作成し、次に `WriteObject` メソッドを使用して JSON データをストリームに書き込みます。  

```csharp
Person p = new Person();
//Set up Person object...
MemoryStream stream1 = new MemoryStream();
DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));
ser.WriteObject(stream1, p);
```

 メモリ ストリームには有効な JSON データが含まれています。
  
```json  
{"age":42,"name":"John"}  
```  
  
 このサンプルでは、JSON データからオブジェクトへの逆シリアル化を示します。 次に、ストリームを巻き戻し、`ReadObject` を呼び出します。  

```csharp
Person p2 = (Person)ser.ReadObject(stream1);
```

 `p2` オブジェクトを調べることで、JSON データが正しく逆シリアル化されていることがわかります。  
  
> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> このディレクトリが存在しない場合は[、.NET Framework 4 の Windows コミュニケーション ファウンデーション (WCF) および Windows ワークフローファウンデーション (WF) サンプル](https://www.microsoft.com/download/details.aspx?id=21459)に移動して、すべての Windows 通信基盤 (WCF) とサンプルを[!INCLUDE[wf1](../../../../includes/wf1-md.md)]ダウンロードします。 このサンプルは、次のディレクトリに格納されます。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\JsonSerialization`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルを設定、ビルド、および実行するには  
  
1. [「Windows コミュニケーション ファンデーション サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)」の説明に従って、ソリューション JsonSerialization.sln をビルドします。  
  
2. 作成されたコンソール アプリケーションを実行します。  
