---
title: '方法: 変数 (Visual Basic) では、複数の値を保持します。'
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], composite data types
- composite types [Visual Basic]
- composite data types [Visual Basic]
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures [Visual Basic], composite data types
- arrays [Visual Basic], compilation errors
- types [Visual Basic], composite
ms.assetid: 5fe0e558-aac2-4a40-b7f2-7cfea7336917
ms.openlocfilehash: e2e1648ea508ecdd744adb8d2a4f7fdbc1e586c4
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59332262"
---
# <a name="how-to-hold-more-than-one-value-in-a-variable-visual-basic"></a>方法: 変数 (Visual Basic) では、複数の値を保持します。
として宣言する場合、変数が 1 つ以上の値を保持する*複合データ型*します。  
  
 [複合データ型](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)構造体、配列、およびクラスが含まれます。 複合データ型の変数には、基本データ型とその他の複合型の組み合わせを保持できます。 構造体とクラスは、コードだけではなく、データを保持できます。  
  
### <a name="to-hold-more-than-one-value-in-a-variable"></a>変数に 1 つ以上の値を保持するには  
  
1. 変数の使用する複合データ型を確認します。  
  
2. 複合データ型が既に定義されていない場合、変数が使用できるように定義します。  
  
    -   含む構造体の定義、 [Structure ステートメント](../../../../visual-basic/language-reference/statements/structure-statement.md)します。  
  
    -   配列を定義、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)します。  
  
    -   クラスを定義、[クラス ステートメント](../../../../visual-basic/language-reference/statements/class-statement.md)します。  
  
3. 使用して変数を宣言、`Dim`ステートメント。  
  
4. 変数名に続けて、`As`句。  
  
5. に従って、`As`キーワードは、適切な複合データ型の名前に置き換えます。  
  
## <a name="see-also"></a>関連項目

- [データの種類](../../../../visual-basic/language-reference/data-types/index.md)
- [型文字](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [複合データ型](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [構造体](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [クラスとオブジェクト](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
