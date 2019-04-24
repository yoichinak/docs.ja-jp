---
title: MustInherit (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- MustInherit
- vb.MustInherit
helpviewer_keywords:
- classes [Visual Basic], abstract
- MustInherit classes [Visual Basic], MustInherit keyword
- abstract classes [Visual Basic], MustInherit class
- MustInherit keyword [Visual Basic]
ms.assetid: b8f05185-90e3-4dd7-adc2-90d852fab5b4
ms.openlocfilehash: 0bda03d3c01356317fbcc56d44199ff4f9484b5b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58816565"
---
# <a name="mustinherit-visual-basic"></a>MustInherit (Visual Basic)
クラスを基底クラスとしてのみ使用できることと、オブジェクトを直接作成できないことを指定します。  
  
## <a name="remarks"></a>Remarks  
 目的を*基本クラス*(とも呼ばれます、*抽象クラス*) それから派生したすべてのクラスに共通した機能を定義することです。 これにより、派生クラスが共通の要素を再定義する必要がなくなります。 場合によっては、この共通の機能が、使用可能なオブジェクトを作成するのに十分な完了していませんし、各派生クラスが不足している機能を定義します。 このような場合は、派生クラスからのみオブジェクトを作成、使用側コードをします。 使用する`MustInherit`でこれを強制する基本クラス。  
  
 別の用途を`MustInherit`クラスは、関連するクラスのセットに変数を制限します。 基本クラスを定義し、そこからこれらのすべての関連するクラスを派生できます。 基本クラスは、すべての派生クラスに共通の機能を提供する必要はありませんが、その変数に値を割り当てるためのフィルターとして使用できます。 使用側コードでは、基底クラスとしての変数を宣言する場合に、Visual Basic を使用すると、派生クラスの 1 つのオブジェクトのみをその変数に代入できます。  
  
 .NET Framework では、いくつかを定義します`MustInherit`クラスは、それらの間で<xref:System.Array>、 <xref:System.Enum>、および<xref:System.ValueType>します。 <xref:System.ValueType> 変数を制限する基底クラスの例に示します。 すべての値の型から派生<xref:System.ValueType>します。 として変数を宣言する場合<xref:System.ValueType>、その変数に値型のみを割り当てることができます。  
  
## <a name="rules"></a>ルール  
  
-   **宣言コンテキスト。** 使用することができます`MustInherit`でのみ、`Class`ステートメント。  
  
-   **結合された修飾子。** 指定することはできません`MustInherit`と共に`NotInheritable`同じ宣言内。  
  
## <a name="example"></a>例  
 次の例は、強制的な継承と強制的なオーバーライドを示しています。 基本クラス`shape`変数を定義します`acrossLine`します。 クラスは、`circle`と`square`から派生`shape`します。 定義を継承`acrossLine`、関数を定義する必要がありますが、`area`計算は図形の種類ごとに異なるためです。  
  
 [!code-vb[VbVbalrKeywords#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#2)]  
  
 宣言できます`shape1`と`shape2`型`shape`します。 オブジェクトを作成することはできませんただし、`shape`関数の機能がないため`area`がマークされていると`MustInherit`します。  
  
 として宣言されているため、 `shape`、変数`shape1`と`shape2`派生クラスからオブジェクトに制限される`circle`と`square`します。 Visual Basic はできません、他のオブジェクトをこれらの変数に割り当てることにより、タイプ セーフの高レベル。  
  
## <a name="usage"></a>使用法  
 `MustInherit`修飾子は、このコンテキストで使用できます。  
  
 [Class ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)  
  
## <a name="see-also"></a>関連項目

- [Inherits ステートメント](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [キーワード](../../../visual-basic/language-reference/keywords/index.md)
- [継承の基本](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
