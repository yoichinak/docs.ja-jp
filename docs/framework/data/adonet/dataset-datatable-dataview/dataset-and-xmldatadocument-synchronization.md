---
title: DataSet と XmlDataDocument の同期
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0ce3793d-54b2-47e4-8cf7-b0591cc4dd21
ms.openlocfilehash: 5360a7bce1b5470271bc6b512484964ebb9fd8d1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54587779"
---
# <a name="dataset-and-xmldatadocument-synchronization"></a>DataSet と XmlDataDocument の同期
ADO.NET の <xref:System.Data.DataSet> には、データのリレーショナル表現があります。 階層データにアクセスするには、.NET Framework で使用できる XML クラスを使用できます。 従来、この 2 つのデータ表現は個別に使用されていました。 ただし、.NET Framework により、リアルタイムの同期のアクセスを使用してデータのリレーショナルで階層的な表現の両方に、**データセット**オブジェクトと<xref:System.Xml.XmlDataDocument>オブジェクトに、それぞれします。  
  
 ときに、**データセット**と同期されて、 **XmlDataDocument**、1 つのセットのデータの両方のオブジェクトを操作します。 つまり、変更する場合、**データセット**、変更の反映で、 **XmlDataDocument**、またはその逆。 間のリレーションシップ、**データセット**と**XmlDataDocument**構築されたサービスのスイート全体にアクセスするデータの 1 つのセットを使用して、1 つのアプリケーションを許可することで優れた柔軟性を作成します。周囲、**データセット**(Web フォームと Windows フォームのコントロールや Visual Studio .NET デザイナーを使用)、Extensible Stylesheet Language (XSL)、XSL Transformations (XSLT)、および XML のパスを含む XML サービスのスイートと言語 (XPath)。 アプリケーションでアクセス対象とするサービス セットを選択する必要はありません。どちらのサービス セットにもアクセスできます。  
  
 同期するいくつかの方法がある、**データセット**で、 **XmlDataDocument**します。 次の操作を行うことができます。  
  
-   設定、**データセット**スキーマ (つまり、リレーショナル構造) およびデータを使用し、それを新しい同期**XmlDataDocument**。 この方法では、既存のリレーショナル データの階層ビューが作成されます。 例:  
  
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
  
-   設定、**データセット**スキーマのみを使用 (など、厳密に型指定された**データセット**) と同期する**XmlDataDocument**、し、ロード、 **XmlDataDocument** XML ドキュメントから。 この方法では、既存の階層データのリレーショナル ビューが作成されます。 テーブル名と列名、**データセット**スキーマは同期をとる XML 要素の名前と一致する必要があります。 この名前の一致では、大文字と小文字が区別されます。  
  
     注意のスキーマ、**データセット**のみ、リレーショナル ビューで公開する、XML 要素との一致する必要があります。 つまり、このドキュメント上に非常に大きい XML ドキュメントと非常に小さなリレーショナル ウィンドウを作成できます。 **XmlDataDocument**場合でも、XML ドキュメント全体を保持、**データセット**のみの一部を公開します。 (この詳細な例についてを参照してください[DataSet と XmlDataDocument の同期](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md)。)。  
  
     次のコード例を作成するための手順を示しています、**データセット**と同期し、そのスキーマを読み込み、 **XmlDataDocument**します。 なお、**データセット**スキーマがのみから要素を対応付ける必要があります、 **XmlDataDocument**を使用して公開する、**データセット**します。  
  
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
  
     読み込むことはできません、 **XmlDataDocument**と同期されている場合、**データセット**データを格納します。 読み込もうとすると例外がスローされます。  
  
-   新規作成**XmlDataDocument** 、XML ドキュメントからそれを読み込むしを使用して、データのリレーショナル ビューにアクセスし、**データセット**のプロパティ、 **XmlDataDocument**します。 スキーマを設定する必要がある、**データセット**内のデータのいずれかを表示する前に、 **XmlDataDocument**を使用して、**データセット**します。 テーブル名と列の名前、もう一度、**データセット**スキーマは同期をとる XML 要素の名前と一致する必要があります。 この名前の一致では、大文字と小文字が区別されます。  
  
     次のコード例のデータのリレーショナル ビューにアクセスする方法を示しています、 **XmlDataDocument**します。  
  
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
  
 同期のもう 1 つの利点、 **XmlDataDocument**で、**データセット**は XML ドキュメントの忠実性を保持します。 場合、**データセット**は使用して XML ドキュメントから取得されます**ReadXml**による XML ドキュメントとして返されます、データが書き込まれるときに、 **WriteXml**から大幅に異なる場合があります、元の XML ドキュメントです。 これは、ため、**データセット**、空白文字、または XML ドキュメントからの要素の順序などの階層情報などの書式設定は維持されません。 **データセット**も XML ドキュメントからのスキーマが一致しなかったため無視された要素を含んでいない、**データセット**します。 同期、 **XmlDataDocument**で、**データセット**によりで管理する元の XML ドキュメントの書式設定で階層的な要素の構造、 **XmlDataDocument**中、**データセット**だけデータとスキーマに対応する情報が含まれています、**データセット**します。  
  
 同期するときに、**データセット**で、 **XmlDataDocument**、結果がかどうかに応じて異なる場合があります、<xref:System.Data.DataRelation>オブジェクトが入れ子にします。 詳細については、[Datarelation の入れ子](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [DataSet と XmlDataDocument の同期](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md)  
 厳密に型指定された同期を示して**データセット**、最小限のスキーマで、 **XmlDataDocument**します。  
  
 [DataSet に対する XPath クエリの実行](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/performing-an-xpath-query-on-a-dataset.md)  
 内容に対する XPath クエリの実行を示します、**データセット**します。  
  
 [DataSet への XSLT 変換の適用](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/applying-an-xslt-transform-to-a-dataset.md)  
 内容に XSLT 変換の適用を示して、**データセット**します。  
  
## <a name="related-sections"></a>関連項目  
 [DataSet での XML の使用](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 について説明しますが、どのように**データセット**の内容を保存したりするなど、データ ソースとして XML と対話を**データセット**XML データとして。  
  
 [DataRelation の入れ子化](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 重要性について説明します入れ子になった**DataRelation**オブジェクトの内容を表すときに、**データセット**を XML データとしてこれらのリレーションシップを作成する方法について説明します。  
  
 [DataSet、DataTable、および DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 について説明します、**データセット**とアプリケーション データを管理し、リレーショナル データベースや XML などのデータ ソースと対話する方法。  
  
 <xref:System.Xml.XmlDataDocument>  
 に関するリファレンス情報を含む、 **XmlDataDocument**クラス。  
  
## <a name="see-also"></a>関連項目
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
