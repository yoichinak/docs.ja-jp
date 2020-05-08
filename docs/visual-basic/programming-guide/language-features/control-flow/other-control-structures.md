---
title: その他の制御構造
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures [Visual Basic]
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
ms.openlocfilehash: 758df361f421684655147ae288af3f350e53c4d7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348131"
---
# <a name="other-control-structures-visual-basic"></a>その他の制御構造 (Visual Basic)
Visual Basic には、リソースを破棄したり、オブジェクト参照を繰り返さなければならない回数を減らしたりするうえで役立つ制御構造が用意されています。  
  
## <a name="usingend-using-construction"></a>Using...End Using コンストラクション  
 `Using...End Using` コンストラクションによりステートメント ブロックが構築され、このブロック内で SQL 接続などのリソースを使用します。 必要に応じて、`Using` ステートメントを使用してリソースを取得できます。 `Using` ブロックを終了すると、リソースが自動的に破棄され、他のコードがそのリソースを使用できるようになります。 リソースはローカルで、破棄可能である必要があります。 詳細については、「[Using ステートメント](../../../../visual-basic/language-reference/statements/using-statement.md)」を参照してください。  
  
## <a name="withend-with-construction"></a>With...End With コンストラクション  
 `With...End With` コンストラクションを使用すると、オブジェクト参照を一度指定した後、そのメンバーにアクセスする一連のステートメントを実行できます。 これにより、Visual Basic にアクセスするステートメントごとに参照を再確立する必要がなくなるため、コードが簡略化され、パフォーマンスが向上します。 詳細については、「[With...End With ステートメント](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [制御フロー](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [条件判断構造](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [ループ構造](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [入れ子になった制御構造](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Using ステートメント](../../../../visual-basic/language-reference/statements/using-statement.md)
- [With...End With ステートメント](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
