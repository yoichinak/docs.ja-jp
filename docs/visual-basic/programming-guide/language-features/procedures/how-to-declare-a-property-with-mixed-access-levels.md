---
title: '方法: 混合アクセス レベル (Visual Basic) を持つプロパティを宣言します。'
ms.date: 07/20/2015
helpviewer_keywords:
- access levels [Visual Basic], properties
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- mixed access levels
- Visual Basic code, properties
- properties [Visual Basic], access levels
- Property statement [Visual Basic], declaring mixed access levels
ms.assetid: fdbb2d97-279a-4956-b26c-cbdfbc34915a
ms.openlocfilehash: e899b57e02f492b0e4909aca84c069e5b7688618
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59339815"
---
# <a name="how-to-declare-a-property-with-mixed-access-levels-visual-basic"></a>方法: 混合アクセス レベル (Visual Basic) を持つプロパティを宣言します。
場合は、`Get`と`Set`手順が異なるアクセス レベルのプロパティについてでより制限の緩やかなレベルを使用することができます、`Property`ステートメントといずれかより制限の厳しいレベル、`Get`または`Set`ステートメント。 プロパティの値を取得できるコードの特定の部分と値を変更することができるコードの他の特定の部分を使う場合は、プロパティに混合アクセス レベルを使用します。  
  
 アクセス レベルの詳細については、次を参照してください。[アクセス レベルを Visual Basic で](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)します。  
  
### <a name="to-declare-a-property-with-mixed-access-levels"></a>混合アクセス レベルを持つプロパティを宣言するには  
  
1. 通常の方法でプロパティを宣言しより制限の少ないアクセス レベルを指定 (など`Public`) で、`Property`ステートメント。  
  
2. いずれかを宣言、`Get`または`Set`より制限の厳しいアクセス レベルを指定する手順 (など`Friend`)。  
  
3. その他のプロパティ プロシージャでは、アクセス レベルを指定しません。 アクセス レベルで宣言されていると想定して、`Property`ステートメント。 プロパティ プロシージャの 1 つだけにアクセスを制限することができます。  
  
     [!code-vb[VbVbcnProcedures#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#10)]  
  
     前の例では、`Get`手順では、同じ`Protected`プロパティ自体としてのアクセス中に、`Set`手順では`Private`アクセス。 派生したクラス`employee`読み取ることができます、`salary`値のみが、`employee`クラスで設定できます。  
  
## <a name="see-also"></a>関連項目

- [プロシージャ](./index.md)
- [Property プロシージャ](./property-procedures.md)
- [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)
- [Property ステートメント](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Visual Basic でのプロパティと変数の違い](./differences-between-properties-and-variables.md)
- [方法: プロパティを作成します。](./how-to-create-a-property.md)
- [方法: プロパティ プロシージャを呼び出す](./how-to-call-a-property-procedure.md)
- [方法: 宣言し、Visual Basic では、既定のプロパティを呼び出す](./how-to-declare-and-call-a-default-property.md)
- [方法: プロパティに値を格納します。](./how-to-put-a-value-in-a-property.md)
- [方法: プロパティから値を取得します。](./how-to-get-a-value-from-a-property.md)
