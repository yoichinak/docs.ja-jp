---
title: Parallel LINQ (PLINQ)
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- PLINQ, overview
ms.assetid: 3d4d0cd3-bde4-490b-99e7-f4e41be96455
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c438170ec48f40e59f8710d4e3820d6e915bed5
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2019
ms.locfileid: "55903833"
---
# <a name="parallel-linq-plinq"></a>Parallel LINQ (PLINQ)
Parallel LINQ (PLINQ) は、LINQ to Objects の並列実装です。 PLINQ は、LINQ 標準クエリ演算子の完全なセットを <xref:System.Linq> 名前空間の拡張メソッドとして実装し、並列操作用の追加演算子も備えています。 PLINQ は、LINQ 構文の単純さと読みやすさに加え、並列プログラミングのパワーを兼ね備えています。 タスク並列ライブラリを対象とするコードと同じように、PLINQ クエリのコンカレンシーの程度は、ホスト コンピューターの能力に基づいて調整されます。  
  
 多くのシナリオで、PLINQ は、ホスト コンピューターで使用可能なすべてのコアをより効率的に使用することで、LINQ to Objects クエリの速度を大幅に上昇させることができます。 このパフォーマンスの向上によって、デスクトップに高パフォーマンスの演算能力がもたらされます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [PLINQ の概要](../../../docs/standard/parallel-programming/introduction-to-plinq.md)  
  
 [PLINQ での高速化について](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)  
  
 [PLINQ における順序維持](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md)  
  
 [PLINQ のマージ オプション](../../../docs/standard/parallel-programming/merge-options-in-plinq.md)  
  
 [方法: 単純な PLINQ クエリを作成して実行する](../../../docs/standard/parallel-programming/how-to-create-and-execute-a-simple-plinq-query.md)  
  
 [方法: PLINQ クエリの順序を制御する](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md)  
  
 [方法: 並列および順次の LINQ クエリを連結する](../../../docs/standard/parallel-programming/how-to-combine-parallel-and-sequential-linq-queries.md)  
  
 [方法: PLINQ クエリの例外を処理する](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md)  
  
 [方法: PLINQ クエリを取り消す](../../../docs/standard/parallel-programming/how-to-cancel-a-plinq-query.md)  
  
 [方法: カスタムの PLINQ 集約関数を記述する](../../../docs/standard/parallel-programming/how-to-write-a-custom-plinq-aggregate-function.md)  
  
 [方法: PLINQ の実行モードを指定する](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md)  
  
 [方法: PLINQ のマージ オプションを指定する](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)  
  
 [方法: PLINQ を使用してファイル ディレクトリを反復処理する](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-plinq.md)  
  
 [方法: PLINQ クエリのパフォーマンスを測定する](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md)  
  
 [PLINQ データのサンプル](../../../docs/standard/parallel-programming/plinq-data-sample.md)  
  
## <a name="see-also"></a>関連項目

- <xref:System.Linq.ParallelEnumerable>
- [並列プログラミング](../../../docs/standard/parallel-programming/index.md)
- [統合言語クエリ (LINQ) - C#](../../csharp/programming-guide/concepts/linq/index.md)  
- [統合言語クエリ (LINQ) - Visual Basic](../../visual-basic/programming-guide/concepts/linq/index.md)  
