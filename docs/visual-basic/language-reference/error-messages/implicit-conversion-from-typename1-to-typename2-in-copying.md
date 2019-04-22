---
title: "'ByRef' パラメーター '<typename1>' の値を、一致する引数に戻してコピーする際の、'<typename2>' から '<parametername>' への暗黙的な変換です。"
ms.date: 07/20/2015
f1_keywords:
- vbc41999
- bc41999
helpviewer_keywords:
- BC41999
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
ms.openlocfilehash: 7b02659d96b08c592b25ddf3ef1f99114c3ee269
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58831762"
---
# <a name="implicit-conversion-from-typename1-to-typename2-in-copying-the-value-of-byref-parameter-parametername-back-to-the-matching-argument"></a>暗黙的な変換 '\<typename1 >' を'\<typename2 >' の 'ByRef' パラメーターの値をコピー '\<parametername >'、一致する引数に戻してします。
プロシージャが呼び出される、 [ByRef](../../../visual-basic/language-reference/modifiers/byref.md)よりも、対応するパラメーターのさまざまな型の引数。  
  
 引数を渡す場合`ByRef`、Visual Basic は、ローカル変数の参照を渡す代わりにプロシージャに引数の値をコピーすることがあります。 このような場合は、プロシージャが返されるときに Visual Basic する必要がありますにコピーしてローカル変数の値戻す呼び出し元のコードの引数。  
  
 `ByRef` 引数の値がプロシージャにコピーされ、引数とパラメーターが同じ型である場合、変換は必要ありません。 種類が異なる場合は、Visual Basic が双方向で変換する必要があります。 使用できないため`CType`または暗黙的なプロシージャの引数またはパラメーター、このような変換での他の変換キーワードのいずれかが常にします。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「[Visual Basic での警告の構成](/visualstudio/ide/configuring-warnings-in-visual-basic)」をご覧ください。  
  
 **エラー ID:** BC41999  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   可能であれば、Visual Basic は、変換を行う必要はありませんので、プロシージャのパラメーターとして、同じ種類の呼び出し元の引数を使用します。  
  
-   パラメーター型とは異なる引数型を使用してプロシージャを呼び出す必要があり、呼び出し元の引数に値を返す必要がない場合は、 [ByRef](../../../visual-basic/language-reference/modifiers/byval.md) ではなく `ByRef`になるようにパラメーターを定義します。  
  
## <a name="see-also"></a>関連項目

- [プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [プロシージャのパラメーターと引数](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [引数の値渡しと参照渡し](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [暗黙の型変換と明示的な型変換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
