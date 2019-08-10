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
ms.openlocfilehash: 9680700267f17c8e316de351fead61f1dc4aded0
ms.sourcegitcommit: 9ee6cd851b6e176a5811ea28ed0d5935c71950f9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2019
ms.locfileid: "68869019"
---
# <a name="throw-statement-visual-basic"></a>Throw ステートメント (Visual Basic)

プロシージャ内で例外をスローします。

## <a name="syntax"></a>構文

```vb
Throw [ expression ]
```

## <a name="part"></a>パーツ

`expression`\
スローされる例外に関する情報を提供します。 `Catch`ステートメント内に存在する場合は省略可能。それ以外の場合は必須。

## <a name="remarks"></a>Remarks

ステートメント`Throw`によって例外がスローされ、構造化された例外処理`Try`コード (...`Catch`...) または非構造化例外処理コード`On Error GoTo`() があります。 `Finally` `Throw`ステートメントを使用すると、適切な例外処理コードが見つかるまで呼び出し履歴が上に移動するの Visual Basic で、コード内でエラーをトラップすることができます。

式が指定されていない`Catch` `Catch`ステートメントは、ステートメント内でのみ使用できます。この場合、ステートメントは、ステートメントによって現在処理されている例外を再スローします。 `Throw`

ステートメント`Throw`は、 `expression`例外の呼び出し履歴をリセットします。 が`expression`指定されていない場合、呼び出し履歴は変更されません。 <xref:System.Exception.StackTrace%2A>プロパティを使用して、例外の呼び出し履歴にアクセスできます。

## <a name="example"></a>例

次のコードでは`Throw` 、ステートメントを使用して例外をスローします。

[!code-vb[VbVbalrStatements#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#84)]

## <a name="see-also"></a>関連項目

- [Try...Catch...Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [On Error ステートメント](../../../visual-basic/language-reference/statements/on-error-statement.md)
