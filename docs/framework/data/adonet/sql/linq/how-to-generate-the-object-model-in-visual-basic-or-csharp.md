---
title: '方法: Visual Basic または C# でオブジェクト モデルを生成する'
ms.date: 03/30/2017
ms.assetid: a0c73b33-5650-420c-b9dc-f49310c201ee
ms.openlocfilehash: 8752a28b9bcfd068afcfc5d33c3097f26cf0f231
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59225366"
---
# <a name="how-to-generate-the-object-model-in-visual-basic-or-c"></a>方法: Visual Basic または C# でオブジェクト モデルを生成します。\#
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、使用しているプログラミング言語のオブジェクト モデルが、リレーショナル データベースに対応付けられています。 2 つのツールは Visual Basic を自動的に生成するために使用可能なまたはC#既存のデータベースのメタデータからモデル。  
  
-   Visual Studio を使用している場合を使用できます、[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]オブジェクト モデルを生成します。 [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)]生成するために豊富なユーザー インターフェイスを提供する[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]オブジェクト モデルです。 詳細については、「 [Linq to Visual Studio での SQL ツール](https://docs.microsoft.com/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)します。
  
-   SQLMetal コマンド ライン ツール。 詳しくは、「[SqlMetal.exe (コード生成ツール)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)」をご覧ください。  
  
    > [!NOTE]
    >  既存のデータベースがなく、オブジェクト モデルからデータベースを作成する場合は、コード エディターと <xref:System.Data.Linq.DataContext.CreateDatabase%2A> を使用してオブジェクト モデルを作成できます。 詳細については、「[方法 :データベースを動的に作成](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md)です。  
  
 ドキュメントを[!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)]Visual Basic を生成する方法の例を示しますまたはC#オブジェクト モデルを使用して、[!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)]します。 以下の情報は、SQLMetal コマンド ライン ツールの使用方法の例です。 詳しくは、「[SqlMetal.exe (コード生成ツール)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)」をご覧ください。  
  
## <a name="example"></a>例  
 次の例に示す SQLMetal コマンドラインでは、Northwind サンプル データベースのオブジェクトの属性に基づくモデルとして Visual Basic コードを生成します。 ストアド プロシージャと関数も含まれます。  
  
```  
sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions  
```  
  
## <a name="example"></a>例  
 次の例に示す SQLMetal コマンド ラインでは、Northwind サンプル データベースの属性ベースのオブジェクト モデルとして C# コードが生成されます。 ストアド プロシージャと関数も含まれ、テーブル名は自動的に複数化されます。  
  
```  
sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize  
```  
  
## <a name="see-also"></a>関連項目

- [プログラミング ガイド](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)
- [LINQ to SQL オブジェクト モデル](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [チュートリアルによる学習](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
- [方法: コード エディターを使用してエンティティ クラスをカスタマイズします。](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
- [属性ベースの対応付け](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)
- [SqlMetal.exe (コード生成ツール)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
- [外部マップ](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)
- [サンプル データベースのダウンロード](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
- [オブジェクト モデルの作成](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
