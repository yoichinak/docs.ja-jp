---
title: DataContractSerializer と DataContractResolver を使用した NetDataContractSerializer 機能の提供
ms.date: 03/30/2017
ms.assetid: 1376658f-f695-45f7-a7e0-94664e9619ff
ms.openlocfilehash: 481d9d7f30f9c2137ec91a87c9743dcb0a97baf7
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816812"
---
# <a name="using-datacontractserializer-and-datacontractresolver-to-provide-the-functionality-of-netdatacontractserializer"></a>DataContractSerializer と DataContractResolver を使用した NetDataContractSerializer 機能の提供
このサンプルでは、<xref:System.Runtime.Serialization.DataContractSerializer> を適切な <xref:System.Runtime.Serialization.DataContractResolver> と共に使用して、<xref:System.Runtime.Serialization.NetDataContractSerializer> と同じ機能を提供する方法を示します。 このサンプルで示すのは、<xref:System.Runtime.Serialization.DataContractResolver> を作成して <xref:System.Runtime.Serialization.DataContractSerializer> に追加する方法です。

## <a name="sample-details"></a>サンプルの詳細
 <xref:System.Runtime.Serialization.NetDataContractSerializer> は、1 つの重要な点で <xref:System.Runtime.Serialization.DataContractSerializer> とは異なります。<xref:System.Runtime.Serialization.NetDataContractSerializer> はシリアル化された XML の中に CLR 型情報を含みますが、<xref:System.Runtime.Serialization.DataContractSerializer> にはこの情報は含まれません。 したがって、<xref:System.Runtime.Serialization.NetDataContractSerializer> は、シリアル化と逆シリアル化の両方で、同一の CLR 型を共有する結果になる場合のみ使用できます。 ただし、<xref:System.Runtime.Serialization.DataContractSerializer> よりも優れたパフォーマンスが得られるため、<xref:System.Runtime.Serialization.NetDataContractSerializer> を使用することをお勧めします。 <xref:System.Runtime.Serialization.DataContractSerializer> を追加することによって、<xref:System.Runtime.Serialization.DataContractResolver> でシリアル化される情報を変更することができます。

 このサンプルは、2 つのプロジェクトで構成されます。 最初のプロジェクトでは、<xref:System.Runtime.Serialization.NetDataContractSerializer> を使用してオブジェクトをシリアル化します。 2 番目のプロジェクトでは、<xref:System.Runtime.Serialization.DataContractSerializer> を <xref:System.Runtime.Serialization.DataContractResolver> と共に使用して、最初のプロジェクトと同じ機能を提供します。

 次のコード例では、DCSwithDCR プロジェクトの <xref:System.Runtime.Serialization.DataContractResolver> に追加される `MyDataContractResolver` という名前のカスタム <xref:System.Runtime.Serialization.DataContractSerializer> の実装を示します。

```csharp
class MyDataContractResolver : DataContractResolver
{
    private XmlDictionary dictionary = new XmlDictionary();

    public MyDataContractResolver()
    {
    }

    // Used at deserialization
    // Allows users to map xsi:type name to any Type
    public override Type ResolveName(string typeName, string typeNamespace, DataContractResolver knownTypeResolver)
    {
        Type type = knownTypeResolver.ResolveName(typeName, typeNamespace, null);
        if (type == null)
        {
            type = Type.GetType(typeName + ", " + typeNamespace);
        }
        return type;
    }

    // Used at serialization
    // Maps any Type to a new xsi:type representation
    public override void ResolveType(Type dataContractType, DataContractResolver knownTypeResolver, out XmlDictionaryString typeName, out XmlDictionaryString typeNamespace)
    {
        knownTypeResolver.ResolveType(dataContractType, null, out typeName, out typeNamespace);
        if (typeName == null || typeNamespace == null)
        {
            XmlDictionary dictionary = new XmlDictionary();
            typeName = dictionary.Add(dataContractType.FullName);
            typeNamespace = dictionary.Add(dataContractType.Assembly.FullName);
        }
    }
}
```

#### <a name="to-use-this-sample"></a>このサンプルを使用するには

1.  Visual Studio 2012 を使用して、DCRSample.sln ソリューション ファイルを開きます。

2.  ソリューション ファイルを右クリックし **プロパティ**します。

3.  **ソリューション プロパティ ページ**ダイアログで、**共通プロパティ**、**スタートアップ プロジェクト**を選択します**マルチ スタートアップ プロジェクト:** します。

4.  次に、 **DCSwithDCR**プロジェクトで、**開始**から、**アクション**ドロップダウンします。

5.  次に、 **NetDCS**プロジェクトで、**開始**から、**アクション**ドロップダウンします。

6.  クリックして**OK**ダイアログ ボックスを閉じます。

7.  ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。

8.  ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。

> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\NetDcSasDcSwithDCR`  
  
