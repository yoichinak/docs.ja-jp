---
title: '方法: WCF Web HTTP プログラミング モデルを使用して任意のデータを返すサービスを作成する'
ms.date: 03/30/2017
ms.assetid: 0283955a-b4ae-458d-ad9e-6fbb6f529e3d
ms.openlocfilehash: f5735f4d596e17afc32b1419e9f41fd8a56af410
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157484"
---
# <a name="how-to-create-a-service-that-returns-arbitrary-data-using-the-wcf-web-http-programming-model"></a>方法: WCF Web HTTP プログラミング モデルを使用して任意のデータを返すサービスを作成する
開発者は、データがサービス操作から返される流れを完全に制御する必要が生じることがあります。 これは、サービス操作が WCF でサポートされていない形式のデータを返す必要があるときに、大文字と小文字です。 このトピックでは、WCF WEB HTTP プログラミング モデルを使用して、このようなサービスを作成するについて説明します。 ストリームを返す操作を 1 つ持つサービスを例に取ります。  
  
### <a name="to-implement-the-service-contract"></a>サービス コントラクトを実装するには  
  
1.  サービス コントラクトを定義します。 コントラクトは `IImageServer` と呼ばれ、`GetImage` を返す <xref:System.IO.Stream> というメソッドが入っています。  
  
    ```  
    [ServiceContract]  
        public interface IImageServer  
        {  
            [WebGet]  
            Stream GetImage(int width, int height);  
        }  
    ```  
  
     メソッドを返すため、<xref:System.IO.Stream>適用なしに返されるデータの書式設定、WCF は、操作がサービス操作から返されるバイト数を完全に制御を持つことを想定しています。  
  
2.  サービス コントラクトを実装します。 コントラクトには 1 つの操作 (`GetImage`) しかありません。 このメソッドはビットマップを生成して、それを <xref:System.IO.MemoryStream> に .jpg 形式で保存します。 操作はそのストリームを呼び出し元に戻します。  
  
    ```  
    public class Service : IImageServer  
       {  
           public Stream GetImage(int width, int height)  
           {  
               Bitmap bitmap = new Bitmap(width, height);  
               for (int i = 0; i < bitmap.Width; i++)  
               {  
                   for (int j = 0; j < bitmap.Height; j++)  
                   {  
                       bitmap.SetPixel(i, j, (Math.Abs(i - j) < 2) ? Color.Blue : Color.Yellow);  
                   }  
               }  
               MemoryStream ms = new MemoryStream();  
               bitmap.Save(ms, System.Drawing.Imaging.ImageFormat.Jpeg);  
               ms.Position = 0;  
               WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";  
               return ms;  
           }  
       }  
    ```  
  
     2 番目のコードの最後の行に注意してください。 `WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";`  
  
     コンテンツ タイプのヘッダーにこの設定`"image/jpeg"`します。 この例では .jpg ファイルを戻す方法を示していますが、必要に応じて、任意の種類のデータを任意の形式で戻すように変更できます。 操作はデータを生成または取得してそれをストリームに書き込む必要があります。  
  
### <a name="to-host-the-service"></a>サービスをホストするには  
  
1.  コンソール アプリケーションを作成し、サービスをホストします。  
  
    ```  
    class Program  
    {  
        static void Main(string[] args)  
        {  
        }   
    }  
    ```  
  
2.  変数を作成し、`Main` メソッド内のサービスに使用するベース アドレスを保持します。  
  
    ```  
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3.  サービス クラスとベース アドレスを指定するサービスの <xref:System.ServiceModel.ServiceHost> インスタンスを作成します。  
  
    ```  
    ServiceHost host = new ServiceHost(typeof(Service), new Uri(baseAddress));  
    ```  
  
4.  <xref:System.ServiceModel.WebHttpBinding> と <xref:System.ServiceModel.Description.WebHttpBehavior> を使用して、エンドポイントを追加します。  
  
    ```  
    host.AddServiceEndpoint(typeof(IImageServer), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5.  サービス ホストを開きます。  
  
    ```  
    host.Open()  
    ```  
  
6.  サービスを終了するためにユーザーが Enter キーを押すのを待ちます。  
  
    ```  
    Console.WriteLine("Service is running");  
    Console.Write("Press ENTER to close the host");  
    Console.ReadLine();  
    host.Close();  
    ```  
  
### <a name="to-call-the-raw-service-using-internet-explorer"></a>Internet Explorer を使用して生のサービスを呼び出すには  
  
1.  サービスを実行します。サービスからの次の出力が表示されます。 `Service is running Press ENTER to close the host`  
  
2.  Internet Explorer を開き「`http://localhost:8000/Service/GetImage?width=50&height=40`」と入力します。黄色い長方形とその中心を通る青い斜線が表示されます。  
  
## <a name="example"></a>例  
 この例で使用されているコードの全容を次に示します。  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.ServiceModel;  
using System.ServiceModel.Web;  
using System.ServiceModel.Description;  
using System.IO;  
using System.Drawing;  
  
namespace RawImageService  
{  
    // Define the service contract  
    [ServiceContract]  
    public interface IImageServer  
    {  
        [WebGet]  
        Stream GetImage(int width, int height);  
    }  
  
    // implement the service contract  
    public class Service : IImageServer  
    {  
        public Stream GetImage(int width, int height)  
        {  
            // Although this method returns a jpeg, it can be  
            // modified to return any data you want within the stream  
            Bitmap bitmap = new Bitmap(width, height);  
            for (int i = 0; i < bitmap.Width; i++)  
            {  
                for (int j = 0; j < bitmap.Height; j++)  
                {  
                    bitmap.SetPixel(i, j, (Math.Abs(i - j) < 2) ? Color.Blue : Color.Yellow);  
                }  
            }  
            MemoryStream ms = new MemoryStream();  
            bitmap.Save(ms, System.Drawing.Imaging.ImageFormat.Jpeg);  
            ms.Position = 0;  
            WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";  
            return ms;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
            ServiceHost host = new ServiceHost(typeof(Service), new Uri(baseAddress));  
            host.AddServiceEndpoint(typeof(IImageServer), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
            host.Open();  
            Console.WriteLine("Service is running");  
            Console.Write("Press ENTER to close the host");  
            Console.ReadLine();  
            host.Close();  
  
        }  
    }  
}  
```  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
  
-   コード例のコンパイル時には、System.ServiceModel.dll と System.ServiceModel.Web.dll を参照します。  
  
## <a name="see-also"></a>関連項目

- [WCF Web HTTP プログラミング モデル](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
