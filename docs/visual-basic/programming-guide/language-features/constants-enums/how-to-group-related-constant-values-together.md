---
title: '方法: グループ関連する定数値 (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
ms.openlocfilehash: 63475487c8a35f5b306b28d4e7097324bef00d85
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977826"
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a>方法: グループ関連する定数値 (Visual Basic)
列挙型は、関連する定数をグループ化する最善の方法です。 持つ列挙体を作成する、`Enum`クラスまたはモジュールの宣言セクション内のステートメント。 詳細については、「[方法 :列挙型を宣言](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)します。  
  
### <a name="to-group-related-constant-values"></a>グループに関連する定数値  
  
1.  コードのアクセス レベルを含む宣言を記述、`Enum`キーワード、および有効な名前。 この例で作成、`Private`列挙型、`temperatureValues`します。  
  
     [!code-vb[VbEnumsTask#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#21)]  
  
2.  列挙体の定数を定義します。 この例で作成、`Public`列挙`temperatureValues`し、その値を割り当てます。  
  
     [!code-vb[VbEnumsTask#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#1)]  
  
## <a name="see-also"></a>関連項目
- [列挙型と名前の修飾](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [方法: 列挙体のメンバーを参照してください。](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [列挙型を使用する状況](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [定数の概要](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [定数とリテラルのデータ型](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [定数と列挙体](../../../../visual-basic/language-reference/constants-and-enumerations.md)
