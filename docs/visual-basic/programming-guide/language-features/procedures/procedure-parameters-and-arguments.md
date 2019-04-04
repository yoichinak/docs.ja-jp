---
title: プロシージャのパラメーターと引数 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], argument lists
- values [Visual Basic], passing to procedures
- arguments [Visual Basic], passing
- procedures [Visual Basic], parameters
- Visual Basic code, argument lists
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic procedures
- parameters [Visual Basic], lists
- arguments [Visual Basic], Visual Basic procedures
- arguments [Visual Basic], procedures
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- argument lists [Visual Basic]
- procedures [Visual Basic], parameter lists
ms.assetid: ff275aff-aa13-40df-bd4c-63486db8c1e9
ms.openlocfilehash: 80065cabcacdcf44b04fef7bacb978ca9c8077ae
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825457"
---
# <a name="procedure-parameters-and-arguments-visual-basic"></a>プロシージャのパラメーターと引数 (Visual Basic)
ほとんどの場合、プロシージャには、呼び出されたときの状況に関する情報が必要があります。 繰り返される、または共有のタスクを実行する手順では、呼び出しごとに異なる情報を使用します。 この情報は、変数、定数、および呼び出しでは、プロシージャに渡す式で構成されます。  
  
 A*パラメーター*プロシージャには、このメソッドを呼び出すときに指定することが期待される値を表します。 プロシージャの宣言では、そのパラメーターを定義します。  
  
 パラメーターなし、1 つのパラメーター、または 1 つ以上のプロシージャを定義できます。 パラメーターを指定するプロシージャの定義の一部と呼ばれる、*パラメーター リスト*します。  
  
 *引数*プロシージャを呼び出すときにプロシージャのパラメーターに指定した値を表します。 プロシージャを呼び出すときに、呼び出し元のコードは、引数を提供します。 引数を指定するプロシージャの呼び出しの一部と呼ばれる、*引数リスト*します。  
  
 次の図は、プロシージャを呼び出すコード`safeSquareRoot`2 つの異なる場所からします。 最初の呼び出しは、変数の値を渡します`x`(4.0) パラメーターに`number`とで戻り値`root`(2.0)、変数に割り当てられている`y`します。 2 番目の呼び出しにリテラル値 9.0 を通過する`number`、戻り値 (3.0) を変数に代入と`z`します。  
  
 ![パラメーターに引数を渡すことを示す図](./media/procedure-parameters-and-arguments/pass-argument-parameter.gif)  
  
 詳細については、[の相違点の間でパラメーターと引数](./differences-between-parameters-and-arguments.md)を参照してください。  
  
## <a name="parameter-data-type"></a>パラメーターのデータ型  
 使用して、パラメーターのデータ型を定義する、`As`宣言内の句。 たとえば、次の関数は、文字列と整数を受け取ります。  
  
 [!code-vb[VbVbcnProcedures#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#32)]  
  
 型チェック スイッチの場合 ([Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) は`Off,`、`As`する点を除いて、すべてのパラメーターがそれを使用する必要があります、1 つのパラメーターで使用する場合、句は省略可能でします。 型チェックが場合`On`、`As`句がすべてのプロシージャのパラメーターが必要です。  
  
 呼び出し元のコードがなど、対応するパラメーターの異なるデータ型の引数を指定するかどうかは`Byte`を`String`パラメーターを次のいずれかの操作にする必要があります。  
  
-   パラメーターのデータ型に拡大変換するデータ型の引数だけを渡す  
  
-   設定`Option Strict Off`暗黙的な縮小変換を許可するか、  
  
-   変換キーワードを使用して、データ型を明示的に変換します。  
  
### <a name="type-parameters"></a>型パラメーター  
 A*ジェネリック プロシージャ*も 1 つまたは複数定義します*パラメーター入力*だけでなく、通常のパラメーター。 ジェネリック プロシージャでは、個々 の呼び出しの要件をデータ型を調整できるように、プロシージャを呼び出すたびに異なるデータ型を渡すコードの呼び出しを許可します。 「 [Generic Procedures in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [プロシージャ](./index.md)
- [Sub プロシージャ](./sub-procedures.md)
- [Function プロシージャ](./function-procedures.md)
- [Property プロシージャ](./property-procedures.md)
- [演算子プロシージャ](./operator-procedures.md)
- [方法: プロシージャのパラメーターを定義します。](./how-to-define-a-parameter-for-a-procedure.md)
- [方法: プロシージャに引数を渡す](./how-to-pass-arguments-to-a-procedure.md)
- [引数の値渡しと参照渡し](./passing-arguments-by-value-and-by-reference.md)
- [プロシージャのオーバーロード](./procedure-overloading.md)
- [Visual Basic における型変換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
