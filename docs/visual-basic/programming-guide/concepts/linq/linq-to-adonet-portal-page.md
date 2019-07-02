---
title: LINQ to ADO.NET (ポータル ページ)
ms.date: 07/20/2015
ms.assetid: bbbd7c76-2981-4b91-b8d2-437547181f52
ms.openlocfilehash: 5783e45f666779e6cfecd611f1e2a34dae5e7df9
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506000"
---
# <a name="linq-to-adonet-portal-page"></a>LINQ to ADO.NET (ポータル ページ)
LINQ to ADO.NET では、ADO.NET での列挙可能なオブジェクトを使用してクエリを実行することができます、[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]プログラミング モデル。  
  
> [!NOTE]
>  LINQ to ADO.NET のドキュメントについては、.NET Framework SDK の ADO.NET のセクションにあります。[LINQ と ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md)。
  
 次の 3 つの別個の ADO.NET[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]テクノロジ。LINQ to DataSet、 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]、および[!INCLUDE[linq_entities](~/includes/linq-entities-md.md)]します。 LINQ to DataSet の提供に対するクエリの実行度で最適化された、 <xref:System.Data.DataSet>、 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] SQL Server データベースのスキーマを直接クエリすることができますと[!INCLUDE[linq_entities](~/includes/linq-entities-md.md)]Entity Data Model のクエリを実行することができます。  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  
 <xref:System.Data.DataSet> は、ADO.NET で最も幅広く使用されているコンポーネントの 1 つであり、ADO.NET の基礎である非接続型プログラミングの重要な要素です。 こうした突出した特長がある反面、<xref:System.Data.DataSet> のクエリ機能には制限もあります。  
  
 LINQ to DataSet に豊富なクエリ機能を構築できます。<xref:System.Data.DataSet>他の多くのデータ ソースに使用される同じクエリ機能を使用します。  
  
 詳細については、「[LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)」を参照してください。  
  
## <a name="linq-to-sql"></a>LINQ to SQL  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] には、リレーショナル データをオブジェクトとして管理するためのランタイム インフラストラクチャが用意されています。 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] では、リレーショナル データベースのデータ モデルが、開発者のプログラミング言語で表されるオブジェクト モデルに対応付けられています。 アプリケーションを実行すると、[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] は、オブジェクト モデルの統合言語クエリを SQL に変換し、それをデータベースに送信して実行します。 データベースから結果が返されると、[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] で元の操作できるオブジェクトに変換されます。  
  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] には、データベースのストアド プロシージャ、ユーザー定義関数、オブジェクト モデルの継承のサポートが含まれています。  
  
 詳細については、「[LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)」を参照してください。  
  
## <a name="linq-to-entities"></a>LINQ to Entities  
 エンティティ データ モデルを通じて、リレーショナル データは、.NET 環境でのオブジェクトとして公開されます。 これにより、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] の利用に最適なオブジェクト レイヤーが実現されます。開発者は、ビジネス ロジックの構築に使用する言語で、データベースを照会するクエリを作成できます。 この機能は、[!INCLUDE[linq_entities](~/includes/linq-entities-md.md)] と呼ばれます。 LINQ の詳細については、「[LINQ to Entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [LINQ と ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md)
- [統合言語クエリ (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)
