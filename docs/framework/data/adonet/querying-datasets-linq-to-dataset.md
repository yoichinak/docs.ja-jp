---
title: DataSet のクエリ (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
ms.openlocfilehash: ec4ee345835294499f7ac9f665a9b79e2efc0f64
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504657"
---
# <a name="querying-datasets-linq-to-dataset"></a>DataSet のクエリ (LINQ to DataSet)
<xref:System.Data.DataSet> オブジェクトへのデータの読み込みが完了すると、そのデータセットに対してクエリを実行できるようになります。 使用するような LINQ to DataSet のクエリの作成は[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)]に対して他[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]-データ ソースを有効にします。 ただしを使用すると[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]クエリを実行、<xref:System.Data.DataSet>オブジェクトの列挙クエリを実行する<xref:System.Data.DataRow>カスタム型の列挙体ではなく、オブジェクト。 つまりのメンバーのいずれかを使用できます、<xref:System.Data.DataRow>クラス、[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]クエリ。 これにより、高度で複雑なクエリの作成が可能となります。  
  
 他の実装と同様[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]LINQ を作成するには 2 つの異なる形式でデータセット クエリ: クエリ式の構文とメソッド ベースのクエリ構文。 クエリ式の構文またはメソッド ベースのクエリ構文を使用して、<xref:System.Data.DataSet> 内の単一テーブル、<xref:System.Data.DataSet> 内の複数テーブル、または、型指定された <xref:System.Data.DataSet> 内のテーブルを対象にクエリを実行できます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [単一テーブルのクエリ](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)  
 単一テーブルのクエリを実行する方法について説明します。  
  
 [複数テーブルにまたがるクエリ](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)  
 複数テーブルにまたがるクエリを実行する方法について説明します。  
  
 [型指定された DataSet のクエリ](../../../../docs/framework/data/adonet/querying-typed-datasets.md)  
 型指定された <xref:System.Data.DataSet> オブジェクトに対してクエリを実行する方法について説明します。  
  
## <a name="see-also"></a>関連項目

- [LINQ to DataSet の例](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
- [DataSet へのデータの読み込み](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
