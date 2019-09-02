---
title: DiffGrams
ms.date: 03/30/2017
ms.assetid: 037f3991-7bbc-424b-b52e-8b03585d3e34
ms.openlocfilehash: b9e6fb4ce1c2c7ee7d081a1cb2106d30960853c7
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204880"
---
# <a name="diffgrams"></a>DiffGrams
DiffGram は、データ要素の現在のバージョンと元のバージョンを識別する XML 形式です。 <xref:System.Data.DataSet> では、 の内容を読み込んで永続化するため、およびネットワーク接続経由で転送する場合にこの内容をシリアル化するために、DiffGram 形式が使用されます。 が diffgram として書き込まれると、のスキーマで<xref:System.Data.DataSet>はなく、コンテンツを正確に再作成するために必要なすべての情報が diffgram に挿入されます。ただし、**元**の列と<xref:System.Data.DataSet> **現在**の行のバージョン、行のエラー情報、および行の順序。  
  
 XML Web サービスから <xref:System.Data.DataSet> を送信または取得するときには、DiffGram 形式が暗黙的に使用されます。 また、ReadXml メソッドを使用して<xref:System.Data.DataSet> xml からのコンテンツを読み込むとき、または WriteXml メソッドを使用<xref:System.Data.DataSet>してのコンテンツを xml で書き込むときに、コンテンツを DiffGram として読み取るか書き込むように指定できます。 詳細については、「 [xml からの dataset の読み込み](loading-a-dataset-from-xml.md)」と「 [xml データとしての dataset の内容の書き込み](writing-dataset-contents-as-xml-data.md)」を参照してください。  
  
 .NET Framework では、DiffGram 形式は主に <xref:System.Data.DataSet> の内容をシリアル化するときの形式として使用されますが、Microsoft SQL Server データベース内のテーブル データを変更するときにも DiffGrams を使用できます。  
  
 Diffgram は、すべてのテーブルの内容を **\<diffgram >** 要素に書き込むことによって生成されます。  
  
### <a name="to-generate-a-diffgram"></a>Diffgram を生成するには  
  
1. ルート テーブル (親を一切持たないテーブル) のリストを生成します。  
  
2. リストの各テーブルとその子孫について、すべての行の現在のバージョンを最初の Diffgram セクションに書き込みます。  
  
3. の<xref:System.Data.DataSet>各テーブルについて、Diffgram の **\<before >** セクションに、すべての行の元のバージョン (存在する場合) を記述します。  
  
4. エラーのある行については、エラーの内容を Diffgram の **\<errors >** セクションに書き込みます。  
  
 Diffgram は XML ファイルの上から下に向かって処理されます。  
  
### <a name="to-process-a-diffgram"></a>Diffgram を処理するには  
  
1. Diffgram の最初のセクションを処理します。このセクションには、行の現在のバージョンが格納されています。  
  
2. 変更および削除された行の元の行バージョンを含む、2番目または **\<前の >** セクションを処理します。  
  
    > [!NOTE]
    > 行が削除済みとしてマークされていた場合、削除操作によってその行の子孫も削除される場合があります。この点は、現在の `Cascade` の <xref:System.Data.DataSet> プロパティに依存します。  
  
3. **\<エラー >** セクションを処理します。 このセクションの各項目について、指定された行および列のエラー情報を設定します。  
  
> [!NOTE]
> <xref:System.Data.XmlWriteMode> を Diffgram に設定した場合、ターゲット <xref:System.Data.DataSet> の内容が、元の <xref:System.Data.DataSet> の内容と異なる場合があります。  
  
## <a name="diffgram-format"></a>DiffGram 形式  
 DiffGram 形式は、現在のデータ、元のデータ (または前のデータ)、エラーの 3 つのセクションから構成されています。DiffGram の例を次に示します。  
  
```xml  
<?xml version="1.0"?>  
<diffgr:diffgram   
         xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"  
         xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1"  
         xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  
   <DataInstance>  
   </DataInstance>  
  
  <diffgr:before>  
  </diffgr:before>  
  
  <diffgr:errors>  
  </diffgr:errors>  
</diffgr:diffgram>  
```  
  
 DiffGram 形式を構成するデータ ブロックについて次に説明します。  
  
 **\<**  ***DataInstance***  **>**  
 この要素の名前***Datainstance***は、このドキュメントで説明するために使用されます。 ***Datainstance***要素は、 <xref:System.Data.DataSet>またはの<xref:System.Data.DataTable>行を表します。 *Datainstance*の代わりに、要素に<xref:System.Data.DataSet>はまたは<xref:System.Data.DataTable>の名前が含まれます。 DiffGram 形式のこのブロックには現在のデータが含まれています。現在のデータは、変更されている場合と未変更の場合があります。 変更された要素 (行) は、**次**のように変更されます。  
  
 **\<diffgr:before>**  
 DiffGram 形式のこのブロックには、行の元の内容が含まれています。 このブロックの要素は、 **diffgram: id**注釈を使用して***datainstance***ブロック内の要素と一致します。  
  
 **\<diffgr:errors>**  
 DiffGram 形式のこのブロックには、 ***Datainstance***ブロック内の特定の行のエラー情報が含まれています。 このブロックの要素は、 **diffgram: id**注釈を使用して***datainstance***ブロック内の要素と一致します。  
  
## <a name="diffgram-annotations"></a>DiffGram 注釈  
 DiffGram では、<xref:System.Data.DataSet> の行バージョンやエラー情報を表すさまざまな DiffGram ブロックの要素を関連付けるため、いくつかの注釈が使用されます。  
  
 次の表では、DiffGram 名前空間で定義されている DiffGram 注釈**urn:スキーマ-microsoft-com:xml-diffgram-v1**します。  
  
|注釈|説明|  
|----------------|-----------------|  
|**ID**|次のように使用されます。  **\<> する前**に、と **\<** **>**  **\<** の間に、"エラー > は***datainstance***ブロック内の要素に対してブロックします。 RowIdentifier **: id**注釈の値は、 *[TableName] []* という形式になっています。 たとえば、`<Customers diffgr:id="Customers1">` のように指定します。|  
|**parentId**|***Datainstance*** **\<** **ブロック>** のどの要素が現在の要素の親要素であるかを識別します。 RowIdentifier **: parentId**注釈の値は、 *[TableName] []* という形式になっています。 たとえば、`<Orders diffgr:parentId="Customers1">` のように指定します。|  
|**hasChanges**|***Datainstance*** **\<** **ブロック>** 内の行を変更済みとして識別します。 **Haschanges**注釈には、次の2つの値のいずれかを指定できます。<br /><br /> **inserted**<br /> **追加された**行を識別します。<br /><br /> **変更**<br /> は、**変更**された行を識別します。**元**の行バージョンは、> ブロックの **\<前に**ある、次のようにします。 **削除**された行の**元**の行 **\<** **>**  **\<** バージョンは、> ブロックの前であるとしますが、 ***datainstance***ブロックに注釈付きの要素はありません。|  
|**hasErrors**|RowError を使用して **\<** ***datainstance*** **>** ブロック内の行を識別します。 Error 要素は、  **\<">** " ブロックに配置されます。|  
|**Error**|RowError  **\<: errors >** block 内の特定の要素ののテキストを格納します。|  
  
 <xref:System.Data.DataSet> の内容が DiffGram として読み取られる、または書き込まれるときには、上記以外の注釈も含まれます。 次の表に、名前空間で定義されている追加の注釈を**urn:スキーマ-microsoft-com:xml-msdata**します。  
  
|注釈|説明|  
|----------------|-----------------|  
|**RowOrder**|元のデータの行順序を保持し、特定の <xref:System.Data.DataTable> の行のインデックスを識別します。|  
|**[非表示]**|**ColumnMapping**プロパティが**Mappingtype. Hidden**に設定されている列を識別します。 属性は、 **msdata: hidden** *[ColumnName]* = "*value*" という形式で記述されます。 たとえば、`<Customers diffgr:id="Customers1" msdata:hiddenContactTitle="Owner">` のように指定します。<br /><br /> データが格納されている隠し列だけが DiffGram 属性として書き込まれます。 それ以外の場合は無視されます。|  
  
## <a name="sample-diffgram"></a>DiffGram のサンプル  
 DiffGram 形式の例を次に示します。 この例では、変更のコミット前のテーブル内の行に対する更新結果が示されています。 CustomerID の "ALFKI" である行は変更されていますが、更新されていません。 その結果、**現在**の行には、 ***datainstance*** **>** ブロックに **\<** "Customers1" という**id**の "" が含まれています。また 、**元**の行には、  **\<diffgram: >** ブロックの前。 CustomerID が "ANATR" の行には**RowError**が含まれているため、で`diffgr:hasErrors="true"`注釈が付けられ、  **\<: errors >** ブロックに関連する要素があります。  
  
```xml  
<diffgr:diffgram xmlns:msdata="urn:schemas-microsoft-com:xml-msdata" xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
  <CustomerDataSet>  
    <Customers diffgr:id="Customers1" msdata:rowOrder="0" diffgr:hasChanges="modified">  
      <CustomerID>ALFKI</CustomerID>  
      <CompanyName>New Company</CompanyName>  
    </Customers>  
    <Customers diffgr:id="Customers2" msdata:rowOrder="1" diffgram:hasErrors="true">  
      <CustomerID>ANATR</CustomerID>  
      <CompanyName>Ana Trujillo Emparedados y Helados</CompanyName>  
    </Customers>  
    <Customers diffgr:id="Customers3" msdata:rowOrder="2">  
      <CustomerID>ANTON</CustomerID>  
      <CompanyName>Antonio Moreno Taquera</CompanyName>  
    </Customers>  
    <Customers diffgr:id="Customers4" msdata:rowOrder="3">  
      <CustomerID>AROUT</CustomerID>  
      <CompanyName>Around the Horn</CompanyName>  
    </Customers>  
  </CustomerDataSet>  
  <diffgr:before>  
    <Customers diffgr:id="Customers1" msdata:rowOrder="0">  
      <CustomerID>ALFKI</CustomerID>  
      <CompanyName>Alfreds Futterkiste</CompanyName>  
    </Customers>  
  </diffgr:before>  
  <diffgr:errors>  
    <Customers diffgr:id="Customers2" diffgr:Error="An optimistic concurrency violation has occurred for this row."/>  
  </diffgr:errors>  
</diffgr:diffgram>  
```  
  
## <a name="see-also"></a>関連項目

- [DataSet での XML の使用](using-xml-in-a-dataset.md)
- [XML からの DataSet の読み込み](loading-a-dataset-from-xml.md)
- [DataSet 内容の XML データとしての書き込み](writing-dataset-contents-as-xml-data.md)
- [DataSet、DataTable、および DataView](index.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
