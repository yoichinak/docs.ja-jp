---
title: '方法: プロシージャ (Visual Basic) を作成します。'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, reusing
- procedure declarations
- procedures [Visual Basic], about procedures
ms.assetid: 4f779247-0b50-47e8-9e5c-ab5cf39ac0d2
ms.openlocfilehash: 0f3b0a793b2751b0ec9bb2b7cd6fedc12ae19e18
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970806"
---
# <a name="how-to-create-a-procedure-visual-basic"></a>方法: プロシージャ (Visual Basic) を作成します。
開始の宣言ステートメントの間のプロシージャを囲む (`Sub`または`Function`) と終了の宣言ステートメント (`End Sub`または`End Function`)。 すべての手順のコードは、これらのステートメントの範囲です。  
  
 プロシージャは、最初と最後のステートメントが、他のプロシージャの外部にある必要がありますので、別のプロシージャを含めることはできません。  
  
 さまざまな場所で同じタスクを実行するコードがあれば、プロシージャの 1 回として、タスクを記述し、コード内の異なる場所から呼び出すできます。  
  
### <a name="to-create-a-procedure-that-does-not-return-a-value"></a>値を返さないプロシージャを作成するには  
  
1.  その他のプロシージャの外側を使用して、`Sub`ステートメントの後に、`End Sub`ステートメント。  
  
2.  `Sub`ステートメントでは、以下の`Sub`キーワード、プロシージャ、かっこで囲まれたパラメーター リストの名前に置き換えます。  
  
3.  間のプロシージャのコード ステートメントを配置、`Sub`と`End Sub`ステートメント。  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a>値を返すプロシージャを作成するには  
  
1.  その他のプロシージャの外側を使用して、`Function`ステートメントの後に、`End Function`ステートメント。  
  
2.  `Function`ステートメントでは、以下の`Function`パラメーター リストをかっこで、プロシージャの名前を持つキーワードをクリックし、`As`戻り値のデータ型を指定する句。  
  
3.  間のプロシージャのコード ステートメントを配置、`Function`と`End Function`ステートメント。  
  
4.  使用して、`Return`ステートメントを呼び出し元のコードに値を返します。  
  
### <a name="to-connect-your-new-procedure-with-the-old-repetitive-blocks-of-code"></a>繰り返し発生する以前のコード ブロックで、新しいプロシージャを接続するには  
  
1.  古いコードのアクセス権がある場所に新しいプロシージャを定義することを確認します。  
  
2.  呼び出す 1 つのステートメントで反復的なタスクを実行するステートメントを置き換える、古い、繰り返し発生するコード ブロックで、`Sub`または`Function`プロシージャ。  
  
3.  プロシージャがある場合、`Function`値を返すことを呼び出し元のステートメントは、変数に格納することなど、返された値を持つ操作を実行します。 そうしないと、値は失われますを確認します。  
  
## <a name="example"></a>例  
 次`Function`プロシージャは、最長の辺またはの他の 2 つの辺の値を指定された直角三角形の斜辺を計算します。  
  
 [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>関連項目

- [プロシージャ](./index.md)
- [Sub プロシージャ](./sub-procedures.md)
- [Function プロシージャ](./function-procedures.md)
- [Property プロシージャ](./property-procedures.md)
- [演算子プロシージャ](./operator-procedures.md)
- [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)
- [再帰プロシージャ](./recursive-procedures.md)
- [プロシージャのオーバーロード](./procedure-overloading.md)
- [クラスとオブジェクト](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [オブジェクト指向プログラミング (Visual Basic)](../../concepts/object-oriented-programming.md)
