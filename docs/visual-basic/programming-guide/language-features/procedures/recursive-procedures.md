---
title: 再帰プロシージャ (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], that call themselves
- procedures [Visual Basic], recursive
- procedures [Visual Basic], calling
- recursive procedures
- functions [Visual Basic], calling recursively
- recursion
ms.assetid: ba1d3962-b4c3-48d3-875e-96fdb4198327
ms.openlocfilehash: de9a2af9fc3cd78879b6525245727a6f52d51c63
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832386"
---
# <a name="recursive-procedures-visual-basic"></a>再帰プロシージャ (Visual Basic)
A*再帰*手順は、自分自身を呼び出します。 通常、これは Visual Basic コードを記述する最も効果的な方法ではありません。  
  
 次の手順では、元の引数の階乗を計算するのに再帰を使用します。  
  
 [!code-vb[VbVbcnProcedures#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#51)]  
  
## <a name="considerations-with-recursive-procedures"></a>再帰プロシージャに関する考慮事項  
 **制限条件**します。 再帰処理を終了するには少なくとも 1 つの条件をテストする再帰的な手順を設計する必要があり、妥当な数の再帰呼び出し内でこのような条件が満たされていないケースを処理することも必要があります。 失敗せずに満たすことが少なくとも 1 つの条件がない、プロシージャを実行する可能性が高く無限ループで実行します。  
  
 **メモリ使用状況**。 アプリケーションが、ローカル変数の領域量が制限されています。 プロシージャが、それ自体を呼び出すたびに、ローカル変数の追加のコピーの領域を使用します。 最終的と、このプロセスが無期限に解決しない場合は、<xref:System.StackOverflowException>エラー。  
  
 **効率**します。 ほとんどの場合に、再帰はループを置き換えることができます。 ループでは、引数の受け渡し、追加のストレージを初期化し、値を返すのオーバーヘッドはありません。 パフォーマンスは、再帰的な呼び出しなしの方があります。  
  
 **相互再帰**します。 2 つの手順では、互いを呼び出す場合、パフォーマンスが大きく低下、または、無限ループでもを確認する場合があります。 このような設計は、1 つの再帰プロシージャと同じ問題を提示しますが、検出およびデバッグが困難になることができます。  
  
 **かっこで囲んで呼び出す**します。 ときに、`Function`プロシージャを呼び出す再帰的に、引数リストがない場合でも、プロシージャ名、かっこを従う必要があります。 関数名を取得する場合は、関数の戻り値を表すとします。  
  
 **テスト**します。 再帰プロシージャを記述する場合はいくつかの制限の条件を満たしているかどうかを確認する非常に慎重にテストする必要があります。 再帰の呼び出しが多すぎるため、メモリ不足が実行できないということを確認する必要があります。  
  
## <a name="see-also"></a>関連項目

- <xref:System.StackOverflowException>
- [プロシージャ](./index.md)
- [Sub プロシージャ](./sub-procedures.md)
- [Function プロシージャ](./function-procedures.md)
- [Property プロシージャ](./property-procedures.md)
- [演算子プロシージャ](./operator-procedures.md)
- [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)
- [プロシージャのオーバーロード](./procedure-overloading.md)
- [プロシージャのトラブルシューティング](./troubleshooting-procedures.md)
- [ループ構造](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
