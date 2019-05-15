---
title: '方法: XML ファイルにオブジェクト データを書き込む (C#)'
ms.date: 07/20/2015
ms.assetid: 7681eb98-703d-4005-a369-26a7bca0f894
ms.openlocfilehash: a4fdb496e3b015b2e3b46c9705ba1c05c20423f0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64595526"
---
# <a name="how-to-write-object-data-to-an-xml-file-c"></a>方法: XML ファイルにオブジェクト データを書き込む (C#)
<xref:System.Xml.Serialization.XmlSerializer> クラスを使用して、クラスから XML ファイルにオブジェクトを書き込む例を次に示します。  
  
## <a name="example"></a>例  
  
```csharp  
public class XMLWrite  
{  
  
   static void Main(string[] args)  
    {  
        WriteXML();  
    }  
  
    public class Book  
    {  
        public String title;   
    }  
  
    public static void WriteXML()  
    {  
        Book overview = new Book();  
        overview.title = "Serialization Overview";  
        System.Xml.Serialization.XmlSerializer writer =   
            new System.Xml.Serialization.XmlSerializer(typeof(Book));  
  
        var path = Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments) + "//SerializationOverview.xml";  
        System.IO.FileStream file = System.IO.File.Create(path);  
  
        writer.Serialize(file, overview);  
        file.Close();  
    }  
}  
```  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 クラスには、パラメーターのないパブリック コンストラクターが必要です。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
- シリアル化されるクラスにパブリックなパラメーターなしのコンストラクターがない場合  
  
- ファイルが存在するものの、読み取り専用の場合 (<xref:System.IO.IOException>)  
  
- パスが長すぎる (<xref:System.IO.PathTooLongException>)。  
  
- ディスクの空き領域がない場合 (<xref:System.IO.IOException>)  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 次のコード例では、ファイルが存在しない場合は新規にファイルを作成します。 アプリケーションでファイルを作成する必要がある場合、そのアプリケーションにはフォルダーに対する `Create` アクセスが必要です。 ファイルが既に存在する場合、アプリケーションに必要なのは、より低い権限である `Write` アクセスだけです。 フォルダーに対して `Read` アクセスを許可するのではなく、可能な限りアプリケーションの配置時にファイルを作成しておき、1 つのファイルに対してのみ `Create` アクセスを許可する方が安全です。  
  
## <a name="see-also"></a>関連項目

- <xref:System.IO.StreamWriter>
- [方法: XML ファイルからオブジェクト データを読み込む (C#)](../../../../csharp/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)
- [シリアル化 (C#)](../../../../csharp/programming-guide/concepts/serialization/index.md)
