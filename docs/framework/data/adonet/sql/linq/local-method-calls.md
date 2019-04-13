---
title: ローカル メソッド呼び出し
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34b5012-aee9-4994-9364-1d99d12b7463
ms.openlocfilehash: c8a4c29b1faa3c05f2cf32e9a60104b43a9b1c40
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074548"
---
# <a name="local-method-calls"></a>ローカル メソッド呼び出し
ローカル メソッド呼び出しとは、オブジェクト モデル内で実行される呼び出しです。 リモート メソッド呼び出しとは、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] が SQL に変換し、データベース エンジンに送信して実行される呼び出しです。 ローカル メソッド呼び出しが必要なときに[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]SQL への呼び出しを変換することはできません。 それ以外の場合は、<xref:System.InvalidOperationException> がスローされます。  
  
## <a name="example-1"></a>例 1  
 次の例では、`Order` クラスは Northwind サンプル データベースの Orders テーブルに割り当てられています。 このクラスには、ローカル インスタンス メソッドが追加されています。  
  
 クエリ 1 では、`Order` クラスのコンストラクターがローカルで実行されます。 クエリ 2 では、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] が `LocalInstanceMethod()` を SQL に変換しようとすると、処理は失敗し、<xref:System.InvalidOperationException> 例外がスローされるはずです。 しかし、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ではローカル メソッド呼び出しがサポートされているため、クエリ 2 で例外はスローされません。  
  
 [!code-csharp[DlinqLocalMethodCall#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/Program.cs#1)]
 [!code-vb[DlinqLocalMethodCall#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/Module1.vb#1)]  
  
 [!code-csharp[DlinqLocalMethodCall#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/northwind.cs#2)]
 [!code-vb[DlinqLocalMethodCall#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/northwind.vb#2)]  
  
## <a name="see-also"></a>関連項目

- [背景情報](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
