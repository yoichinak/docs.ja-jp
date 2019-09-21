---
title: DataSet と XmlDataDocument の同期
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0ce3793d-54b2-47e4-8cf7-b0591cc4dd21
ms.openlocfilehash: e76e81153cb7d074fe975744c6b6041ee04be90f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785430"
---
# <a name="dataset-and-xmldatadocument-synchronization"></a>DataSet と XmlDataDocument の同期
ADO.NET の <xref:System.Data.DataSet> には、データのリレーショナル表現があります。 階層データにアクセスするには、.NET Framework で使用できる XML クラスを使用できます。 従来、この 2 つのデータ表現は個別に使用されていました。 ただし、.NET Framework では、データ**セット**オブジェクトと<xref:System.Xml.XmlDataDocument>オブジェクトを使用して、データのリレーショナル表現と階層表現の両方に対してリアルタイムの同期アクセスを行うことができます。  
  
 データ**セット**が**XmlDataDocument**と同期されると、両方のオブジェクトが1つのデータセットを処理します。 これは、**データセット**に変更が加えられた場合、変更が**XmlDataDocument**に反映されることを意味します。また、その逆も同様です。 データセットと XmlDataDocument**の間**の関係により、1つのデータセットを使用して1つのアプリケーションでデータ**セット**を中心に構築されたサービススイート全体にアクセスできるようになり (Web フォームやWindows フォームコントロール、および Visual Studio .NET デザイナー) に加えて、拡張スタイルシート言語 (XSL)、XSL transformation (XSLT)、XML Path Language (XPath) などの XML サービス群が含まれています。 アプリケーションでアクセス対象とするサービス セットを選択する必要はありません。どちらのサービス セットにもアクセスできます。  
  
 **データセット**を**XmlDataDocument**と同期するには、いくつかの方法があります。 次の操作を行うことができます。  
  
- データ**セット**にスキーマ (リレーショナル構造) とデータを設定し、新しい**XmlDataDocument**と同期します。 この方法では、既存のリレーショナル データの階層ビューが作成されます。 例:  
  
    ```vb  
    Dim dataSet As DataSet = New DataSet  
  
    ' Add code here to populate the DataSet with schema and data.  
  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)  
    ```  
  
    ```csharp  
    DataSet dataSet = new DataSet();  
  
    // Add code here to populate the DataSet with schema and data.  
  
    XmlDataDocument xmlDoc = new XmlDataDocument(dataSet);  
    ```  
  
- **データセット**にスキーマのみ (厳密に型指定された**データセット**など) を設定し、それを**XmlDataDocument**と同期してから、XML ドキュメントから**XmlDataDocument**を読み込みます。 この方法では、既存の階層データのリレーショナル ビューが作成されます。 **データセット**スキーマ内のテーブル名と列名は、同期する XML 要素の名前と一致している必要があります。 この名前の一致では、大文字と小文字が区別されます。  
  
     **データセット**のスキーマは、リレーショナルビューで公開する XML 要素とのみ一致する必要があることに注意してください。 つまり、このドキュメント上に非常に大きい XML ドキュメントと非常に小さなリレーショナル ウィンドウを作成できます。 **XmlDataDocument**では、**データセット**が公開している部分がごくわずかでも、XML ドキュメント全体が保持されます。 (詳細な例については、「XmlDataDocument を使用した[データセットの同期](synchronizing-a-dataset-with-an-xmldatadocument.md)」を参照してください)。  
  
     次のコード例は、**データセット**を作成してそのスキーマを設定し、 **XmlDataDocument**と同期する手順を示しています。 **データセット**スキーマは、**データセット**を使用して公開する**XmlDataDocument**の要素とのみ一致する必要があることに注意してください。  
  
    ```vb  
    Dim dataSet As DataSet = New DataSet  
  
    ' Add code here to populate the DataSet with schema, but not data.  
  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)  
    xmlDoc.Load("XMLDocument.xml")  
    ```  
  
    ```csharp  
    DataSet dataSet = new DataSet();  
  
    // Add code here to populate the DataSet with schema, but not data.  
  
    XmlDataDocument xmlDoc = new XmlDataDocument(dataSet);  
    xmlDoc.Load("XMLDocument.xml");  
    ```  
  
     データが含まれているデータ**セット**と同期されている場合、 **XmlDataDocument**を読み込むことはできません。 読み込もうとすると例外がスローされます。  
  
- 新しい**XmlDataDocument**を作成して XML ドキュメントから読み込み、 **XmlDataDocument**のデータ**セット**プロパティを使用してデータのリレーショナルビューにアクセスします。 データセットを使用して**XmlDataDocument**内のデータを表示するには、データ**セット**のスキーマを設定する必要が**あります。** ここでも、**データセット**スキーマ内のテーブル名と列名は、同期する XML 要素の名前と一致している必要があります。 この名前の一致では、大文字と小文字が区別されます。  
  
     次のコード例では、 **XmlDataDocument**内のデータのリレーショナルビューにアクセスする方法を示します。  
  
    ```vb  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument  
    Dim dataSet As DataSet = xmlDoc.DataSet  
  
    ' Add code here to create the schema of the DataSet to view the data.  
  
    xmlDoc.Load("XMLDocument.xml")  
    ```  
  
    ```csharp  
    XmlDataDocument xmlDoc = new XmlDataDocument();  
    DataSet dataSet = xmlDoc.DataSet;  
  
    // Add code here to create the schema of the DataSet to view the data.  
  
    xmlDoc.Load("XMLDocument.xml");  
    ```  
  
 **XmlDataDocument**を**データセット**と同期するもう1つの利点は、XML ドキュメントの忠実性が維持されることです。 **ReadXml**を使用して xml ドキュメントからデータ**セット**を作成した場合、データが**WRITEXML**を使用して xml ドキュメントとして書き戻されると、元の xml ドキュメントとは大きく異なる場合があります。 これは、**データセット**が XML ドキュメントからの空白などの書式設定や要素の順序などの階層情報を保持しないためです。 **データ**セットには、**データセット**のスキーマと一致しなかったために無視された XML ドキュメントの要素も含まれていません。 **XmlDataDocument**と**データセット**を同期すると、元の XML ドキュメントの書式設定と階層要素構造が**XmlDataDocument**に保持されますが、データ**セット**にはデータのみが含まれ、**データセット**に適したスキーマ情報。  
  
 **データセット**を**XmlDataDocument**と同期する場合、 <xref:System.Data.DataRelation>オブジェクトが入れ子になっているかどうかによって結果が異なる場合があります。 詳細については、「 [datarelation の入れ子](nesting-datarelations.md)」を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [DataSet と XmlDataDocument の同期](synchronizing-a-dataset-with-an-xmldatadocument.md)  
 **XmlDataDocument**を使用して、厳密に型指定された**データセット**と最小スキーマを同期する方法を示します。  
  
 [DataSet に対する XPath クエリの実行](performing-an-xpath-query-on-a-dataset.md)  
 **データセット**の内容に対して XPath クエリを実行する方法を示します。  
  
 [DataSet への XSLT 変換の適用](applying-an-xslt-transform-to-a-dataset.md)  
 XSLT 変換を**DataSet**の内容に適用する方法を示します。  
  
## <a name="related-sections"></a>関連項目  
 [DataSet での XML の使用](using-xml-in-a-dataset.md)  
 データセットの内容を XML**データとし**て読み込み、永続化するなど、データ**セット**をデータソースとして xml と対話する方法について説明します。  
  
 [DataRelation の入れ子化](nesting-datarelations.md)  
 **DataSet**の内容を XML データとして表す場合に、入れ子になった**DataRelation**オブジェクトの重要性について説明し、これらの関係を作成する方法について説明します。  
  
 [DataSet、DataTable、および DataView](index.md)  
 データ**セット**と、それを使用してアプリケーションデータを管理し、リレーショナルデータベースや XML などのデータソースと対話する方法について説明します。  
  
 <xref:System.Xml.XmlDataDocument>  
 **XmlDataDocument**クラスに関する参照情報を格納します。  
  
## <a name="see-also"></a>関連項目

- [ADO.NET の概要](../ado-net-overview.md)
