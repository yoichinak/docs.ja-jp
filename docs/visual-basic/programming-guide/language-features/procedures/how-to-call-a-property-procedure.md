---
title: '方法: プロパティ プロシージャ (Visual Basic) を呼び出す'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], property procedures
- procedure calls [Visual Basic], property procedures
ms.assetid: 96bc4d74-d9c3-4b7a-954d-58ac8553cd94
ms.openlocfilehash: d05c1b63f5567ade9935f80ecc022eb4840e0af0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59318755"
---
# <a name="how-to-call-a-property-procedure-visual-basic"></a>方法: プロパティ プロシージャ (Visual Basic) を呼び出す
プロパティ プロシージャを呼び出すには、「プロパティ値を保存するか値を取得します。 プロパティは変数にアクセスする同じ方法でアクセスします。  
  
 プロパティの`Set`プロシージャは、値を格納し、その`Get`プロシージャが値を取得します。 ただし、明示的に呼び出さないこれらのプロシージャ名で。 格納または変数の値を取得すると同様、代入ステートメントまたは式のプロパティを使用します。 Visual Basic では、プロパティのプロシージャ呼び出しを行います。  
  
### <a name="to-call-a-propertys-get-procedure"></a>プロパティの Get プロシージャを呼び出す  
  
1. 式、変数名を使用する場合と同じ方法でプロパティ名を使用します。 プロパティを使用する変数または定数を使用する任意の場所。  
  
     - または -  
  
     等号の後、プロパティ名を使用して (`=`)、代入ステートメントにサインインします。  
  
     次の例の値を読み取る、<xref:Microsoft.VisualBasic.DateAndTime.Now%2A>プロパティ、暗黙的に呼び出すその`Get`プロシージャ。  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2. プロパティが引数を受け取る場合は、次の引数リストを囲むためにかっこによるプロパティ名。 引数がない場合、かっこを省略することができます。  
  
3. コンマで区切り、かっこ内の引数リストで、引数を配置します。 プロパティが、対応するパラメーターを定義するのと同じ順序で引数を指定してください。  
  
 プロパティの値が、式、変数と同様に参加する定数または変数または代入ステートメントの左側にあるプロパティに格納されます。  
  
### <a name="to-call-a-propertys-set-procedure"></a>プロパティを呼び出すための Set でプロシージャ  
  
1. 代入ステートメントの左側にあるプロパティ名を使用します。  
  
     次の例の値の設定、<xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>プロパティ、暗黙的に呼び出して、`Set`プロシージャ。  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2. プロパティが引数を受け取る場合は、次の引数リストを囲むためにかっこによるプロパティ名。 引数がない場合、かっこを省略することができます。  
  
3. コンマで区切り、かっこ内の引数リストで、引数を配置します。 プロパティが、対応するパラメーターを定義するのと同じ順序で引数を指定してください。  
  
 代入ステートメントの右側にある生成された値は、プロパティに格納されます。  
  
## <a name="see-also"></a>関連項目

- [Property プロシージャ](./property-procedures.md)
- [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)
- [Property ステートメント](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Visual Basic でのプロパティと変数の違い](./differences-between-properties-and-variables.md)
- [方法: プロパティを作成します。](./how-to-create-a-property.md)
- [方法: 混合アクセス レベルを持つプロパティを宣言します。](./how-to-declare-a-property-with-mixed-access-levels.md)
- [方法: 宣言し、Visual Basic では、既定のプロパティを呼び出す](./how-to-declare-and-call-a-default-property.md)
- [方法: プロパティに値を格納します。](./how-to-put-a-value-in-a-property.md)
- [方法: プロパティから値を取得します。](./how-to-get-a-value-from-a-property.md)
- [Get ステートメント](../../../../visual-basic/language-reference/statements/get-statement.md)
- [Set ステートメント](../../../../visual-basic/language-reference/statements/set-statement.md)
