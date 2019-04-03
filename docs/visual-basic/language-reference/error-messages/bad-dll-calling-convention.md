---
title: DLL を正しく呼び出せません。
ms.date: 07/20/2015
f1_keywords:
- vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
ms.openlocfilehash: c4f9917a7fb807cf7da92a3bba2d3edec8045bd2
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58813521"
---
# <a name="bad-dll-calling-convention"></a>DLL を正しく呼び出せません。
ダイナミック リンク ライブラリ (DLL) に渡される引数が、ルーチンで想定されているものを正確に一致する必要があります。 呼び出し規則は、数、種類、および引数の順序で処理します。 プログラムを無効な型または引数の数が渡される DLL にルーチンを呼び出す可能性があります。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  すべての引数の型に同意を呼び出すルーチンの宣言で指定されていることを確認します。  
  
2.  同じ数の呼び出しの対象とするルーチンの宣言に示されている引数を渡していることを確認します。  
  
3.  DLL 内のルーチンは、値によって引数が必要ですが場合に、必ず`ByVal`ルーチンの宣言でこれらの引数が指定されています。  
  
## <a name="see-also"></a>関連項目

- [エラーの種類](../../../visual-basic/programming-guide/language-features/error-types.md)
- [Call ステートメント](../../../visual-basic/language-reference/statements/call-statement.md)
- [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)
