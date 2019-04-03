---
title: 型引数をデリゲートから推論できませんでした
ms.date: 07/20/2015
f1_keywords:
- bc36564
- vbc36564
helpviewer_keywords:
- BC36564
ms.assetid: 21312807-e1cd-4ac1-ae1c-c28a9c25164d
ms.openlocfilehash: 1024cf6f2c1fa112db29cb710eef190a5022d3af
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838600"
---
# <a name="type-arguments-could-not-be-inferred-from-the-delegate"></a>型引数をデリゲートから推論できませんでした
代入ステートメントは、 `AddressOf` を使用してジェネリック プロシージャのアドレスをデリゲートに割り当てますが、ジェネリック プロシージャに型引数を指定していません。  
  
 通常、ジェネリック型を呼び出す場合は、ジェネリック型が定義する型パラメーターごとに型引数を指定します。 型引数を指定しない場合、コンパイラは型パラメーターに渡される型を推論しようとします。 コンテキストにコンパイラが型を推論するのに十分な情報が提供されていない場合は、エラーが生成されます。  
  
 **エラー ID:** BC36564  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   ジェネリック プロシージャの型引数を `AddressOf` 式で指定します。  
  
## <a name="see-also"></a>関連項目

- [Visual Basic におけるジェネリック型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [AddressOf 演算子](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Generic Procedures in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)
- [型リスト](../../../visual-basic/language-reference/statements/type-list.md)
- [拡張メソッド](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
