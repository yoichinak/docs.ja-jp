---
title: ステートメントの終わりを指定してください。
ms.date: 07/20/2015
f1_keywords:
- bc30205
- vbc30205
helpviewer_keywords:
- BC30205
ms.assetid: 53c7f825-a737-4b76-a1fa-f67745b8bd40
ms.openlocfilehash: 1ce5c793a09df34ac17e70e3253e98108bf76fb8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61803332"
---
# <a name="end-of-statement-expected"></a>ステートメントの終わりを指定してください。
ステートメントが構文的に完了するが、その他のプログラミング要素に依存してステートメントを終了する要素。 行終端記号は、すべてのステートメントの末尾にある必要があります。
  
 行終端記号は、Visual Basic のソース ファイルの文字を行に分割します。 行ターミネータの例には、Unicode キャリッジ リターン文字 (& HD)、Unicode とライン フィード文字 (& HA)、および、Unicode 復帰文字の Unicode のラインフィード文字後にします。 行ターミネータの詳細については、次を参照してください。、 [Visual Basic 言語仕様](~/_vblang/spec/lexical-grammar.md#line-terminators)します。
  
 **エラー ID:** BC30205
  
## <a name="to-correct-this-error"></a>このエラーを解決するには
  
1. 2 つの異なるステートメントが同じ行に格納された誤ってかどうかを確認します。
  
2. ステートメントを終了要素の後に行終端記号を挿入します。
  
## <a name="see-also"></a>関連項目

- [方法: コード内でステートメントを分割および連結する](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
- [ステートメント](../../../visual-basic/programming-guide/language-features/statements.md)
