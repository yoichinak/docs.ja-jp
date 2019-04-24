---
title: パラメーターと引数の違い (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- parameters [Visual Basic], and arguments
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], and parameters
- procedure parameters
- parameters [Visual Basic], definition
ms.assetid: c237c056-74f4-4749-9f2c-15864f139a31
ms.openlocfilehash: a69b956c7cffcc2a26916d6fc92f23dd4e2322d7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58838977"
---
# <a name="differences-between-parameters-and-arguments-visual-basic"></a>パラメーターと引数の違い (Visual Basic)
ほとんどの場合、プロシージャが呼び出されたときの状況に関する情報が必要です。 繰り返される、または共有のタスクを実行する手順では、呼び出しごとに異なる情報を使用します。 この情報は、変数、定数、および呼び出しでは、プロシージャに渡す式で構成されます。  
  
 プロシージャには、この情報を通信するために、プロシージャの定義、*パラメーター*、呼び出し元のコードを渡します、*引数*パラメーターにします。 駐車場としてパラメーターと引数は、自動車を考えることができます。 さまざまな自動車は、異なる時刻で駐車場で駐車できると同様、呼び出し元のコードは、it は、プロシージャを呼び出すたびに、同じパラメーターを別の引数を渡すことができます。  
  
## <a name="parameters"></a>パラメーター  
 A*パラメーター*プロシージャには、それを呼び出すときに渡すことが期待される値を表します。 プロシージャの宣言では、そのパラメーターを定義します。  
  
 定義するとき、`Function`または`Sub`プロシージャを指定する、*パラメーター リスト*プロシージャ名の直後に続くかっこ内に示します。 各パラメーターの名前、データ型、および引き渡し方法を指定 ([ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)または[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md))。 パラメーターが省略可能であるかも指定できます。 これは、その値を渡す呼び出し元のコードがないことを意味します。  
  
 各パラメーターの名前として、*ローカル変数*の手順でします。 パラメーター名は、他の変数を使用すると同じ方法で使用します。  
  
## <a name="arguments"></a>引数  
 *引数*プロシージャを呼び出す場合、プロシージャのパラメーターに渡す値を表します。 プロシージャを呼び出すときに、呼び出し元のコードは、引数を提供します。  
  
 呼び出すと、`Function`または`Sub`プロシージャを含める、*引数リスト*プロシージャ名の直後に続くかっこで囲まれました。 各引数は、パラメーター リスト内の同じ位置に対応します。  
  
 パラメーターの定義とは対照的引数には名前がありません。 各引数は、0 以上の変数、定数、およびリテラルに含めることができる式です。 通常、対応するパラメーター、定義されているデータ型に一致する必要があります式の評価結果のデータ型と、いずれの場合も、パラメーターの型に変換できるあります。  
  
## <a name="see-also"></a>関連項目

- [プロシージャ](./index.md)
- [Sub プロシージャ](./sub-procedures.md)
- [Function プロシージャ](./function-procedures.md)
- [Property プロシージャ](./property-procedures.md)
- [演算子プロシージャ](./operator-procedures.md)
- [方法: プロシージャのパラメーターを定義します。](./how-to-define-a-parameter-for-a-procedure.md)
- [方法: プロシージャに引数を渡す](./how-to-pass-arguments-to-a-procedure.md)
- [引数の値渡しと参照渡し](./passing-arguments-by-value-and-by-reference.md)
- [再帰プロシージャ](./recursive-procedures.md)
- [プロシージャのオーバーロード](./procedure-overloading.md)
