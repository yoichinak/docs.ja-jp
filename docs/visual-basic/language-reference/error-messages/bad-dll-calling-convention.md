---
title: DLL を正しく呼び出せません。
ms.date: 07/20/2015
f1_keywords:
- vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
ms.openlocfilehash: f7b0c3a6edbe0b950195306fa66287ff9b209bfe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61935279"
---
# <a name="bad-dll-calling-convention"></a>DLL を正しく呼び出せません。
ダイナミック リンク ライブラリ (DLL) に渡される引数は、ルーチンによって予期されるものと完全に一致する必要があります。 呼び出し規則は、引数の数、型、および順序を扱います。 プログラムが DLL 内のルーチンを呼び出しているときに、間違った型または数の引数が渡されている可能性があります。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. すべての引数の型が、呼び出しているルーチンの宣言で指定されている型と一致していることを確認します。  
  
2. 呼び出しているルーチンの宣言で指定したものと同じ数の引数を渡していることを確認します。  
  
3. DLL ルーチンが値渡しの引数を予期している場合は、ルーチンの宣言でこれらの引数に `ByVal` が指定されていることを確認します。  
  
## <a name="see-also"></a>関連項目

- [エラーの種類](../../../visual-basic/programming-guide/language-features/error-types.md)
- [Call ステートメント](../../../visual-basic/language-reference/statements/call-statement.md)
- [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)
