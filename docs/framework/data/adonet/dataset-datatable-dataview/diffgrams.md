---
title: DiffGrams
ms.date: 03/30/2017
ms.assetid: 037f3991-7bbc-424b-b52e-8b03585d3e34
ms.openlocfilehash: 2c521ef33c98234dac5f4b819a800cd524218462
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151157"
---
# <a name="diffgrams"></a>DiffGrams
DiffGram は、データ要素の現在のバージョンと元のバージョンを識別する XML 形式です。  では、 の内容を読み込んで永続化するため、およびネットワーク接続経由で転送する場合にこの内容をシリアル化するために、DiffGram 形式が使用されます。 DiffGram<xref:System.Data.DataSet>として書き込まれると、**元**の行バージョンと**現在**の行バージョンの列値、行エラー情報、および行の順序を含め<xref:System.Data.DataSet>、 の内容を正確に再作成するために必要なすべての情報が DiffGram に設定されます。  
  
 XML Web サービスから <xref:System.Data.DataSet> を送信または取得するときには、DiffGram 形式が暗黙的に使用されます。 また **、ReadXml**メソッドを使用して<xref:System.Data.DataSet>XML からコンテンツを読み込む場合、または**WriteXml**メソッドを<xref:System.Data.DataSet>使用して XML の内容を書き込むときに、内容を DiffGram として読み取りまたは書き込むことを指定できます。 詳細については、「 [XML からのデータセットの読み込み](loading-a-dataset-from-xml.md)」および「 XML[データとしてのデータセットの内容の書き込み](writing-dataset-contents-as-xml-data.md)」を参照してください。  
  
 .NET Framework では、DiffGram 形式は主に <xref:System.Data.DataSet> の内容をシリアル化するときの形式として使用されますが、Microsoft SQL Server データベース内のテーブル データを変更するときにも DiffGrams を使用できます。  
  
 Diffgram は、すべてのテーブルの内容を**\<diffgram>** 要素に書き込むと生成されます。  
  
### <a name="to-generate-a-diffgram"></a>Diffgram を生成するには  
  
1. ルート テーブル (親を一切持たないテーブル) のリストを生成します。  
  
2. リストの各テーブルとその子孫について、すべての行の現在のバージョンを最初の Diffgram セクションに書き込みます。  
  
3. <xref:System.Data.DataSet>の各テーブルに対して、すべての行の元のバージョン (存在する場合) を Diffgram の**\<前>** セクションに書き出します。  
  
4. エラーがある行の場合は、エラーの内容を Diffgram の**\<エラー>** セクションに書き込みます。  
  
 Diffgram は XML ファイルの上から下に向かって処理されます。  
  
### <a name="to-process-a-diffgram"></a>Diffgram を処理するには  
  
1. Diffgram の最初のセクションを処理します。このセクションには、行の現在のバージョンが格納されています。  
  
2. 変更された行と削除**\<** された行の元の行バージョンを含む 2 番目または前のセクション>処理します。  
  
    > [!NOTE]
    > 行が削除済みとしてマークされていた場合、削除操作によってその行の子孫も削除される場合があります。この点は、現在の `Cascade` の <xref:System.Data.DataSet> プロパティに依存します。  
  
3. セクションの**\<エラー>** 処理します。 このセクションの各項目について、指定された行および列のエラー情報を設定します。  
  
> [!NOTE]
> <xref:System.Data.XmlWriteMode> を Diffgram に設定した場合、ターゲット <xref:System.Data.DataSet> の内容が、元の <xref:System.Data.DataSet> の内容と異なる場合があります。  
  
## <a name="diffgram-format"></a>DiffGram の書式  
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
  
 **\<**  ***データインスタンス***  **>**  
 この要素の名前***DataInstance***は、このドキュメントで説明するために使用されます。 要素***は***、<xref:System.Data.DataSet>または の行を<xref:System.Data.DataTable>表します。 要素には *、 または*の名前<xref:System.Data.DataSet>が含まれます<xref:System.Data.DataTable>。 DiffGram 形式のこのブロックには現在のデータが含まれています。現在のデータは、変更されている場合と未変更の場合があります。 変更された要素または行は **、diffgr:hasChanges**アノテーションで識別されます。  
  
 **\<diffgr:>する前に**  
 DiffGram 形式のこのブロックには、行の元の内容が含まれています。 このブロック内の要素は **、diffgr:id**注釈を使用して***DataInstance***ブロック内の要素と照合されます。  
  
 **\<diffgr:エラー>**  
 DiffGram 形式のこのブロックには ***、DataInstance***ブロック内の特定の行のエラー情報が含まれています。 このブロック内の要素は **、diffgr:id**注釈を使用して***DataInstance***ブロック内の要素と照合されます。  
  
## <a name="diffgram-annotations"></a>DiffGram の注釈  
 DiffGram では、<xref:System.Data.DataSet> の行バージョンやエラー情報を表すさまざまな DiffGram ブロックの要素を関連付けるため、いくつかの注釈が使用されます。  
  
 次の表に、DiffGram 名前空間**urn:schemas-microsoft-com:xml-diffgram-v1**で定義されている DiffGram 注釈について説明します。  
  
|Annotation|説明|  
|----------------|-----------------|  
|**id**|**\<** **>** **diffgr:before>と diffgr:errors>ブロック内の要素を DataInstance ブロック内の要素にペアに\<** するのに使用されます。 ** \<** ***DataInstance*** **diffgr:id**アノテーションを持つ値は *、[テーブル名][RowIdentifier]* という形式です。 例: `<Customers diffgr:id="Customers1">`。|  
|**Parentid**|現在の要素の**\<** 親要素である***DataInstance*****>** ブロックの要素を識別します。 **diffgr:parentId**アノテーションを持つ値は *、[テーブル名][行識別子]* という形式です。 例: `<Orders diffgr:parentId="Customers1">`。|  
|**hasChanges**|**\<** ***DataInstance*****>** ブロック内の行を変更済みとして識別します。 **hasChanges**アノテーションには、次の 2 つの値のいずれかを指定できます。<br /><br /> **挿入**<br /> **追加された**行を識別します。<br /><br /> **変更**<br /> ** \<diffgr: before**ブロック内の**オリジナル**行バージョンを含む**変更された**行>識別します。 **削除された**行は**\<diffgr: before>** ブロックに**オリジナル**行バージョンを持ちますが ***、DataInstance*****>** ブロックには**\<** 注釈付き要素はありません。|  
|**hasErrors**|**\<*****データ インスタンス*****>** ブロック内の行を **、行エラー**で識別します。 エラー要素は**\<diffgr:errors>** ブロックに配置されます。|  
|**エラー**|** \<diffgr:errors>** ブロック内の特定の要素の**RowError**のテキストが含まれています。|  
  
 <xref:System.Data.DataSet> の内容が DiffGram として読み取られる、または書き込まれるときには、上記以外の注釈も含まれます。 次の表に、名前空間 urn で定義されているこれらの追加の注釈について**説明します。**  
  
|Annotation|説明|  
|----------------|-----------------|  
|**RowOrder**|元のデータの行順序を保持し、特定の <xref:System.Data.DataTable> の行のインデックスを識別します。|  
|**[非表示]**|列マッピング**プロパティが** **MappingType.Hidden**に設定されていると識別します。 属性は **、msdata:hidden** *[列名]*="*値*"の形式で書き込まれます。 例: `<Customers diffgr:id="Customers1" msdata:hiddenContactTitle="Owner">`。<br /><br /> データが格納されている隠し列だけが DiffGram 属性として書き込まれます。 それ以外の場合は、無視されます。|  
  
## <a name="sample-diffgram"></a>DiffGram のサンプル  
 DiffGram 形式の例を次に示します。 この例では、変更のコミット前のテーブル内の行に対する更新結果が示されています。 CustomerID の "ALFKI" である行は変更されていますが、更新されていません。 その結果 ***、DataInstance*****>** ブロック内に 「Customers1」 の**diffgr:id** **\<** を持つ**現在**の行と**\<、diffgr:in diffgr: 前の>** ブロックに "Customers1" の**diffgr:id**を持つ**元**の行があります。 "ANATR" の CustomerID を持つ行には**RowError**が含まれるため、`diffgr:hasErrors="true"`この行にはアノテーションが付けられており**\<、diffgr:errors>** ブロックに関連する要素があります。  
  
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
- [ADO.NET の概要](../ado-net-overview.md)
