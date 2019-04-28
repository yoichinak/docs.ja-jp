---
title: Sub プロシージャ (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Sub procedures [Visual Basic], about Sub procedures
- statement blocks
- Sub procedures [Visual Basic], calling
- procedures [Visual Basic], calling
- Sub procedures [Visual Basic], syntax
- Sub procedures
- procedures [Visual Basic], Sub
- syntax [Visual Basic], Sub procedures
ms.assetid: 6a0a4958-ed0a-4d3d-8d31-0772c82bda58
ms.openlocfilehash: b70594e002bbf08f0890586e78df901ccb26c7ce
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791822"
---
# <a name="sub-procedures-visual-basic"></a>Sub プロシージャ (Visual Basic)
A`Sub`手順は、一連の Visual Basic のステートメントで囲まれた、`Sub`と`End Sub`ステートメント。 `Sub`呼び出しコードに値を返すことはできませんが、プロシージャは、タスクを実行し、呼び出し元のコードにコントロールを返します。  
  
 そのステートメントが実行されます、プロシージャが呼び出されるたびに後の最初の実行可能ステートメントで始まる、`Sub`ステートメントと最初の終了`End Sub`、 `Exit Sub`、または`Return`ステートメントが発生しました。  
  
 定義することができます、`Sub`プロシージャでは、モジュール、クラス、および構造体。 既定では`Public`、することができるから呼び出せる任意の場所でモジュール、クラス、またはで定義された構造体にアクセスできるアプリケーション。 用語、*メソッド*、について説明します、`Sub`または`Function`プロシージャの定義の外部からアクセスされるモジュール、クラスまたは構造体。 詳細については、「[プロシージャ](./index.md)」を参照してください。  
  
 A`Sub`プロシージャは、定数、変数、または、呼び出し元のコードに渡される式などの引数をとることができます。  
  
## <a name="declaration-syntax"></a>宣言の構文  
 宣言の構文、`Sub`手順のとおりです。  
  
 `[` *modifiers* `] Sub`  *subname* `[(` *parameterlist* `)]`  
  
 `' Statements of the Sub procedure.`  
  
 `End Sub`  
  
 `modifiers`アクセス レベルとオーバー ロード、オーバーライド、共有、およびシャドウ処理に関する情報を指定できます。 詳細については、次を参照してください。 [Sub ステートメント](../../../../visual-basic/language-reference/statements/sub-statement.md)します。  
  
## <a name="parameter-declaration"></a>パラメーターの宣言  
 各プロシージャのパラメーターと同様にどのように変数を宣言する、パラメーター名とデータ型を指定することを宣言するとします。 引数渡しの方法を指定することもでき、パラメーターは省略可能かどうか、またはパラメーター配列。  
  
 パラメーター リスト内の各パラメーターの構文は次のとおりです。  
  
 `[Optional] [ByVal | ByRef] [ParamArray]`  *parametername*  `As`  *datatype*  
  
 パラメーターが省略可能な場合は、その宣言の一部として既定値も指定する必要があります。 既定値を指定する構文は次のとおりです。  
  
 `Optional [ByVal | ByRef]`  *parametername*  `As`  *datatype*  `=`  *defaultvalue*  
  
### <a name="parameters-as-local-variables"></a>ローカル変数とパラメーター  
 プロシージャに制御が渡される、各パラメーターは、ローカル変数として扱われます。 これは、その有効期間は、プロシージャのと同じことと、そのスコープは、プロシージャ全体を意味します。  
  
## <a name="calling-syntax"></a>呼び出し構文  
 呼び出す、`Sub`スタンドアロンのステートメントの呼び出しで明示的にプロシージャ。 式の中でその名前を使用して呼び出すことはできません。 省略可能でないすべての引数の値を指定する必要があり、引数リストをかっこで囲む必要があります。 引数が指定されていない場合、かっこを省略することができます。 使用、`Call`キーワードは省略可能ですが、推奨されません。  
  
 呼び出しの構文を`Sub`手順のとおりです。  
  
 `[Call]`  *subname* `[(` *argumentlist* `)]`  
  
 呼び出すことができます、`Sub`からそれを定義するクラスの外側のメソッド。 最初に、使用する必要がある、`New`キーワード、クラスのインスタンスを作成またはメソッドを呼び出すには、クラスのインスタンスを返します。 詳細については、次を参照してください。 [New 演算子](../../../../visual-basic/language-reference/operators/new-operator.md)します。 次を呼び出す、次の構文を使用することができます、`Sub`インスタンス オブジェクトのメソッド。  
  
 *オブジェクト*.*methodname*`[(`*argumentlist*`)]`  
  
### <a name="illustration-of-declaration-and-call"></a>宣言と呼び出しの図  
 次`Sub`の手順では、コンピューターの演算子、アプリケーションを実行する作業はどれもタイムスタンプを表示します。 アプリケーションのすべてのタスクの開始時に、このコードではなく、呼び出しだけ`tellOperator`さまざまな場所からします。 各呼び出しには文字列で、`task`開始されているタスクを識別する引数。  
  
 [!code-vb[VbVbcnProcedures#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#2)]  
  
 次の例では、一般的な呼び出しを`tellOperator`します。  
  
 [!code-vb[VbVbcnProcedures#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>関連項目

- [プロシージャ](./index.md)
- [Function プロシージャ](./function-procedures.md)
- [Property プロシージャ](./property-procedures.md)
- [演算子プロシージャ](./operator-procedures.md)
- [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)
- [Sub ステートメント](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [方法: 値を返さないプロシージャを呼び出す](./how-to-call-a-procedure-that-does-not-return-a-value.md)
- [方法: Visual Basic でイベント ハンドラーを呼び出す](./how-to-call-an-event-handler.md)
