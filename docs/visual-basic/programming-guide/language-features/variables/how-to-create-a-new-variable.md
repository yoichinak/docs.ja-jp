---
title: '方法: 新しい変数 (Visual Basic) を作成します。'
ms.date: 07/20/2015
helpviewer_keywords:
- Dim statement [Visual Basic]
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
ms.openlocfilehash: 86236f7e6f4821cc45dfab80273d82b6f167fba8
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58823286"
---
# <a name="how-to-create-a-new-variable-visual-basic"></a>方法: 新しい変数 (Visual Basic) を作成します。
変数を作成する、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)します。  
  
### <a name="to-create-a-new-variable"></a>新しい変数を作成するには  
  
1.  変数を宣言、`Dim`ステートメント。  
  
    ```  
    Dim newCustomer  
    ```  
  
2.  変数の特性の仕様を含める[プライベート](../../../../visual-basic/language-reference/modifiers/private.md)、[静的](../../../../visual-basic/language-reference/modifiers/static.md)、 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)、または[WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md)します。 詳細については、次を参照してください。[宣言された要素の特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)します。  
  
    ```  
    Public Static newCustomer  
    ```  
  
     必要はありません、`Dim`の宣言でその他のキーワードを使用する場合は、キーワード。  
  
3.  Visual Basic の規則と規則に従う必要があります、変数の名前を持つ仕様に従ってください。 詳細については、次を参照してください。 [宣言された要素の名前](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
  
    ```  
    Public Static newCustomer  
    ```  
  
4.  名に続けて、[として](../../../../visual-basic/language-reference/statements/as-clause.md)変数のデータ型を指定する句。  
  
    ```  
    Public Static newCustomer As Customer  
    ```  
  
     既定値を使用して、データ型を指定しない場合:`Object`します。  
  
5.  に従って、`As`句に等号 (`=`) し、変数の初期値を等号 (=) に従います。  
  
     Visual Basic が実行されるたびに、変数に指定した値を割り当て、`Dim`ステートメント。 含むコードが最初に入ると、Visual Basic で、変数のデータ型の既定の初期値が割り当てられます、初期値を指定しない場合、`Dim`ステートメント。  
  
     含めることによって、クラスのインスタンスを作成するには、変数が参照型である場合、 [New 演算子](../../../../visual-basic/language-reference/operators/new-operator.md)キーワード、`As`句。 使用しない場合`New`、変数の初期値は[Nothing](../../../../visual-basic/language-reference/nothing.md)します。  
  
    ```  
    Public Static newCustomer As New Customer  
    ```  
  
## <a name="see-also"></a>関連項目

- [変数](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [宣言された要素の名前](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [宣言された要素の特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [ステートメント](../../../../visual-basic/language-reference/statements/index.md)
- [ローカル型の推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Infer ステートメント](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
