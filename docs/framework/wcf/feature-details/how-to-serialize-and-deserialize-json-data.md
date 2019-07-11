---
title: '方法: JSON データをシリアル化および逆シリアル化する'
ms.date: 03/25/2019
ms.assetid: 88abc1fb-8196-4ee3-a23b-c6934144d1dd
ms.openlocfilehash: 0c56b298737dc9b9902f13c586edffb3d05257f8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783008"
---
# <a name="how-to-serialize-and-deserialize-json-data"></a>方法: および JSON データを逆シリアル化
JSON (JavaScript Object Notation) は、クライアント ブラウザーと AJAX 対応の Web サービスとの間で、少量のデータを高速に交換できる効率的なデータ エンコード形式です。  
  
 この記事では、JSON でエンコードされたデータに .NET 型のオブジェクトをシリアル化して、JSON 形式でデータをシリアル化の .NET 型のインスタンスに戻す方法を示します。 この例では、データ コントラクトを使用して、シリアル化と逆シリアル化ユーザー定義の方法を示します`Person`使用して型<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>します。  
  
 通常、JSON のシリアル化および逆シリアル化は自動的に処理 Windows Communication Foundation (WCF) によって AJAX 対応エンドポイント経由で公開されているサービス操作でデータ コントラクト型を使用する場合。 ただし、場合によっては、JSON データを直接操作する必要があります。   
  
> [!NOTE]
>  サーバーまたは他の何らかの送信応答のシリアル化中にエラーが発生した場合に返されないことが取得をクライアントにエラーとして。  
  
 この記事がに基づいて、 [JSON のシリアル化](../samples/json-serialization.md)サンプル。  
  
## <a name="to-define-the-data-contract-for-a-person-type"></a>Person 型のデータ コントラクトを定義するには 
  
1. クラスに `Person` をアタッチし、シリアル化するメンバーに <xref:System.Runtime.Serialization.DataContractAttribute> 属性をアタッチすることで、<xref:System.Runtime.Serialization.DataMemberAttribute> のデータ コントラクトを定義します。 データ コントラクトの詳細については、次を参照してください。[サービス コントラクトの設計](../designing-service-contracts.md)します。  
  
    ```csharp  
    [DataContract]  
    internal class Person  
    {  
        [DataMember]  
        internal string name;  
  
        [DataMember]  
        internal int age;  
    }  
    ```  
  
## <a name="to-serialize-an-instance-of-type-person-to-json"></a>Person 型のインスタンスを JSON にシリアル化するには  
  
1. `Person` 型のインスタンスを作成します。  
  
    ```csharp  
    var p = new Person();  
    p.name = "John";  
    p.age = 42;  
    ```  
  
2. シリアル化、`Person`オブジェクトをメモリ ストリームを使用して、<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>します。  
  
    ```csharp  
    var stream1 = new MemoryStream();  
    var ser = new DataContractJsonSerializer(typeof(Person));  
    ```  
  
3. JSON データをストリームに書き込むには、<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> メソッドを使用します。  
  
    ```csharp  
    ser.WriteObject(stream1, p);  
    ```  
  
4. JSON の出力を表示します。  
  
    ```csharp  
    stream1.Position = 0;  
    var sr = new StreamReader(stream1);  
    Console.Write("JSON form of Person object: ");  
    Console.WriteLine(sr.ReadToEnd());  
    ```  
  
## <a name="to-deserialize-an-instance-of-type-person-from-json"></a>JSON から Person 型のインスタンスに逆シリアル化するには  
  
1. `Person` の <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> メソッドを使用して、JSON エンコードされたデータを <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> の新しいインスタンスに逆シリアル化します。  
  
    ```csharp  
    stream1.Position = 0;  
    var p2 = (Person)ser.ReadObject(stream1);  
    ```  
  
2. 結果を表示します。  
  
    ```csharp  
    Console.WriteLine($"Deserialized back, got name={p2.name}, age={p2.age}");  
    ```  
  
## <a name="example"></a>例  
  
```csharp  
// Create a User object and serialize it to a JSON stream.  
public static string WriteFromObject()  
{  
    // Create User object.  
    var user = new User("Bob", 42);  
  
    // Create a stream to serialize the object to.  
    var ms = new MemoryStream();  
  
    // Serializer the User object to the stream.  
    var ser = new DataContractJsonSerializer(typeof(User));  
    ser.WriteObject(ms, user);  
    byte[] json = ms.ToArray();  
    ms.Close();  
    return Encoding.UTF8.GetString(json, 0, json.Length);  
}  
  
// Deserialize a JSON stream to a User object.  
public static User ReadToObject(string json)  
{  
    var deserializedUser = new User();  
    var ms = new MemoryStream(Encoding.UTF8.GetBytes(json));  
    var ser = new DataContractJsonSerializer(deserializedUser.GetType());  
    deserializedUser = ser.ReadObject(ms) as User;  
    ms.Close();  
    return deserializedUser;  
}  
```  
  
> [!NOTE]
>  JSON シリアライザーは、次のサンプル コードに示すように、データ コントラクターの複数のメンバーが同じ名前である場合、シリアル化例外をスローします。  
  
```csharp  
[DataContract]  
public class TestDuplicateDataBase  
{  
    [DataMember]  
    public int field1 = 123;  
}

[DataContract]  
public class TestDuplicateDataDerived : TestDuplicateDataBase  
{  
    [DataMember]  
    public new int field1 = 999;  
}  
```  
  
## <a name="see-also"></a>関連項目

- [スタンドアロン JSON のシリアル化](stand-alone-json-serialization.md)
- [JSON のサポートおよびその他のデータ転送の形式](support-for-json-and-other-data-transfer-formats.md)
