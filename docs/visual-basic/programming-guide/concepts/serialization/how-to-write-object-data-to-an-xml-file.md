---
title: '方法: オブジェクトのデータを書き込む XML ファイル (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: f7966480-5ed2-43ac-9894-33427436de2a
ms.openlocfilehash: 52b896b0191f29f68cc31e02fc325638ca6341b4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783501"
---
# <a name="how-to-write-object-data-to-an-xml-file-visual-basic"></a>方法: オブジェクトのデータを書き込む XML ファイル (Visual Basic)
<xref:System.Xml.Serialization.XmlSerializer> クラスを使用して、クラスから XML ファイルにオブジェクトを書き込む例を次に示します。  
  
## <a name="example"></a>例  
  
```vb  
Public Module XMLWrite  
  
    Sub Main()  
        WriteXML()  
    End Sub  
  
    Public Class Book  
        Public Title As String  
    End Class  
  
    Public Sub WriteXML()  
        Dim overview As New Book  
        overview.Title = "Serialization Overview"  
        Dim writer As New System.Xml.Serialization.XmlSerializer(GetType(Book))  
        Dim file As New System.IO.StreamWriter(  
            "c:\temp\SerializationOverview.xml")  
        writer.Serialize(file, overview)  
        file.Close()  
    End Sub  
End Module  
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
- [方法: XML ファイル (Visual Basic) からオブジェクト データを読み込む](../../../../visual-basic/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)
- [シリアル化 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md)
