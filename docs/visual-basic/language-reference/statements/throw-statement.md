---
title: Throw ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Throw
helpviewer_keywords:
- structured exception handling, throw statements
- try-catch exception handling, throw statements
- throw statement [Visual Basic], about throw statements
- throwing exceptions, throw statement
- exception handling, throw statement
- On Error statement [Visual Basic], throwing exceptions
- throwing exceptions
- exception handling, unstructured
- throw statement [Visual Basic]
ms.assetid: a6e07406-5c8a-4498-87a2-8339f3651d62
ms.openlocfilehash: 2494eac2f61f112f3ba6321ada7404f8cd618049
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766637"
---
# <a name="throw-statement-visual-basic"></a>Throw ステートメント (Visual Basic)
プロシージャ内で例外をスローします。  
  
## <a name="syntax"></a>構文  
  
```  
Throw [ expression ]  
```  
  
## <a name="part"></a>パーツ  
 `expression`  
 スローされる例外に関する情報を提供します。 内に存在するときに省略可能な`Catch`ステートメントでは、それ以外の場合に必要です。  
  
## <a name="remarks"></a>Remarks  
 `Throw`ステートメントは、構造化例外処理コードで処理できる例外をスローします (`Try`.`Catch`...`Finally`) または非構造化例外処理コード (`On Error GoTo`)。 使用することができます、 `Throw` Visual Basic は、適切な例外処理コードが見つかるまで呼び出し履歴を移動するために、コード内のエラーをトラップするステートメント。  
  
 A`Throw`式ステートメントでのみ使用できます、`Catch`ステートメントでは、case ステートメントが現在処理中の例外を再スロー、`Catch`ステートメント。  
  
 `Throw`ステートメントの呼び出し履歴をリセットする、`expression`例外。 場合`expression`が指定されていない、コール スタックは変更されません。 例外の呼び出し履歴にアクセスすることができます、<xref:System.Exception.StackTrace%2A>プロパティ。  
  
## <a name="example"></a>例  
 次のコードでは、`Throw`例外をスローするステートメント。  
  
 [!code-vb[VbVbalrStatements#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#84)]  
  
## <a name="requirements"></a>必要条件  
 **名前空間:**[Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **モジュール:** `Interaction`  
  
 **アセンブリ:** Visual Basic ランタイム ライブラリ (Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>関連項目

- [Try...Catch...Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [On Error ステートメント](../../../visual-basic/language-reference/statements/on-error-statement.md)
