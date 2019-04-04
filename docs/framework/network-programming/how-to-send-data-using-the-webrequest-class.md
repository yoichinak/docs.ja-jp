---
title: '方法: WebRequest クラスを使用してデータを送信する'
ms.date: 03/25/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebRequest class, sending data to a host
- Sending data to a host, using WebRequest class
ms.assetid: 66686878-38ac-4aa6-bf42-ffb568ffc459
ms.openlocfilehash: 591a1129625a4ff08c9aa37ce651bbc0320ff25d
ms.sourcegitcommit: d938c39afb9216db377d0f0ecdaa53936a851059
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2019
ms.locfileid: "58634272"
---
# <a name="how-to-send-data-by-using-the-webrequest-class"></a>方法: WebRequest クラスを使用してデータを送信する
次の手順では、サーバーにデータを送信するための手順について説明します。 この手順は、通常、Web ページへのデータをポストするときに使用されます。 
  
## <a name="to-send-data-to-a-host-server"></a>ホスト サーバーにデータを送信するには  
  
1.  スクリプトや ASP.NET ページなど、データを受け取るリソースの URI を指定して <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> を呼び出すことによって <xref:System.Net.WebRequest> インスタンスを作成します。 次に例を示します。 
  
    ```csharp  
    WebRequest request = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx");  
    ```  
  
    ```vb  
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx")  
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
  
3.  HTTP `POST` メソッドなど、要求と共にデータを送信することを許可するプロトコル メソッドを指定します。  
  
    ```csharp  
    request.Method = "POST";  
    ```  
  
    ```vb  
    request.Method = "POST"  
    ```  
  
4.  要求で含めるバイト数に <xref:System.Web.HttpRequest.ContentLength> プロパティを設定します。 次に例を示します。 
  
    ```csharp  
    request.ContentLength = byteArray.Length;  
    ```  
  
    ```vb  
    request.ContentLength = byteArray.Length  
    ```  
  
5.  <xref:System.Web.HttpRequest.ContentType> プロパティに適切な値を設定します。 次に例を示します。
  
    ```csharp  
    request.ContentType = "application/x-www-form-urlencoded";  
    ```  
  
    ```vb  
    request.ContentType = "application/x-www-form-urlencoded"  
    ```  
  
6.  <xref:System.Net.WebRequest.GetRequestStream%2A> メソッドを呼び出すことで、要求のデータを保持するストリームを取得します。 次に例を示します。
  
    ```csharp  
    Stream dataStream = request.GetRequestStream();  
    ```  
  
    ```vb  
    Stream dataStream = request.GetRequestStream()  
    ```  
  
7.  `GetRequestStream` メソッドによって返される <xref:System.IO.Stream> オブジェクトにデータを書き込みます。 次に例を示します。
  
    ```csharp  
    dataStream.Write(byteArray, 0, byteArray.Length);  
    ```  
  
    ```vb  
    dataStream.Write(byteArray, 0, byteArray.Length)  
    ```  
  
8.  <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> メソッドを呼び出すことで、要求のストリームを閉じます。 次に例を示します。
  
    ```csharp  
    dataStream.Close();  
    ```  
  
    ```vb  
    dataStream.Close()  
    ```  
  
9. <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType> を呼び出してサーバーに要求を送信します。 このメソッドは、サーバーの応答を格納するオブジェクトを返します。 返された `WebResponse` オブジェクトの型は、要求の URI のスキームで決定されます。 次に例を示します。
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
10. `WebResponse` オブジェクトのプロパティにアクセスするか、またはそれをプロトコル固有インスタンスにキャストして、プロトコル固有のプロパティを読み取ることができます。 

    たとえば、<xref:System.Net.HttpWebResponse> の HTTP 固有のプロパティにアクセスするには、`WebResponse` オブジェクトを <xref:System.Net.HttpWebResponse> 参照にキャストします。 次のコード例では、応答で送信される HTTP 固有の <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> プロパティを表示する方法を示します。
  
    ```csharp  
    Console.WriteLine(((HttpWebResponse)response).StatusDescription);    
    ```  
  
    ```vb  
    Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)  
    ```  
  
11. サーバーによって送信された応答データを格納しているストリームを取得するには、`WebResponse` オブジェクトの <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> メソッドを呼び出します。 次に例を示します。
  
    ```csharp  
    Stream dataStream = response.GetResponseStream();  
    ```  
  
    ```vb  
    Dim dataStream As Stream = response.GetResponseStream()  
    ```  
  
12. 応答オブジェクトからデータを読み取った後に、<xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> メソッドを使用してそのオブジェクトを閉じるか、<xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> メソッドを使用して応答ストリームを閉じます。 応答またはストリームのいずれかを閉じないと、アプリケーションからサーバーへの接続が不足し、追加の要求を処理できなくなる可能性があります。 `WebResponse.Close` メソッドは応答を閉じるときに `Stream.Close` を呼び出すため、応答とストリーム オブジェクトの両方で `Close` を呼び出す必要はありませんが、呼び出しても害はありません。 次に例を示します。
  
    ```csharp  
    response.Close();  
    ```  
  
    ```vb  
    response.Close()  
    ```  
  
## <a name="example"></a>例  
  
次のコード例は、Web サーバーにデータを送信し、その応答内のデータを読み取る方法を示しています。  

```csharp  
using System;  
using System.IO;  
using System.Net;  
using System.Text;  
  
namespace Examples.System.Net  
{  
    public class WebRequestPostExample  
    {  
        public static void Main()  
        {  
            // Create a request by using a URL that can receive a post.   
            WebRequest request = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx ");  
            // Set the Method property of the request to POST.  
            request.Method = "POST";  

            // Create POST data and convert it to a byte array.  
            string postData = "This is a test that posts this string to a Web server.";  
            byte[] byteArray = Encoding.UTF8.GetBytes(postData);  

            // Set the ContentType property of the request.  
            request.ContentType = "application/x-www-form-urlencoded";  
            // Set the ContentLength property of the request.  
            request.ContentLength = byteArray.Length;  

            // Get the request stream.  
            Stream dataStream = request.GetRequestStream();  
            // Write the data to the request stream.  
            dataStream.Write(byteArray, 0, byteArray.Length);  
            // Close the stream.  
            dataStream.Close();  

            // Get the response.  
            WebResponse response = request.GetResponse();  
            // Display the status.  
            Console.WriteLine(((HttpWebResponse)response).StatusDescription);  

            // Get the stream containing content returned by the server.  
            dataStream = response.GetResponseStream();  
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

    Public Class WebRequestPostExample  
  
        Public Shared Sub Main()  

            ' Create a request by using a URL that can receive a post.   
            Dim request As WebRequest = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx ")  
            ' Set the Method property of the request to POST.  
            request.Method = "POST"  

            ' Create POST data and convert it to a byte array.  
            Dim postData As String = "This is a test that posts this string to a Web server."  
            Dim byteArray As Byte() = Encoding.UTF8.GetBytes(postData)  

            ' Set the ContentType property of the WebRequest.  
            request.ContentType = "application/x-www-form-urlencoded"  
            ' Set the ContentLength property of the WebRequest.  
            request.ContentLength = byteArray.Length  

            ' Get the request stream.  
            Dim dataStream As Stream = request.GetRequestStream()  
            ' Write the data to the request stream.  
            dataStream.Write(byteArray, 0, byteArray.Length)  
            ' Close the stream.  
            dataStream.Close()  

            ' Get the response.  
            Dim response As WebResponse = request.GetResponse()  
            ' Display the status.  
            Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)  

            ' Get the stream containing content returned by the server.  
            dataStream = response.GetResponseStream()  
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
- [方法: WebRequest クラスを使用してデータを要求する](how-to-request-data-using-the-webrequest-class.md)
