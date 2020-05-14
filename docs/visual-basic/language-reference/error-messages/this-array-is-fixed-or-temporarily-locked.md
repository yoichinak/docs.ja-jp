---
title: この配列は固定か、または一時的にロックされています。
ms.date: 07/20/2015
f1_keywords:
- vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
ms.openlocfilehash: 8d5e4add2d92a575126fb934ac3874a2e37685f5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350782"
---
# <a name="this-array-is-fixed-or-temporarily-locked-visual-basic"></a>この配列は固定か、または一時的にロックされています。(Visual Basic)
このエラーには、次のような原因が考えられます。  
  
- `ReDim` を使用して、固定サイズの配列の要素数を変更している。  
  
- モジュールレベルの動的配列を再定義しており、その中の 1 つの要素がプロシージャへの引数として渡されている。 要素が渡されると、プロシージャ内の参照パラメーターのメモリの割り当て解除を防ぐために、配列がロックされます。  
  
- 配列を格納する `Variant` 変数に値を代入しようとしたが、`Variant` が現在ロックされている。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. `ReDim` で宣言する (配列がプロシージャ内で宣言されている場合) か、要素数を指定せずに宣言する (配列がモジュール レベルで宣言されている場合) ことによって、元の配列を固定ではなく動的にします。  
  
2. モジュールのすべてのプロシージャ内で要素が表示されるようになるため、本当に要素を渡す必要があるかどうかを判断してください。  
  
3. `Variant` をロックしているものを特定し、それを修復します。  
  
## <a name="see-also"></a>関連項目

- [配列](../../../visual-basic/programming-guide/language-features/arrays/index.md)
