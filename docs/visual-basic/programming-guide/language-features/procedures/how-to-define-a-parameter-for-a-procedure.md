---
title: '方法: プロシージャ (Visual Basic) のパラメーターを定義します。'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure parameters [Visual Basic], defining data types for
- procedures [Visual Basic], parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters [Visual Basic], defining
ms.assetid: 7962808d-407e-4e84-984e-43e9857c53c9
ms.openlocfilehash: 01b150d70c07897f8217ed6958e3654aa28fdf51
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56971794"
---
# <a name="how-to-define-a-parameter-for-a-procedure-visual-basic"></a>方法: プロシージャ (Visual Basic) のパラメーターを定義します。
A*パラメーター*それを呼び出すときに、プロシージャに値を渡すコードの呼び出しを許可します。 プロシージャの各パラメーターは、変数を宣言すると、その名前とデータ型を指定することと同じ方法で宣言します。 渡す方法を指定するかどうか、パラメーターは省略可能です。  
  
 詳細については、[プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)を参照してください。  
  
### <a name="to-define-a-procedure-parameter"></a>プロシージャのパラメーターを定義するには  
  
1.  プロシージャの宣言では、その他のパラメーターをコンマで区切って、プロシージャのパラメーター リストに、パラメーター名を追加します。  
  
2.  パラメーターのデータ型を決定します。  
  
3.  パラメーター名に続けて、`As`データ型を指定する句。  
  
4.  パラメーターの引き渡し方法を決定します。 通常、プロシージャ呼び出し元のコードでは、その値を変更できるようにする場合を除きに、値でパラメーターを渡します。  
  
5.  パラメーター名の前に[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)または[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)引き渡し方法を指定します。 詳細については、[の相違点の間の値と参照渡しによって引数を渡す](./differences-between-passing-an-argument-by-value-and-by-reference.md)を参照してください。  
  
6.  渡しのパラメーターが省略可能な場合は、前に[(省略可能)](../../../../visual-basic/language-reference/modifiers/optional.md)は等号でパラメーターのデータ型に従います (`=`) と、既定値。  
  
     次の例のアウトラインを定義する、 `Sub` 3 つのパラメーターを持つプロシージャ。 最初の 2 つが必要ですし、3 つ目は省略可能です。 パラメーターの宣言は、パラメーター リストにコンマで区切られます。  
  
     [!code-vb[VbVbcnProcedures#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#33)]  
  
     最初のパラメーターを受け入れる、`customer`オブジェクト、および`updateCustomer`に渡される変数を直接更新できます`c`引数が渡されるため[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)します。 渡されるために、プロシージャが最後の 2 つの引数の値を変更できません[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)します。  
  
     呼び出し元のコードがの値を指定しないかどうか、`level`パラメーターでは、Visual Basic 設定を既定値の 0。  
  
     型チェック スイッチの場合 ([Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) は`Off`、`As`パラメーターを定義するときに、句は省略可能です。 ただし、任意の 1 つのパラメーターを使用している場合、`As`句では、いずれも使用する必要あります。 型チェック スイッチがある場合`On`、`As`句がすべてのパラメーター定義が必要です。  
  
     すべてのプログラミング要素のデータ型の指定と呼びます*厳密な型指定*します。 設定すると`Option Strict On`、Visual Basic は、厳密な型指定を適用します。 これは強くお勧めします、次の理由。  
  
    -   変数とパラメーターの IntelliSense のサポートが有効にするとします。 これにより、コードに入力すると、プロパティやその他のメンバーを表示することができます。  
  
    -   これにより、コンパイラが型チェックを実行できます。 これは、オーバーフローなどのエラーにより実行時に失敗するステートメントを検出するのに役立ちます。 サポートしていないオブジェクトに対するメソッドの呼び出しをキャッチします。  
  
    -   コードの実行速度が速くなります。 この理由の 1 つは、プログラミング要素のデータ型を指定しない場合、Visual Basic コンパイラが割り当てる、`Object`型。 コンパイル済みのコードは、間を気軽に変換する必要があります`Object`とその他のデータ型は、パフォーマンスが低下します。  
  
## <a name="see-also"></a>関連項目

- [プロシージャ](./index.md)
- [Sub プロシージャ](./sub-procedures.md)
- [Function プロシージャ](./function-procedures.md)
- [方法: プロシージャに引数を渡す](./how-to-pass-arguments-to-a-procedure.md)
- [引数の値渡しと参照渡し](./passing-arguments-by-value-and-by-reference.md)
- [再帰プロシージャ](./recursive-procedures.md)
- [プロシージャのオーバーロード](./procedure-overloading.md)
- [クラスとオブジェクト](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [オブジェクト指向プログラミング (Visual Basic)](../../concepts/object-oriented-programming.md)
