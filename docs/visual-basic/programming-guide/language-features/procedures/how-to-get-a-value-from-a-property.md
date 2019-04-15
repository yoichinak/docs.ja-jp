---
title: '方法: プロパティ (Visual Basic) から値を取得します。'
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
ms.openlocfilehash: 5e2676a0880092a78405fe5dafa0469161b85610
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59302934"
---
# <a name="how-to-get-a-value-from-a-property-visual-basic"></a>方法: プロパティ (Visual Basic) から値を取得します。
プロパティの値を取得するには、式の中で、プロパティ名を含めます。  
  
 プロパティの`Get`プロシージャが、値を取得しますが、明示的に呼び出さない場合、名前でします。 変数を使用する場合と同様に、プロパティを使用するとします。 Visual Basic では、プロパティのプロシージャ呼び出しを行います。  
  
### <a name="to-retrieve-a-value-from-a-property"></a>プロパティの値を取得するには  
  
1. 式、変数名を使用する場合と同じ方法でプロパティ名を使用します。 プロパティを使用する変数または定数を使用する任意の場所。  
  
     - または -  
  
     等号の後、プロパティ名を使用して (`=`)、代入ステートメントにサインインします。  
  
     次の例は、Visual Basic の値を読み取ります`Now`プロパティ、暗黙的に呼び出して、`Get`プロシージャ。  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2. プロパティが引数を受け取る場合は、次の引数リストを囲むためにかっこによるプロパティ名。 引数がない場合、かっこを省略することができます。  
  
3. コンマで区切り、かっこ内の引数リストで、引数を配置します。 プロパティが、対応するパラメーターを定義するのと同じ順序で引数を指定してください。  
  
 プロパティの値が、式、変数と同様に参加する定数または変数または代入ステートメントの左側にあるプロパティに格納されます。  
  
## <a name="see-also"></a>関連項目

- [手順](./index.md)
- [プロパティ プロシージャ](./property-procedures.md)
- [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)
- [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Visual Basic のプロパティと変数の違い](./differences-between-properties-and-variables.md)
- [方法: プロパティを作成する](./how-to-create-a-property.md)
- [方法: 複数のアクセス レベルを持つプロパティを宣言する](./how-to-declare-a-property-with-mixed-access-levels.md)
- [方法: プロパティ プロシージャを呼び出す](./how-to-call-a-property-procedure.md)
- [方法: 宣言し、Visual Basic では、既定のプロパティを呼び出す](./how-to-declare-and-call-a-default-property.md)
- [方法: プロパティに値を格納する](./how-to-put-a-value-in-a-property.md)
