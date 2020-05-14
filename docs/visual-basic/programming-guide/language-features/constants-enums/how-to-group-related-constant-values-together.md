---
title: '方法: 関連する定数値をまとめてグループ化する'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
ms.openlocfilehash: 151eefee4f69e1db8ba40f91334da8a051b95732
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354041"
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a>方法: 関連する定数値をまとめてグループ化する (Visual Basic)
関連する定数をまとめてグループ化するには、列挙型が最適です。 列挙型は、クラスまたはモジュールの宣言セクションで `Enum` ステートメントを使用して作成します。 詳細については、[列挙型の宣言方法](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)に関するページを参照してください。  
  
### <a name="to-group-related-constant-values"></a>関連する定数値をグループ化するには  
  
1. コード アクセス レベル、`Enum` キーワード、有効な名前を含む宣言を記述します。 次の例では、`Private` の列挙型 `temperatureValues` を作成しています。  
  
     [!code-vb[VbEnumsTask#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#21)]  
  
2. 列挙型の定数を定義します。 次の例では、`Public` の `temperatureValues` 列挙型を作成して、値を割り当てています。  
  
     [!code-vb[VbEnumsTask#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#1)]  
  
## <a name="see-also"></a>関連項目

- [列挙型と名前の修飾](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [方法: 列挙型のメンバーを参照する](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [列挙型を使用する状況](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [定数の概要](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [定数とリテラルのデータ型](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [定数と列挙体](../../../../visual-basic/language-reference/constants-and-enumerations.md)
