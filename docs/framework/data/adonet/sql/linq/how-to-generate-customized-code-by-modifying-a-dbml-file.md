---
title: '方法: DBML ファイルを変更してカスタマイズ コードを生成する'
ms.date: 03/30/2017
ms.assetid: 50ad597a-8598-42d3-82dd-fc7d702ebc37
ms.openlocfilehash: 01890e6b899db6b70049e2d6b8193e5b0f4095fb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781986"
---
# <a name="how-to-generate-customized-code-by-modifying-a-dbml-file"></a>方法: DBML ファイルを変更してカスタマイズ コードを生成する
Visual Basic またはC#ソースコードは、データベースマークアップ言語 (.dbml) メタデータファイルから生成できます。 この方法を使用すると、アプリケーション マッピング コードを生成する前に、既定の .dbml ファイルをカスタマイズできます。 これは高度な機能です。  
  
 実行手順は次のとおりです。  
  
1. .dbml ファイルを生成します。  
  
2. エディターを使用して .dbml ファイルを変更します。 .Dbml ファイルは、.dbml ファイルの[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]スキーマ定義 (.xsd) ファイルに対して検証する必要があることに注意してください。 詳細については、「 [LINQ to SQL でのコード生成](code-generation-in-linq-to-sql.md)」を参照してください。  
  
3. Visual Basic またはC#ソースコードを生成します。  
  
 次の例では、SQLMetal コマンド ライン ツールを使用します。 詳しくは、「[SqlMetal.exe (コード生成ツール)](../../../../tools/sqlmetal-exe-code-generation-tool.md)」をご覧ください。  
  
## <a name="example"></a>例  
 次のコードでは、Northwind サンプル データベースから .dbml ファイルを生成します。 データベース メタデータのソースとして、データベースの名前または .mdf ファイルの名前を使用します。  
  
```  
sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml  
sqlmetal /dbml:mymeta.dbml mydbfile.mdf  
```  
  
## <a name="example"></a>例  
 次のコードでは、 C# .dbml ファイルから Visual Basic またはソースコードファイルが生成されます。  
  
```  
sqlmetal /namespace:nwind /code:nwind.vb /language:vb DBMLFile.dbml  
sqlmetal /namespace:nwind /code:nwind.cs /language:csharp DBMLFile.dbml  
```  
  
## <a name="see-also"></a>関連項目

- [LINQ to SQL でのコード生成](code-generation-in-linq-to-sql.md)
- [SqlMetal.exe (コード生成ツール)](../../../../tools/sqlmetal-exe-code-generation-tool.md)
- [オブジェクト モデルの作成](creating-the-object-model.md)
