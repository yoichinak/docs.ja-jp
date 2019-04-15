---
title: '方法: 宣言し、Visual Basic では、既定のプロパティを呼び出す'
ms.date: 07/20/2015
helpviewer_keywords:
- defaults [Visual Basic], properties
- properties [Visual Basic], default
- procedures [Visual Basic], defining
- default properties [Visual Basic], in Visual Basic
- Visual Basic code, procedures
- Visual Basic code, properties
- default properties
ms.assetid: 68b4026e-09ef-4613-808e-f6287494ff63
ms.openlocfilehash: 9ca9a0ccdac3ac13429928233a0c09d58427ce74
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59295641"
---
# <a name="how-to-declare-and-call-a-default-property-in-visual-basic"></a>方法: 宣言し、Visual Basic では、既定のプロパティを呼び出す
A*プロパティの既定*クラスまたは構造体のプロパティで、指定しなくても、コードにアクセスできます。 呼び出し元のコードは、クラスまたは構造体がないプロパティ、およびコンテキスト プロパティへのアクセスを許可、存在する場合、Visual Basic がそのクラスまたは構造体の既定のプロパティにアクセスを解決します。  
  
 クラスまたは構造体が多くて 1 つの既定のプロパティ。 ただし、既定プロパティはオーバー ロードし、その 1 つ以上のバージョンがあります。  
  
 詳細については、次を参照してください。[既定](../../../../visual-basic/language-reference/modifiers/default.md)します。  
  
### <a name="to-declare-a-default-property"></a>既定のプロパティを宣言するには  
  
1. 通常の方法でプロパティを宣言します。 指定しない、`Shared`または`Private`キーワード。  
  
2. 含める、`Default`プロパティ宣言でキーワード。  
  
3. プロパティの少なくとも 1 つのパラメーターを指定します。 少なくとも 1 つの引数を受け取らない既定のプロパティを定義することはできません。  
  
     [!code-vb[VbVbcnProcedures#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#17)]  
  
### <a name="to-call-a-default-property"></a>既定のプロパティを呼び出す  
  
1. それを含むクラスまたは構造体の型の変数を宣言します。  
  
     [!code-vb[VbVbcnProcedures#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#16)]  
  
2. プロパティ名を通常は式の中で単独で変数名を使用します。  
  
     [!code-vb[VbVbcnProcedures#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#21)]  
  
3. 引数リストをかっこで、変数名に従ってください。 既定のプロパティは、少なくとも 1 つの引数を受け取る必要があります。  
  
     [!code-vb[VbVbcnProcedures#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#20)]  
  
4. プロパティの既定値を取得するには、次の等値または式の中で、引数リストでという名前の変数を使用 (`=`)、代入ステートメントにサインインします。  
  
     [!code-vb[VbVbcnProcedures#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#15)]  
  
5. プロパティの既定値を設定するには、代入ステートメントの左側にある、引数のリストを持つという名前の変数を使用します。  
  
     [!code-vb[VbVbcnProcedures#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#14)]  
  
6. 他のプロパティにアクセスするための作業と同様、という名前の変数と共に既定のプロパティ名を必ず指定することができます。  
  
     [!code-vb[VbVbcnProcedures#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#19)]  
  
## <a name="example"></a>例  
 次の例では、クラスの既定のプロパティを宣言します。  
  
 [!code-vb[VbVbcnProcedures#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#12)]  
  
## <a name="example"></a>例  
 次の例では、既定のプロパティを呼び出す方法`myProperty`クラス`class1`します。 次の 3 つの代入ステートメントで値を格納する`myProperty`、および<xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>呼び出しは、値を読み取ります。  
  
 [!code-vb[VbVbcnProcedures#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#13)]  
  
 既定のプロパティの最も一般的な用途は、<xref:Microsoft.VisualBasic.Collection.Item%2A>さまざまなコレクション クラスのプロパティ。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 既定のプロパティは、ソース コードの文字のわずかな低下につながるが行えるように、コードが読みにくくします。 クラスまたは構造体名への参照を行うときに、呼び出し元のコードがクラスまたは構造に習熟していない場合にすることはできません特定その参照が、クラスまたは構造体自体、または既定のプロパティにアクセスするかどうか。 これについては、コンパイラ エラーまたはランタイム ロジックの微妙なエラーにつながります。  
  
 常を使用して既定のプロパティのエラーの可能性を低くことができますやや、 [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)コンパイラ型チェックを設定する`On`します。  
  
 使用して、定義済みのクラスまたは構造体コードで判断する必要があります、既定のプロパティがあるかどうかであればしようとしている場合、名前は。  
  
 このような短所のためには、既定のプロパティを定義しないを検討してください。 コードを読みやすくは必要がありますも常に明示的に参照するすべてのプロパティを検討してくださいも既定のプロパティ。  
  
## <a name="see-also"></a>関連項目

- [プロパティ プロシージャ](./property-procedures.md)
- [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)
- [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md)
- [既定値](../../../../visual-basic/language-reference/modifiers/default.md)
- [Visual Basic のプロパティと変数の違い](./differences-between-properties-and-variables.md)
- [方法: プロパティを作成する](./how-to-create-a-property.md)
- [方法: 複数のアクセス レベルを持つプロパティを宣言する](./how-to-declare-a-property-with-mixed-access-levels.md)
- [方法: プロパティ プロシージャを呼び出す](./how-to-call-a-property-procedure.md)
- [方法: プロパティに値を格納する](./how-to-put-a-value-in-a-property.md)
- [方法: プロパティから値を取得する](./how-to-get-a-value-from-a-property.md)
