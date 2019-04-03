---
title: '方法: 別の配列 (Visual Basic) を 1 つの配列を割り当てる'
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, arrays
- arrays [Visual Basic], assigning
- arrays [Visual Basic], covariance
ms.assetid: 1ae89ea5-f292-4282-bcfc-e9b06b37fbd5
ms.openlocfilehash: 834dad07ec1f4116aca72a184ccffc664d0a42ed
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58835285"
---
# <a name="how-to-assign-one-array-to-another-array-visual-basic"></a>方法: 別の配列 (Visual Basic) を 1 つの配列を割り当てる
配列がオブジェクトであるため、他のオブジェクト型のような代入ステートメントで使用することができます。 配列変数の配列の要素と、ランク、および長さの情報を構成するデータにポインターを保持し、割り当ては、このポインターのみをコピーします。  
  
### <a name="to-assign-one-array-to-another-array"></a>別の配列に 1 つの配列を割り当てる  
  
1.  2 つの配列に同じランク (次元数) と互換性のある要素のデータ型があることを確認します。  
  
2.  標準の代入ステートメントを使用して、コピー先の配列を元の配列を割り当てます。 いずれの配列名をかっこでは使用しないでください。  
  
    ```  
    Dim formArray() As System.Windows.Forms.Form  
    Dim controlArray() As System.Windows.Forms.Control  
    controlArray = formArray  
    ```  
  
 別に 1 つの配列を割り当てた場合、次の規則が適用されます。  
  
-   **ランクが等しい。** コピー先配列のランク (次元数) は、ソース配列と同じである必要があります。  
  
     2 つの配列のランクが等しい、指定されたディメンションは等値である必要はありません。 割り当ての際に、特定の次元の要素の数を変更できます。  
  
-   **要素の型。** 両方の配列のいずれかがいる必要があります*参照型*要素、または両方の配列が必要*値の型*要素。 詳細については、「 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)」を参照してください。  
  
    -   両方の配列には、値型の要素がある、要素のデータ型正確に同じでなければなりません。 唯一の例外は、の配列を割り当てることができます`Enum`の基本型の配列に要素`Enum`します。  
  
    -   両方の配列には、参照型の要素がある、ソース要素の型が変換先の要素の型から派生する必要があります。 これが、大文字と小文字の場合は、その要素として同じ継承関係がある 2 つの配列。 これは呼び出されます*配列の共変性*します。  
  
 コンパイラは、エラー場合は、上記の規則違反の例のデータ型に互換性がない場合や、ランクが等しくないを報告します。 割り当てを試行する前に、配列に互換性があるかどうかを確認するコードにエラー処理を追加できます。 使用することも、 [TryCast 演算子](../../../../visual-basic/language-reference/operators/trycast-operator.md)例外をスローしないようにする場合は、キーワード。  
  
## <a name="see-also"></a>関連項目

- [配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [配列のトラブルシューティング](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
- [Enum ステートメント](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [配列変換](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
