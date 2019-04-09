---
title: XML からの DataSet リレーショナル構造の推論
ms.date: 03/30/2017
ms.assetid: cd2f41c6-6785-420e-aa43-3ceb0bdccdce
ms.openlocfilehash: 9a9dc7d94728ea797a8930d3f77068fdd3ebfb5c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59191543"
---
# <a name="inferring-dataset-relational-structure-from-xml"></a>XML からの DataSet リレーショナル構造の推論
<xref:System.Data.DataSet> のリレーショナル構造 (スキーマ) は、テーブル、列、制約、およびリレーションで構成されます。 XML から <xref:System.Data.DataSet> を読み込むときには、事前定義されたスキーマを使用するか、または読み込む対象の XML から明示的にまたは推論によってスキーマを作成できます。 スキーマとのコンテンツの読み込みの詳細については、 <xref:System.Data.DataSet> 、XML から次を参照してください。 [XML からの DataSet の読み込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)と[XML からの DataSet スキーマ情報の読み込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)します。  
  
 場合のスキーマを<xref:System.Data.DataSet>が作成されているか、XML スキーマ定義言語 (XSD) を使用してスキーマを明示的に指定する、XML から推奨される方法は、(」の説明に従って[派生の DataSet リレーショナル構造から XML スキーマ (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md))、Xml-data Reduced (XDR) またはします。 XML で利用できる XML スキーマまたは XDR スキーマがない場合は、XML の要素および属性の構造から <xref:System.Data.DataSet> のスキーマを推論できます。  
  
 ここでは、XML の要素と属性およびその構造を示し、<xref:System.Data.DataSet> スキーマの推論に関する規則について説明します。また、その規則に基づいて推論した <xref:System.Data.DataSet> スキーマも示します。  
  
 XML ドキュメント内のすべての属性を推論プロセスの対象には含めないでください。 名前空間で修飾された属性には、XML ドキュメントにとっては重要ですが、<xref:System.Data.DataSet> スキーマにとっては不要なメタデータが含まれていることがあります。 <xref:System.Data.DataSet.InferXmlSchema%2A> を使用して、推論プロセスの間に無視する特定の名前空間を指定できます。 詳細については、次を参照してください。 [XML からの DataSet スキーマ情報の読み込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [DataSet スキーマの推論プロセスの概要](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/summary-of-the-dataset-schema-inference-process.md)  
 XML から <xref:System.Data.DataSet> のスキーマを推論するときの規則について概要を示します。  
  
 [テーブルの推論](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-tables.md)  
 <xref:System.Data.DataSet> のテーブルとして推論される XML の要素について説明します。  
  
 [列の推論](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-columns.md)  
 テーブルの列として推論される XML の要素と属性について説明します。  
  
 [リレーションシップの推論](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-relationships.md)  
 推論された入れ子状のテーブルに対して作成される <xref:System.Data.DataRelation> オブジェクトおよび <xref:System.Data.ForeignKeyConstraint> オブジェクトについて説明します。  
  
 [要素のテキストの推論](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-element-text.md)  
 XML 要素のテキストに対して作成される列について、および XML 要素のテキストが無視される場合について説明します。  
  
 [推論の制限事項](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inference-limitations.md)  
 スキーマ推論の制限事項について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [DataSet での XML の使用](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 <xref:System.Data.DataSet> オブジェクトと XML データとの対話について説明します。  
  
 [XML スキーマ (XSD) からの DataSet リレーショナル構造の派生](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 XML スキーマ定義言語 (XSD) スキーマから作成された <xref:System.Data.DataSet> のリレーショナル構造 (スキーマ) について説明します。  
  
 [ADO.NET の概要](../../../../../docs/framework/data/adonet/ado-net-overview.md)  
 ADO.NET のアーキテクチャとコンポーネントについて、また ADO.NET を使用して既存のデータ ソースにアクセスしたり、アプリケーション データを管理する方法について説明します。  
  
## <a name="see-also"></a>関連項目

- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
