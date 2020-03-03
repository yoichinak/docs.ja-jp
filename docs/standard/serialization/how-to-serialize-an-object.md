---
title: '方法: オブジェクトをシリアル化する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
ms.assetid: a1207d05-32b2-4953-8582-959607991227
ms.openlocfilehash: a587a132446a5f5d74b2d534b1ca3b93ccca1480
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928990"
---
# <a name="how-to-serialize-an-object"></a>方法: オブジェクトをシリアル化する
オブジェクトをシリアル化するには、まず、シリアル化の対象となるオブジェクトを作成し、パブリック プロパティとパブリック フィールドを設定します。 この処理を行うには、転送形式、つまり XML ストリームをストリームとファイルのいずれとして格納するかを決定する必要があります。 たとえば、XML ストリームを永続的な形式で保存する必要がある場合は、<xref:System.IO.FileStream> オブジェクトを作成します。  
  
> [!NOTE]
> XML シリアル化の例については、「[XML シリアル化の例](../../../docs/standard/serialization/examples-of-xml-serialization.md)」を参照してください。  
  
### <a name="to-serialize-an-object"></a>オブジェクトをシリアル化するには  
  
1. オブジェクトを作成し、パブリック フィールドとパブリック プロパティを設定します。  
  
2. そのオブジェクトの型を使用して、<xref:System.Xml.Serialization.XmlSerializer> を構築します。 詳細については、<xref:System.Xml.Serialization.XmlSerializer> クラスのコンストラクターを参照してください。  
  
3. <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> メソッドを呼び出して、オブジェクトのパブリック プロパティとパブリック フィールドを XML ストリーム形式またはファイル形式のいずれかで生成します。 ファイルを作成する例を次に示します。  
  
    ```vb  
    Dim myObject As MySerializableClass = New MySerializableClass()  
    ' Insert code to set properties and fields of the object.  
    Dim mySerializer As XmlSerializer = New XmlSerializer(GetType(MySerializableClass))  
    ' To write to a file, create a StreamWriter object.  
    Dim myWriter As StreamWriter = New StreamWriter("myFileName.xml")  
    mySerializer.Serialize(myWriter, myObject)  
    myWriter.Close()  
    ```  
  
    ```csharp  
    MySerializableClass myObject = new MySerializableClass();  
    // Insert code to set properties and fields of the object.  
    XmlSerializer mySerializer = new   
    XmlSerializer(typeof(MySerializableClass));  
    // To write to a file, create a StreamWriter object.  
    StreamWriter myWriter = new StreamWriter("myFileName.xml");  
    mySerializer.Serialize(myWriter, myObject);  
    myWriter.Close();  
    ```  
  
## <a name="see-also"></a>関連項目

- [XML シリアル化の概要](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [方法: オブジェクトの逆シリアル化](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
