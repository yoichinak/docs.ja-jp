---
title: '方法: プロパティ (Visual Basic) で、値を入力します。'
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
ms.openlocfilehash: ee2449ff905bfdacaeeee4cc244db1ce50e00104
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824309"
---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a>方法: プロパティ (Visual Basic) で、値を入力します。
プロパティに値を格納するには、代入ステートメントの左側にあるプロパティ名を置きます。  
  
 プロパティの`Set`プロシージャに、値が格納されますが、明示的に呼び出さない場合、名前でします。 変数を使用する場合と同様に、プロパティを使用するとします。 Visual Basic では、プロパティのプロシージャ呼び出しを行います。  
  
### <a name="to-store-a-value-in-a-property"></a>プロパティに値を格納するには  
  
1.  代入ステートメントの左側にあるプロパティ名を使用します。  
  
     次の例では、Visual Basic の値を設定する`TimeOfDay`プロパティ、正午を暗黙的に呼び出して、`Set`プロシージャ。  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2.  プロパティが引数を受け取る場合は、次の引数リストを囲むためにかっこによるプロパティ名。 引数がない場合、かっこを省略することができます。  
  
3.  コンマで区切り、かっこ内の引数リストで、引数を配置します。 プロパティが、対応するパラメーターを定義するのと同じ順序で引数を指定してください。  
  
4.  代入ステートメントの右側にある生成された値は、プロパティに格納されます。  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>
- [Property プロシージャ](./property-procedures.md)
- [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)
- [Property ステートメント](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Visual Basic でのプロパティと変数の違い](./differences-between-properties-and-variables.md)
- [方法: プロパティを作成します。](./how-to-create-a-property.md)
- [方法: 混合アクセス レベルを持つプロパティを宣言します。](./how-to-declare-a-property-with-mixed-access-levels.md)
- [方法: プロパティ プロシージャを呼び出す](./how-to-call-a-property-procedure.md)
- [方法: 宣言し、Visual Basic では、既定のプロパティを呼び出す](./how-to-declare-and-call-a-default-property.md)
- [方法: プロパティから値を取得します。](./how-to-get-a-value-from-a-property.md)
