---
title: '方法: Svcutil.exe を使用してコンパイル済みのサービス コードからメタデータをエクスポートする'
ms.date: 03/30/2017
ms.assetid: 95d0aed3-16a2-4398-89bb-39418eeb7355
ms.openlocfilehash: b8ddbaf896ee4c6ea8b6f8e8ce7d0ecef28140ea
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932567"
---
# <a name="how-to-use-svcutilexe-to-export-metadata-from-compiled-service-code"></a>方法: Svcutil.exe を使用してコンパイル済みのサービス コードからメタデータをエクスポートする
Svcutil.exe は、次のように、コンパイル済みアセンブリのサービス、コントラクト、およびデータ型のメタデータをエクスポートできます。  
  
- Svcutil.exe を使用して、アセンブリのセットに対するすべてのコンパイル済みサービス コントラクトのメタデータをエクスポートするには、入力パラメーターとして各アセンブリを指定します。 これは既定の動作です。  
  
- Svcutil.exe を使用して、コンパイル済みサービスのメタデータをエクスポートするには、入力パラメーターとしてサービス アセンブリを指定します。 `/serviceName` オプションを使用して、エクスポートするサービスの構成名を指定する必要があります。 Svcutil.exe を実行すると、指定した実行可能アセンブリの構成ファイルが自動的に読み込まれます。  
  
- アセンブリ セットのすべてのデータ コントラクト型をエクスポートするには、`/dataContractOnly` オプションを使用します。  
  
> [!NOTE]
> `/reference` オプションを使用して、任意の依存アセンブリへのファイル パスを指定してください。  
  
### <a name="to-export-metadata-for-compiled-service-contracts"></a>コンパイル済みサービス コントラクトのメタデータをエクスポートするには  
  
1. サービス コントラクトの実装を 1 つ以上のクラス ライブラリにコンパイルします。  
  
2. コンパイルされたアセンブリに対して Svcutil.exe を実行します。  
  
    > [!NOTE]
    > 依存アセンブリへのファイル パスを指定するには、`/reference` スイッチを使用する必要があります。  
  
    ```  
    svcutil.exe Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-a-compiled-service"></a>コンパイル済みサービスのメタデータをエクスポートするには  
  
1. サービスの実装を実行可能アセンブリにコンパイルします。  
  
2. サービス実行可能ファイルの構成ファイルを作成し、サービス構成を追加します。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name="MyService" >  
            <endpoint address="finder" contract="IPeopleFinder" binding="wsHttpBinding" />  
          </service>  
        </services>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
3. コンパイルされたサービス実行可能ファイルに対して Svcutil.exe を実行します。その際、`/serviceName` スイッチを使用してサービスの構成名を指定してください。  
  
    > [!NOTE]
    > 依存アセンブリへのファイル パスを指定するには、`/reference` スイッチを使用する必要があります。  
  
    ```  
    svcutil.exe /serviceName:MyService Service.exe /reference:path/Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-compiled-data-contracts"></a>コンパイル済みデータ コントラクトのメタデータをエクスポートするには  
  
1. データ コントラクトの実装を 1 つ以上のクラス ライブラリにコンパイルします。  
  
2. コンパイルされたアセンブリに対して Svcutil.exe を実行します。その際、`/dataContract` スイッチを使用して、データ コントラクトのメタデータだけが生成されるように指定してください。  
  
    > [!NOTE]
    > 依存アセンブリへのファイル パスを指定するには、`/reference` スイッチを使用する必要があります。  
  
    ```  
    svcutil.exe /dataContractOnly Contracts.dll  
    ```  
  
## <a name="example"></a>例  
 単純なサービス実装および構成のメタデータを生成する方法を次の例に示します。  
  
 サービス コントラクトのメタデータをエクスポートするには、次のように指定します。  
  
```  
svcutil.exe Contracts.dll  
```  
  
 データ コントラクトのメタデータをエクスポートするには、次のように指定します。  
  
```  
svcutil.exe /dataContractOnly Contracts.dll  
```  
  
 サービス実装のメタデータをエクスポートするには、次のように指定します。  
  
```  
svcutil.exe /serviceName:MyService Service.exe /reference:<path>/Contracts.dll  
```  
  
 `<path>` は Contracts.dll へのパスです。  
  
```  
// The following service contract and data contracts are compiled into   
// Contracts.dll.  
[ServiceContract(ConfigurationName="IPeopleFinder")]  
public interface IPersonFinder  
{  
    [OperationContract]  
    Address GetAddress(Person s);  
}  
  
[DataContract]  
public class Person  
{  
    [DataMember]  
    public string firstName;  
    [DataMember]  
    public string lastName;  
    [DataMember]  
    public int age;  
}  
  
[DataContract]  
public class Address  
{  
    [DataMember]  
    public string city;  
    [DataMember]  
    public string state;  
    [DataMember]  
    public string street;  
    [DataMember]  
    public int zipCode;  
    [DataMember]  
    public Person person;  
}  
  
// The following service implementation is compiled into Service.exe.     
// This service uses the contracts specified in Contracts.dll.  
[ServiceBehavior(ConfigurationName = "MyService")]  
public class MyService : IPersonFinder  
{  
    public Address GetAddress(Person person)  
    {  
        Address address = new Address();  
        address.person = person;  
        return address;  
    }  
}  
  
<!-- The following is the configuration file for Service.exe. -->  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="MyService">  
         <endpoint  address="finder"  
                    binding="basicHttpBinding"  
                    contract="IPeopleFinder"/>  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [メタデータのエクスポートとインポート](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)
