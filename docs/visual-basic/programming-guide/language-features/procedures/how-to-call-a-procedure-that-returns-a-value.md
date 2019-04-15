---
title: '方法: 値 (Visual Basic) を返すプロシージャを呼び出す'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
ms.openlocfilehash: 6f45f01489ee84b6addb1f7c7c8dc584332f38dd
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59333887"
---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a>方法: 値 (Visual Basic) を返すプロシージャを呼び出す
A`Function`プロシージャが呼び出し元のコードに値を返します。 呼び出すことが、名前と引数を含めることによって、式または代入ステートメントの右側にあるいずれか。  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a>式の中で関数のプロシージャを呼び出す  
  
1. 使用して、`Function`プロシージャ名の変数を使用する場合と同じ方法です。 使用することができます、`Function`プロシージャを呼び出す任意の場所、式で変数または定数を使用することができます。  
  
2. 引数リストを囲む中かっこでプロシージャ名に従ってください。 引数がない場合、かっこを省略することができます。 ただし、かっこを使用して、コードを読みやすくします。  
  
3. コンマで区切り、かっこ内の引数リストで、引数を配置します。 同じ順序で引数を指定するかどうかを必ずを`Function`プロシージャが、対応するパラメーターを定義します。  
  
     また、名前で、1 つまたは複数の引数を渡すことができます。 詳細については、次を参照してください。[位置と名前による引数を渡す](./passing-arguments-by-position-and-by-name.md)します。  
  
4. プロシージャから返される値は、式は、変数の値と同じように参加または定数します。  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a>代入ステートメントでプロシージャを関数を呼び出す  
  
1. 使用して、`Function`プロシージャ名の後に続く (`=`) 代入ステートメントにサインインします。  
  
2. 引数リストを囲む中かっこでプロシージャ名に従ってください。 引数がない場合、かっこを省略することができます。 ただし、かっこを使用して、コードを読みやすくします。  
  
3. コンマで区切り、かっこ内の引数リストで、引数を配置します。 同じ順序で引数を指定するかどうかを必ずを`Function`名で渡すことがない限り、プロシージャが、対応するパラメーターを定義します。  
  
4. プロシージャから返される値は、変数または代入ステートメントの左側にあるプロパティに格納されます。  
  
## <a name="example"></a>例  
 次の例では、Visual Basic<xref:Microsoft.VisualBasic.Interaction.Environ%2A>オペレーティング システム環境変数の値を取得します。 最初の行呼び出し`Environ`代入ステートメントでその行によって式と、2 つ目の呼び出し。 `Environ` その単一の引数として変数名を受け取ります。 呼び出し元のコードに変数の値を返します。  
  
 [!code-vb[VbVbcnProcedures#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#7)]  
  
## <a name="see-also"></a>関連項目

- [Function プロシージャ](./function-procedures.md)
- [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)
- [Function ステートメント](../../../../visual-basic/language-reference/statements/function-statement.md)
- [方法: 値を返すプロシージャを作成する](./how-to-create-a-procedure-that-returns-a-value.md)
- [方法: プロシージャから値を返す](./how-to-return-a-value-from-a-procedure.md)
- [方法: 値を返さないプロシージャを呼び出す](./how-to-call-a-procedure-that-does-not-return-a-value.md)
