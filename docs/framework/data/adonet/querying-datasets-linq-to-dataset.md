---
title: DataSet のクエリ (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
ms.openlocfilehash: 79a9b320fbdbfecc3f7d531d992b1529873871a5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783052"
---
# <a name="querying-datasets-linq-to-dataset"></a>DataSet のクエリ (LINQ to DataSet)
<xref:System.Data.DataSet> オブジェクトへのデータの読み込みが完了すると、そのデータセットに対してクエリを実行できるようになります。 LINQ to DataSet を使用したクエリの設定[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)]は、 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]他の対応データソースに対してを使用する場合と似ています。 ただし、オブジェクトに[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] <xref:System.Data.DataSet>対してクエリを使用する場合は、カスタム型の列挙型<xref:System.Data.DataRow>ではなく、オブジェクトの列挙型にクエリを実行することに注意してください。 これは、 <xref:System.Data.DataRow> [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]クエリでクラスの任意のメンバーを使用できることを意味します。 これにより、高度で複雑なクエリの作成が可能となります。  
  
 の他の実装と[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]同様に、クエリ式の構文とメソッドベースのクエリ構文という2つの異なる形式で LINQ to DataSet のクエリを作成できます。 クエリ式の構文またはメソッド ベースのクエリ構文を使用して、<xref:System.Data.DataSet> 内の単一テーブル、<xref:System.Data.DataSet> 内の複数テーブル、または、型指定された <xref:System.Data.DataSet> 内のテーブルを対象にクエリを実行できます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [単一テーブルのクエリ](single-table-queries-linq-to-dataset.md)  
 単一テーブルのクエリを実行する方法について説明します。  
  
 [複数テーブルにまたがるクエリ](cross-table-queries-linq-to-dataset.md)  
 複数テーブルにまたがるクエリを実行する方法について説明します。  
  
 [型指定された DataSet のクエリ](querying-typed-datasets.md)  
 型指定された <xref:System.Data.DataSet> オブジェクトに対してクエリを実行する方法について説明します。  
  
## <a name="see-also"></a>関連項目

- [LINQ to DataSet の例](linq-to-dataset-examples.md)
- [DataSet へのデータの読み込み](loading-data-into-a-dataset.md)
