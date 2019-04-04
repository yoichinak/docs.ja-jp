---
title: '方法: WebRequest クラスを使用してデータを要求する'
ms.date: 03/21/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- downloading Internet resources, steps
- requesting data from Internet, steps
- WebRequest class, receiving data
- receiving data, using WebRequest class
- Internet, requesting data
ms.assetid: 368b8d0f-dc5e-4469-a8b8-b2adbf5dd800
ms.openlocfilehash: 1b71327d007e66cc217f6d69e11122c481e5118f
ms.sourcegitcommit: d938c39afb9216db377d0f0ecdaa53936a851059
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2019
ms.locfileid: "58634038"
---
# <a name="how-to-request-data-by-using-the-webrequest-class"></a>方法: WebRequest クラスを使用してデータを要求する
次の手順では、Web ページやファイルなどのリソースをサーバーから要求するための手順について説明します。 リソースは URI で識別される必要があります。  
  
## <a name="to-request-data-from-a-host-server"></a>ホスト サーバーからデータを要求するには  
  
1.  リソースの URI を指定して <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> を呼び出して <xref:System.Net.WebRequest> インスタンスを作成します。 次に例を示します。 
  
    ```csharp  
    WebRequest request = WebRequest.Create("http://www.contoso.com/default.html");  
    ```  
  
    ```vb  
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/default.html")  
    ```  
  
    > [!NOTE]
    > .NET Framework は、*http:*、*https:*、*ftp:*、*file:* で始まる URI に対応する <xref:System.Net.WebRequest> と <xref:System.Net.WebResponse> クラスから派生したプロトコル固有のクラスを提供します。
    プロトコル固有のプロパティを設定する必要がある場合、<xref:System.Net.WebRequest> または <xref:System.Net.WebResponse> オブジェクトをプロトコル固有のオブジェクトの種類にキャストする必要があります。 詳細については、「[プラグ可能なプロトコルのプログラミング](programming-pluggable-protocols.md)」を参照してください。 
  
2.  `WebRequest` オブジェクトで必要なプロパティ値を設定します。 たとえば、認証を有効にするには、<xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> プロパティを <xref:System.Net.NetworkCredential> クラスのインスタンスに設定します。  
  
    ```csharp  
    request.Credentials = CredentialCache.DefaultCredentials;  
    ```  
  
    ```vb  
    request.Credentials = CredentialCache.DefaultCredentials  
    ```  
  
3.  <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType> を呼び出してサーバーに要求を送信します。 このメソッドは、サーバーの応答を格納するオブジェクトを返します。 返された <xref:System.Net.WebResponse> オブジェクトの型は、要求の URI のスキームで決定されます。 次に例を示します。
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
4.  `WebResponse` オブジェクトのプロパティにアクセスするか、またはそれをプロトコル固有インスタンスにキャストして、プロトコル固有のプロパティを読み取ることができます。 

    たとえば、<xref:System.Net.HttpWebResponse> の HTTP 固有のプロパティにアクセスするには、`WebResponse` オブジェクトを `HttpWebResponse` 参照にキャストします。 次のコード例では、応答で送信される HTTP 固有の <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> プロパティを表示する方法を示します。
  
    ```csharp  
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
    ```  
  
    ```vb  
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)  
    ```  
  
5.  サーバーによって送信された応答データを格納しているストリームを取得するには、<xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> メソッドを呼び出します。 次に例を示します。  
  
    ```csharp  
    Stream dataStream = response.GetResponseStream();  
    ```  
  
    ```vb  
    Dim dataStream As Stream = response.GetResponseStream()  
    ```  
  
6.  応答オブジェクトからデータを読み取った後に、<xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> メソッドを使用してそのオブジェクトを閉じるか、<xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> メソッドを使用して応答ストリームを閉じます。 応答オブジェクトまたはストリームのいずれかを閉じないと、アプリケーションからサーバーへの接続が不足し、追加の要求を処理できなくなる可能性があります。 `WebResponse.Close` メソッドは応答を閉じるときに `Stream.Close` を呼び出すため、応答とストリーム オブジェクトの両方で `Close` を呼び出す必要はありませんが、呼び出しても害はありません。 次に例を示します。
  
    ```csharp  
    response.Close();  
    ```  
  
    ```vb  
    response.Close()  
    ```  
  
## <a name="example"></a>例  

次のコード例は、Web サーバーへの要求を作成し、その応答内のデータを読み取る方法を示しています。  
  
```csharp  
using System;  
using System.IO;  
using System.Net;  
using System.Text;  
  
namespace Examples.System.Net  
{  
    public class WebRequestGetExample  
    {  
        public static void Main()  
        {  
            // Create a request for the URL.   
            WebRequest request = WebRequest.Create(  
              "http://www.contoso.com/default.html");  
            // If required by the server, set the credentials.  
            request.Credentials = CredentialCache.DefaultCredentials;  

            // Get the response.  
            WebResponse response = request.GetResponse();  
            // Display the status.  
            Console.WriteLine (((HttpWebResponse)response).StatusDescription);  

            // Get the stream containing content returned by the server.  
            Stream dataStream = response.GetResponseStream();  
            // Open the stream by using a StreamReader for easy access.  
            StreamReader reader = new StreamReader(dataStream);  

            // Read the content.  
            string responseFromServer = reader.ReadToEnd();  
            // Display the content.  
            Console.WriteLine(responseFromServer);  

            // Clean up the response.  
            reader.Close();  
            response.Close();  
        }  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Net  
Imports System.Text  

Namespace Examples.System.Net 

    Public Class WebRequestGetExample  

        Public Shared Sub Main()  

            ' Create a request for the URL.   
            Dim request As WebRequest = _  
              WebRequest.Create("http://www.contoso.com/default.html")  
            ' If required by the server, set the credentials.  
            request.Credentials = CredentialCache.DefaultCredentials  

            ' Get the response.  
            Dim response As WebResponse = request.GetResponse()  
            ' Display the status.  
            Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)  

            ' Get the stream containing content returned by the server.  
            Dim dataStream As Stream = response.GetResponseStream()  
            ' Open the stream by using a StreamReader for easy access.  
            Dim reader As New StreamReader(dataStream)  

            ' Read the content.  
            Dim responseFromServer As String = reader.ReadToEnd()  
            ' Display the content.  
            Console.WriteLine(responseFromServer)  

            ' Clean up the response.  
            reader.Close()  
            response.Close() 

        End Sub   

    End Class  
 
End Namespace  
```  
  
## <a name="see-also"></a>関連項目
- [インターネット要求の作成](creating-internet-requests.md)
- [ネットワーク上でストリームを使用する](using-streams-on-the-network.md)
- [プロキシを介したインターネットへのアクセス](accessing-the-internet-through-a-proxy.md)
- [データの要求](requesting-data.md)
- [方法: WebRequest クラスを使用してデータを送信する](how-to-send-data-using-the-webrequest-class.md)
