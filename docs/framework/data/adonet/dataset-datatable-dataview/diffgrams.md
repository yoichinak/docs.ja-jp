---
title: DiffGrams
ms.date: 03/30/2017
ms.assetid: 037f3991-7bbc-424b-b52e-8b03585d3e34
ms.openlocfilehash: 048c5331028bbe2bb232302637dbb12bcdd2adc3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61607814"
---
# <a name="diffgrams"></a>DiffGrams
DiffGram は、データ要素の現在のバージョンと元のバージョンを識別する XML 形式です。 <xref:System.Data.DataSet> では、 の内容を読み込んで永続化するため、およびネットワーク接続経由で転送する場合にこの内容をシリアル化するために、DiffGram 形式が使用されます。 ときに、<xref:System.Data.DataSet>正確に再作成する内容は、ただし、スキーマの DiffGram に必要なすべての情報を格納しますが、DiffGram として書き込まれますが、 <xref:System.Data.DataSet>、両方の列の値を含む、**元**と**現在**行のバージョン、行エラー情報、および行の順序。  
  
 XML Web サービスから <xref:System.Data.DataSet> を送信または取得するときには、DiffGram 形式が暗黙的に使用されます。 さらの内容を読み込むときに、<xref:System.Data.DataSet>から XML を使用して、 **ReadXml**メソッドの内容を記述する場合、または、 <xref:System.Data.DataSet> XML を使用して、 **WriteXml**メソッドを指定できます内容の読み取りがまたはを DiffGram として書き込みます。 詳細については、次を参照してください。 [XML からの DataSet の読み込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)と[書き込み DataSet の内容を XML データとして](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)します。  
  
 .NET Framework では、DiffGram 形式は主に <xref:System.Data.DataSet> の内容をシリアル化するときの形式として使用されますが、Microsoft SQL Server データベース内のテーブル データを変更するときにも DiffGrams を使用できます。  
  
 Diffgram は、すべてのテーブルの内容の書き込みによって生成される、  **\<diffgram >** 要素。  
  
### <a name="to-generate-a-diffgram"></a>Diffgram を生成するには  
  
1. ルート テーブル (親を一切持たないテーブル) のリストを生成します。  
  
2. リストの各テーブルとその子孫について、すべての行の現在のバージョンを最初の Diffgram セクションに書き込みます。  
  
3. 各テーブルに対して、 <xref:System.Data.DataSet>、存在する場合に、すべての行の元のバージョンを書き出すの**\<する前に >** Diffgram のセクション。  
  
4. 、エラーが発生した行の書き込みエラーの内容について、 **\<エラー >** 、Diffgram のセクション。  
  
 Diffgram は XML ファイルの上から下に向かって処理されます。  
  
### <a name="to-process-a-diffgram"></a>Diffgram を処理するには  
  
1. Diffgram の最初のセクションを処理します。このセクションには、行の現在のバージョンが格納されています。  
  
2. 2 つ目の処理、または**\<する前に >** の元の行バージョンが含まれるセクションは変更または削除された行。  
  
    > [!NOTE]
    >  行が削除済みとしてマークされていた場合、削除操作によってその行の子孫も削除される場合があります。この点は、現在の `Cascade` の <xref:System.Data.DataSet> プロパティに依存します。  
  
3. プロセス、 **\<エラー >** セクション。 このセクションの各項目について、指定された行および列のエラー情報を設定します。  
  
> [!NOTE]
>  <xref:System.Data.XmlWriteMode> を Diffgram に設定した場合、ターゲット <xref:System.Data.DataSet> の内容が、元の <xref:System.Data.DataSet> の内容と異なる場合があります。  
  
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
 この要素の名前***DataInstance***はこのドキュメントでは説明目的で使用します。 A ***DataInstance***要素を表す、<xref:System.Data.DataSet>または行の<xref:System.Data.DataTable>します。 代わりに*DataInstance*、要素の名前には、<xref:System.Data.DataSet>または<xref:System.Data.DataTable>します。 DiffGram 形式のこのブロックには現在のデータが含まれています。現在のデータは、変更されている場合と未変更の場合があります。 要素、または変更された行がで識別される、 **diffgr:hasChanges**注釈。  
  
 **\<diffgr:before>**  
 DiffGram 形式のこのブロックには、行の元の内容が含まれています。 このブロック内の要素が要素に一致する、 ***DataInstance***ブロックを使用して、 **diffgr:id**注釈。  
  
 **\<diffgr:errors>**  
 DiffGram 形式のこのブロックには、特定の行のエラー情報が含まれています、 ***DataInstance***ブロックします。 このブロック内の要素が要素に一致する、 ***DataInstance***ブロックを使用して、 **diffgr:id**注釈。  
  
## <a name="diffgram-annotations"></a>DiffGram 注釈  
 DiffGram では、<xref:System.Data.DataSet> の行バージョンやエラー情報を表すさまざまな DiffGram ブロックの要素を関連付けるため、いくつかの注釈が使用されます。  
  
 次の表では、DiffGram 名前空間で定義されている DiffGram 注釈**urn:スキーマ-microsoft-com:xml-diffgram-v1**します。  
  
|注釈|説明|  
|----------------|-----------------|  
|**ID**|要素と対応するために使用、  **\<diffgr: する前に >** と **\<diffgr:errors >** ブロックの要素、 **\<*****DataInstance*** **>** ブロックします。 値で、 **diffgr:id**注釈は、形式 *[TableName] [RowIdentifier]* します。 たとえば、`<Customers diffgr:id="Customers1">` のように指定します。|  
|**parentId**|要素を識別する、 **\<** ***DataInstance*** **>** ブロックは、現在の要素の親要素。 値で、 **diffgr:parentId**注釈は、形式 *[TableName] [RowIdentifier]* します。 たとえば、`<Orders diffgr:parentId="Customers1">` のように指定します。|  
|**hasChanges**|行を識別、 **\<** ***DataInstance*** **>** 変更とブロックされます。 **HasChanges**注釈は、次の 2 つの値のいずれかを指定できます。<br /><br /> **inserted**<br /> 識別、 **Added**行。<br /><br /> **変更**<br /> 識別、 **Modified**を含む行を**元**で行のバージョン、  **\<diffgr: する前に >** ブロック。 注意**Deleted**の行、**元**で行のバージョン、  **\<diffgr: する前に >** ブロックが、注釈付き要素、ことはできません**\<**  ***DataInstance*** **>** ブロックします。|  
|**hasErrors**|行を識別、 **\<** ***DataInstance*** **>** ブロックと一緒に、 **RowError**します。 エラー要素は内に、  **\<diffgr:errors >** ブロックします。|  
|**Error**|テキストを含む、 **RowError**で特定の要素に対して、  **\<diffgr:errors >** ブロックします。|  
  
 <xref:System.Data.DataSet> の内容が DiffGram として読み取られる、または書き込まれるときには、上記以外の注釈も含まれます。 次の表に、名前空間で定義されている追加の注釈を**urn:スキーマ-microsoft-com:xml-msdata**します。  
  
|注釈|説明|  
|----------------|-----------------|  
|**RowOrder**|元のデータの行順序を保持し、特定の <xref:System.Data.DataTable> の行のインデックスを識別します。|  
|**[非表示]**|列として識別する、 **ColumnMapping**プロパティに設定**MappingType.Hidden**します。 属性が形式で記述された**msdata: 非表示** *[ColumnName]*="*値*"。 たとえば、`<Customers diffgr:id="Customers1" msdata:hiddenContactTitle="Owner">` のように指定します。<br /><br /> データが格納されている隠し列だけが DiffGram 属性として書き込まれます。 それ以外の場合は無視されます。|  
  
## <a name="sample-diffgram"></a>DiffGram のサンプル  
 DiffGram 形式の例を次に示します。 この例では、変更のコミット前のテーブル内の行に対する更新結果が示されています。 CustomerID の "ALFKI" である行は変更されていますが、更新されていません。 その結果は、**現在**で行の**diffgr:id** "Customers1"の**\<** ***DataInstance*** **>** ブロック、および**元**で行の**diffgr:id** "Customers1"の **\<diffgr: する前に >** ブロックします。 Customerid が"ANATR"の行が含まれています、 **RowError**で注釈が付けられるため、`diffgr:hasErrors="true"`関連する要素があると、  **\<diffgr:errors >** ブロックします。  
  
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

- [DataSet での XML の使用](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [XML からの DataSet の読み込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [DataSet 内容の XML データとしての書き込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)
- [DataSet、DataTable、および DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
