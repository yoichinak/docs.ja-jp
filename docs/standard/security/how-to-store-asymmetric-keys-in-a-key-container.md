---
title: '方法: キー コンテナーに非対称キーを格納する'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [.NET Framework], asymmetric keys
- storing asymmetric keys
- keys, asymmetric
- encryption keys
- keys, storing in key containers
- asymmetric keys [.NET Framework]
- encryption [.NET Framework], asymmetric keys
- decryption keys
ms.assetid: 0dbcbd8d-0dcf-40e9-9f0c-e3f162d35ccc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c6fada360eda46dc695ab732a2573b135d823f0a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62018743"
---
# <a name="how-to-store-asymmetric-keys-in-a-key-container"></a>方法: キー コンテナーに非対称キーを格納する
非対称秘密キーは、ローカル コンピューターにそのまま平文として保存しないでください。 秘密キーを格納する必要がある場合は、キー コンテナーを使用することをお勧めします。 キー コンテナーの詳細については、「[コンピューター レベルおよびユーザー レベルの RSA キー コンテナーについて](https://docs.microsoft.com/previous-versions/aspnet/f5cs0acs(v=vs.100))」を参照してください。  
  
### <a name="to-create-an-asymmetric-key-and-save-it-in-a-key-container"></a>非対称キーを作成し、キー コンテナーに格納するには  
  
1. 新しいインスタンスを作成、<xref:System.Security.Cryptography.CspParameters>クラスし、キー コンテナーを呼び出そうと名前を渡す、<xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType>フィールド。  
  
2. 派生したクラスの新しいインスタンスを作成、<xref:System.Security.Cryptography.AsymmetricAlgorithm>クラス (通常は**RSACryptoServiceProvider**または**DSACryptoServiceProvider**) 渡す前に作成したと**CspParameters**コンス トラクターへのオブジェクト。  
  
### <a name="to-delete-the-key-from-a-key-container"></a>キー コンテナーからキーを削除するには  
  
1. **CspParameters** クラスの新しいインスタンスを作成し、キー コンテナーを呼び出すときに使用する名前を **CspParameters.KeyContainerName** フィールドに渡します。  
  
2. **AsymmetricAlgorithm** クラスから派生したクラス (通常は **RSACryptoServiceProvider** または **DSACryptoServiceProvider**) の新しいインスタンスを作成し、前に作成した **CspParameters** オブジェクトをそのコンストラクターに渡します。  
  
3. **AsymmetricAlgorithm** から派生したクラスの **PersistKeyInCSP** プロパティを **false** (Visual Basic では **False**) に設定します。  
  
4. **AsymmetricAlgorithm** から派生したクラスの **Clear** メソッドを呼び出します。 このメソッドは、クラスのすべてのリソースを解放し、キー コンテナーを消去します。   
  
## <a name="example"></a>例  
 非対称キーを作成し、それをキー コンテナーへ格納し、後でキーを取得し、最後にキー コンテナーからキーを削除する方法の例を次に示します。  
  
 `GenKey_SaveInContainer` メソッドと `GetKeyFromContainer` メソッドのコードは類似していることに注意してください。  <xref:System.Security.Cryptography.CspParameters> オブジェクトのキー コンテナー名を指定した場合、<xref:System.Security.Cryptography.AsymmetricAlgorithm> プロパティまたは <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp%2A> プロパティを true に設定して、指定したキー コンテナーを <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp%2A> オブジェクトに渡すと、次のような処理が行われます。  指定した名前のキー コンテナーが存在しない場合、コンテナーが作成されてキーが保持されます。  指定した名前のキー コンテナーが存在する場合、そのコンテナー内のキーが現在の <xref:System.Security.Cryptography.AsymmetricAlgorithm> オブジェクトに自動的に読み込まれます。  つまり、最初に実行される `GenKey_SaveInContainer` メソッドのコードはこのキーを保持し、2 番目に実行される `GetKeyFromContainer` メソッドのコードはこのキーを読み込みます。  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Security.Cryptography  
 _  
  
Public Class StoreKey  
  
    Public Shared Sub Main()  
        Try  
            ' Create a key and save it in a container.  
            GenKey_SaveInContainer("MyKeyContainer")  
  
            ' Retrieve the key from the container.  
            GetKeyFromContainer("MyKeyContainer")  
  
            ' Delete the key from the container.  
            DeleteKeyFromContainer("MyKeyContainer")  
  
            ' Create a key and save it in a container.  
            GenKey_SaveInContainer("MyKeyContainer")  
  
            ' Delete the key from the container.  
            DeleteKeyFromContainer("MyKeyContainer")  
        Catch e As CryptographicException  
            Console.WriteLine(e.Message)  
        End Try  
    End Sub  
  
    Public Shared Sub GenKey_SaveInContainer(ByVal ContainerName As String)  
        ' Create the CspParameters object and set the key container   
        ' name used to store the RSA key pair.  
        Dim cp As New CspParameters()  
        cp.KeyContainerName = ContainerName  
  
        ' Create a new instance of RSACryptoServiceProvider that accesses  
        ' the key container MyKeyContainerName.  
        Dim rsa As New RSACryptoServiceProvider(cp)  
  
        ' Display the key information to the console.  
        Console.WriteLine("Key added to container:  {0}", rsa.ToXmlString(True))  
    End Sub  
  
    Public Shared Sub GetKeyFromContainer(ByVal ContainerName As String)  
        ' Create the CspParameters object and set the key container   
        '  name used to store the RSA key pair.  
        Dim cp As New CspParameters()  
        cp.KeyContainerName = ContainerName  
  
        ' Create a new instance of RSACryptoServiceProvider that accesses  
        ' the key container MyKeyContainerName.  
        Dim rsa As New RSACryptoServiceProvider(cp)  
  
        ' Display the key information to the console.  
        Console.WriteLine("Key retrieved from container : {0}", rsa.ToXmlString(True))  
    End Sub  
  
    Public Shared Sub DeleteKeyFromContainer(ByVal ContainerName As String)  
        ' Create the CspParameters object and set the key container   
        '  name used to store the RSA key pair.  
        Dim cp As New CspParameters()  
        cp.KeyContainerName = ContainerName  
  
        ' Create a new instance of RSACryptoServiceProvider that accesses  
        ' the key container.  
        Dim rsa As New RSACryptoServiceProvider(cp)  
  
        ' Delete the key entry in the container.  
        rsa.PersistKeyInCsp = False  
  
        ' Call Clear to release resources and delete the key from the container.  
        rsa.Clear()  
  
        Console.WriteLine("Key deleted.")  
    End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Security.Cryptography;  
  
public class StoreKey  
  
{  
    public static void Main()  
    {  
        try  
        {  
            // Create a key and save it in a container.  
            GenKey_SaveInContainer("MyKeyContainer");  
  
            // Retrieve the key from the container.  
            GetKeyFromContainer("MyKeyContainer");  
  
            // Delete the key from the container.  
            DeleteKeyFromContainer("MyKeyContainer");  
  
            // Create a key and save it in a container.  
            GenKey_SaveInContainer("MyKeyContainer");  
  
            // Delete the key from the container.  
            DeleteKeyFromContainer("MyKeyContainer");  
        }  
        catch(CryptographicException e)  
        {  
            Console.WriteLine(e.Message);  
        }  
  
    }  
  
    public static void GenKey_SaveInContainer(string ContainerName)  
    {  
        // Create the CspParameters object and set the key container   
        // name used to store the RSA key pair.  
        CspParameters cp = new CspParameters();  
        cp.KeyContainerName = ContainerName;  
  
        // Create a new instance of RSACryptoServiceProvider that accesses  
        // the key container MyKeyContainerName.  
        RSACryptoServiceProvider rsa = new RSACryptoServiceProvider(cp);  
  
        // Display the key information to the console.  
        Console.WriteLine("Key added to container: \n  {0}", rsa.ToXmlString(true));  
    }  
  
    public static void GetKeyFromContainer(string ContainerName)  
    {  
        // Create the CspParameters object and set the key container   
        // name used to store the RSA key pair.  
        CspParameters cp = new CspParameters();  
        cp.KeyContainerName = ContainerName;  
  
        // Create a new instance of RSACryptoServiceProvider that accesses  
        // the key container MyKeyContainerName.  
        RSACryptoServiceProvider rsa = new RSACryptoServiceProvider(cp);  
  
        // Display the key information to the console.  
        Console.WriteLine("Key retrieved from container : \n {0}", rsa.ToXmlString(true));  
    }  
  
    public static void DeleteKeyFromContainer(string ContainerName)  
    {  
        // Create the CspParameters object and set the key container   
        // name used to store the RSA key pair.  
        CspParameters cp = new CspParameters();  
        cp.KeyContainerName = ContainerName;  
  
        // Create a new instance of RSACryptoServiceProvider that accesses  
        // the key container.  
        RSACryptoServiceProvider rsa = new RSACryptoServiceProvider(cp);  
  
        // Delete the key entry in the container.  
        rsa.PersistKeyInCsp = false;  
  
        // Call Clear to release resources and delete the key from the container.  
        rsa.Clear();  
  
        Console.WriteLine("Key deleted.");  
    }  
}  
```  
  
```Output  
Key added to container:  
<RSAKeyValue> Key Information A</RSAKeyValue>  
Key retrieved from container :  
<RSAKeyValue> Key Information A</RSAKeyValue>  
Key deleted.  
Key added to container:  
<RSAKeyValue> Key Information B</RSAKeyValue>  
Key deleted.  
```  
  
## <a name="see-also"></a>関連項目

- [暗号化と復号化のためのキーの生成](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)
- [データの暗号化](../../../docs/standard/security/encrypting-data.md)
- [データの復号化](../../../docs/standard/security/decrypting-data.md)
- [Cryptographic Services](../../../docs/standard/security/cryptographic-services.md)
