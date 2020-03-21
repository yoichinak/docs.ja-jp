---
title: オブジェクトの参照
ms.date: 03/30/2017
ms.assetid: 7a93d260-91c3-4448-8f7a-a66fb562fc23
ms.openlocfilehash: 5eb842e1bff9ba60074379fde5ef3d0597f2184e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183461"
---
# <a name="object-references"></a>オブジェクトの参照
このサンプルでは、サーバーとクライアント間でオブジェクトを参照渡しする方法を示します。 サンプルでは、シミュレートされた*ソーシャルネットワーク*を使用しています。 ソーシャル ネットワークは、友人のリストを含んでいる `Person` クラスで構成され、このリストの各友人は、それぞれ独自の友人のリストを持つ `Person` クラスのインスタンスです。 これにより、オブジェクトのグラフが作成されます。 このようなソーシャル ネットワークに対する操作は、サービスによって公開されます。  
  
 この例では、サービスはインターネット インフォメーション サービス (IIS) によってホストされています。クライアントはコンソール アプリケーション (.exe) です。  
  
> [!NOTE]
> このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
## <a name="service"></a>サービス  
 `Person` クラスに <xref:System.Runtime.Serialization.DataContractAttribute> 属性が適用され、参照型であることを宣言するため <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> フィールドが `true` に設定されます。 すべてのプロパティに <xref:System.Runtime.Serialization.DataMemberAttribute> 属性が適用されます。  
  
```csharp
[DataContract(IsReference=true)]  
public class Person  
{  
    string name;  
    string location;  
    string gender;  
    int age;  
    List<Person> friends;  
    [DataMember()]  
    public string Name  
    {  
        get { return name; }  
        set { name = value; }  
    }  
    [DataMember()]  
    public string Location  
    {  
        get { return location; }  
        set { location = value; }  
    }  
    [DataMember()]  
    public string Gender  
    {  
        get { return gender; }  
        set { gender = value; }  
    }  
…  
}  
```  
  
 `GetPeopleInNetwork` 操作では、`Person` 型のパラメータを受け取り、ネットワーク内のすべてのユーザー (`friends` リストに含まれるすべてのユーザー、友人の友人など) を重複することなく返します。  
  
```csharp
public List<Person> GetPeopleInNetwork(Person p)  
{  
    List<Person> people = new List<Person>();  
    ListPeopleInNetwork(p, people);  
    return people;  
  
}  
```  
  
 `GetMutualFriends` 操作では、`Person` 型のパラメータを受け取り、自分の `friends` リストにこの人物も存在するリスト内のすべての友人を返します。  
  
```csharp
public List<Person> GetMutualFriends(Person p)  
{  
    List<Person> mutual = new List<Person>();  
    foreach (Person friend in p.Friends)  
    {  
        if (friend.Friends.Contains(p))  
            mutual.Add(friend);  
    }  
    return mutual;  
}  
```  
  
 `GetCommonFriends` 操作では、`Person` 型のリストを受け取ります。 このリストには、2 つの `Person` オブジェクトが存在します。 この操作では、入力リストの両方の `Person` オブジェクトの `friends` リスト内にある `Person` オブジェクトのリストを返します。  
  
```csharp
public List<Person> GetCommonFriends(List<Person> people)  
{  
    List<Person> common = new List<Person>();  
    foreach (Person friend in people[0].Friends)  
        if (people[1].Friends.Contains(friend))  
            common.Add(friend);  
    return common;  
}  
```  
  
## <a name="client"></a>Client  
 クライアント プロキシは、Visual Studio の**サービス参照の追加**機能を使用して作成されます。  
  
 5 つの `Person` オブジェクトで構成されるソーシャル ネットワークが作成されます。 クライアントは、サービスの 3 つのメソッドをそれぞれ呼び出します。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1. [Windows コミュニケーションファウンデーション サンプルのワンタイム セットアップ手順を](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)実行したことを確認します。  
  
2. ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3. 単一または複数のコンピューターにまたがる構成でサンプルを実行するには[、「Windows コミュニケーション ファウンデーション サンプルの実行」の手順に](../../../../docs/framework/wcf/samples/running-the-samples.md)従います。  
  
> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> このディレクトリが存在しない場合は[、.NET Framework 4 の Windows コミュニケーション ファウンデーション (WCF) および Windows ワークフローファウンデーション (WF) サンプル](https://www.microsoft.com/download/details.aspx?id=21459)に移動して、すべての Windows 通信基盤 (WCF) とサンプルを[!INCLUDE[wf1](../../../../includes/wf1-md.md)]ダウンロードします。 このサンプルは、次のディレクトリに格納されます。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\ObjectReferences`  
  
## <a name="see-also"></a>関連項目

- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>
- [相互運用可能なオブジェクト参照](../../../../docs/framework/wcf/feature-details/interoperable-object-references.md)
