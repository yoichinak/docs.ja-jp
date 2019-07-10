---
title: ストアド プロシージャによる操作のカスタマイズ
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: aedbecc1-c33c-4fb4-8861-fdf7e1dc6b8a
ms.openlocfilehash: d9f8d15b46f6e5575bd206bf572ffda0365e58f6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743554"
---
# <a name="customizing-operations-by-using-stored-procedures"></a>ストアド プロシージャによる操作のカスタマイズ
ストアド プロシージャは、既定の動作をオーバーライドする方法として一般的に使用されます。 このトピックでは、ストアド プロシージャ用に生成されたメソッド ラッパーを使用する方法、およびストアド プロシージャを直接呼び出す方法の例を示します。  
  
 Visual Studio を使用している場合は、挿入、更新、および削除を実行するストアド プロシージャを割り当てるオブジェクト リレーショナル デザイナーを使用できます。  
  
> [!NOTE]
>  データベースによって生成された値を読み取るには、ストアド プロシージャの出力パラメーターを使用します。 出力パラメーターを使用できない場合記述ではなく、部分メソッドの実装をオーバーライド オブジェクト リレーショナル デザイナーによって生成されました。 データベースによって生成される値に割り当てられているメンバーは、`INSERT` 操作または `UPDATE` 操作が正常に完了した後で、適切な値に設定する必要があります。 詳細については、次を参照してください。[開発者でオーバーライドする既定の動作の責任](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)します。  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 次の例では、`Northwind` クラスに、ストアド プロシージャを呼び出す 2 つのメソッドがあり、派生クラスでのオーバーライドに使用されているものとします。  
  
### <a name="code"></a>コード  
 [!code-csharp[DLinqOverrideDefaultSproc#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#1)]
 [!code-vb[DLinqOverrideDefaultSproc#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#1)]  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 次のクラスはこれらのメソッドをオーバーライドに使用しています。  
  
### <a name="code"></a>コード  
 [!code-csharp[DLinqOverrideDefaultSproc#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#2)]
 [!code-vb[DLinqOverrideDefaultSproc#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#2)]  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 `NorthwindThroughSprocs` は `Northwnd` とまったく同様に使用できます。  
  
### <a name="code"></a>コード  
 [!code-csharp[DLinqOverrideDefaultSproc#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/Program.cs#3)]
 [!code-vb[DLinqOverrideDefaultSproc#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>関連項目

- [既定の動作をオーバーライドするときの開発者の責任](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)
