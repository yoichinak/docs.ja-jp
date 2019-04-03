---
title: '方法: プロパティ (Visual Basic) を作成します。'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, properties
- properties [Visual Basic]
ms.assetid: 4d229712-6be8-4c5c-bac5-06995ce9185a
ms.openlocfilehash: 3e3f1168a983b2fa608cbadffba0531afef7c92b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816850"
---
# <a name="how-to-create-a-property-visual-basic"></a>方法: プロパティ (Visual Basic) を作成します。
プロパティの定義との間を囲む、`Property`ステートメントおよび`End Property`ステートメント。 この定義内で定義、 `Get` 、プロシージャ、`Set`プロシージャ、またはその両方です。 プロパティのすべてのコードが、これらのプロシージャ内に存在します。  
  
 `Get`プロパティの値を取得し、`Set`プロシージャが値を格納します。 読み取り/書き込みアクセス権のプロパティを設定する場合、両方の手順を定義する必要があります。 読み取り専用プロパティを定義するのみ`Get`、書き込み専用プロパティで定義することのみ`Set`します。  
  
### <a name="to-create-a-property"></a>プロパティを作成するには  
  
1.  任意のプロパティまたはプロシージャの外側を使用して、 [Property ステートメント](../../../../visual-basic/language-reference/statements/property-statement.md)、その後に、`End Property`ステートメント。  
  
2.  次のプロパティは、パラメーターを受け取る場合、`Property`パラメーター リストをかっこで、プロシージャの名前を持つキーワード。  
  
3.  かっこの後に、`As`プロパティの値のデータ型を指定する句。 書き込み専用プロパティの場合でもデータ型を指定する必要があります。  
  
4.  追加`Get`と`Set`プロシージャに、必要に応じて。 次の手順を参照してください。  
  
### <a name="to-create-a-get-procedure-that-retrieves-a-property-value"></a>プロパティの値を取得する Get プロシージャを作成するには  
  
1.  間、`Property`と`End Property`、ステートメントの記述、 [Get ステートメント](../../../../visual-basic/language-reference/statements/get-statement.md)、その後に、`End Get`ステートメント。 パラメーターを定義する必要はありません、`Get`プロシージャ。  
  
2.  間で、プロパティの値を取得するコードのステートメントを配置、`Get`と`End Get`ステートメント。 その他の計算やデータ操作を生成して、プロパティの値を返すだけでなく、このコードを含めることができます。  
  
3.  使用して、`Return`ステートメントを呼び出し元のコードに、プロパティの値を返します。  
  
 記述する必要があります、`Get`プロシージャおよび読み取り専用プロパティの読み取り/書き込みプロパティ。 定義する必要があります、`Get`書き込み専用プロパティ プロシージャをします。  
  
### <a name="to-create-a-set-procedure-that-writes-a-propertys-value"></a>プロパティの値を書き込みます Set プロシージャを作成するには  
  
1.  間、`Property`と`End Property`、ステートメントの記述、 [Set ステートメント](../../../../visual-basic/language-reference/statements/set-statement.md)、その後に、`End Set`ステートメント。  
  
2.  `Set`ステートメントでは、以下の`Set`パラメーター リストをかっこで囲まれたキーワード。 このパラメーターの一覧には、呼び出し元のコードに渡される値の少なくとも値パラメーターを含める必要があります。 この値のパラメーターの既定の名前は`Value`、該当する場合は、別の名前を使用することができます。 データは、型、プロパティ自体と同じ値のパラメーターが必要です。  
  
3.  間でプロパティに値を格納するコードのステートメントを配置、`Set`と`End Set`ステートメント。 このコードは、他の計算や検査して、プロパティの値を格納するだけでなくデータ操作を含めることができます。  
  
4.  値パラメーターを使用して、呼び出し元のコードによって提供される値をそのまま使用します。 この値は、代入ステートメントに直接格納するかを格納する内部値を計算する式で使用します。  
  
 記述する必要があります、`Set`プロシージャの読み取り/書き込みプロパティおよび書き込み専用プロパティ。 定義する必要があります、`Set`読み取り専用プロパティ プロシージャをします。  
  
## <a name="example"></a>例  
 次の例では、2 つの構成名、名、および、最後の名前と完全な名前を格納する読み取り/書き込みプロパティを作成します。 呼び出し元のコードを読み取るとき`fullName`、`Get`プロシージャは、2 つの構成名を結合し、完全な名前を返します。 呼び出し元のコードによって、新しい完全な名前を割り当てられるとき、`Set`プロシージャは、それを 2 つの部分に分割しようと試みます。 場所が見つからない場合すべて最初の名前として格納します。  
  
 [!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]  
  
 次の例では、一般的なプロパティ プロシージャの呼び出し`fullName`します。 最初の呼び出しは、プロパティの値を設定し、2 番目の呼び出しでは、それを取得します。  
  
 [!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>関連項目

- [プロシージャ](./index.md)
- [Property プロシージャ](./property-procedures.md)
- [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)
- [Visual Basic でのプロパティと変数の違い](./differences-between-properties-and-variables.md)
- [方法: 混合アクセス レベルを持つプロパティを宣言します。](./how-to-declare-a-property-with-mixed-access-levels.md)
- [方法: プロパティ プロシージャを呼び出す](./how-to-call-a-property-procedure.md)
- [方法: 宣言し、Visual Basic では、既定のプロパティを呼び出す](./how-to-declare-and-call-a-default-property.md)
- [方法: プロパティに値を格納します。](./how-to-put-a-value-in-a-property.md)
- [方法: プロパティから値を取得します。](./how-to-get-a-value-from-a-property.md)
