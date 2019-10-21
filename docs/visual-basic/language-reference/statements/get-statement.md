---
title: Get ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Get
helpviewer_keywords:
- Get statement [Visual Basic], syntax
- Get statement [Visual Basic]
- properties [Visual Basic], read-only
- read-only properties
- Get keyword [Visual Basic]
- property procedures [Visual Basic], Get statements
ms.assetid: 56b05cdc-bd64-4dfd-bb12-824eacec6f94
ms.openlocfilehash: d76155b8ff29e4f5e9206ae8fc689fa4fcaf3b8c
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581827"
---
# <a name="get-statement"></a>Get ステートメント
プロパティの値を取得するために使用される `Get` プロパティプロシージャを宣言します。  
  
## <a name="syntax"></a>構文  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Get()  
    [ statements ]  
End Get  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`attributelist`|省略可能です。 「[属性リスト](../../../visual-basic/language-reference/statements/attribute-list.md)」を参照してください。|  
|`accessmodifier`|このプロパティの `Get` および `Set` ステートメントのうちの1つで、省略可能です。 次のいずれかの値を指定します。<br /><br /> [保護されている](../../../visual-basic/language-reference/modifiers/protected.md)-   <br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [プライベート](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> 「 [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。|  
|`statements`|省略可能です。 @No__t_0 プロパティプロシージャが呼び出されたときに実行される1つ以上のステートメント。|  
|`End Get`|必須です。 @No__t_0 property プロシージャの定義を終了します。|  
  
## <a name="remarks"></a>Remarks  
 プロパティが `WriteOnly` としてマークされている場合を除き、すべてのプロパティには `Get` プロパティプロシージャが必要です。 @No__t_0 プロシージャは、プロパティの現在の値を返すために使用されます。  
  
 Visual Basic は、プロパティの値を式が要求すると、プロパティの `Get` プロシージャを自動的に呼び出します。  
  
 プロパティ宣言の本体には、プロパティの `Get` と、[プロパティステートメント](../../../visual-basic/language-reference/statements/property-statement.md)と `End Property` ステートメントの間の `Set` プロシージャのみを含めることができます。 これらのプロシージャ以外を格納することはできません。 特に、プロパティの現在の値を格納することはできません。 この値はプロパティの外部に格納する必要があります。これは、プロパティプロシージャの内部に格納する場合、他のプロパティプロシージャがアクセスできないためです。 通常の方法では、プロパティと同じレベルで宣言された[プライベート](../../../visual-basic/language-reference/modifiers/private.md)変数に値を格納します。 @No__t_0 プロシージャは、適用先のプロパティ内で定義する必要があります。  
  
 @No__t_2 ステートメントで `accessmodifier` を使用しない限り、`Get` プロシージャの既定値は、それを含むプロパティのアクセスレベルです。  
  
## <a name="rules"></a>ルール  
  
- **混合アクセスレベル。** 読み取り/書き込みプロパティを定義する場合は、必要に応じて、`Get` または `Set` のいずれかのプロシージャに対して異なるアクセスレベルを指定できますが、両方を指定することはできません。 この場合、プロシージャのアクセスレベルは、プロパティのアクセスレベルよりも制限されている必要があります。 たとえば、プロパティが `Friend` として宣言されている場合は、`Get` プロシージャ `Private` を宣言できますが、`Public` は宣言できません。  
  
     @No__t_0 プロパティを定義する場合、`Get` プロシージャはプロパティ全体を表します。 @No__t_0 に対して異なるアクセスレベルを宣言することはできません。これは、プロパティに2つのアクセスレベルが設定されるためです。  
  
- **戻り値の型。** [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)では、返される値のデータ型を宣言できます。 @No__t_0 プロシージャは、そのデータ型を自動的に返します。 任意のデータ型を指定することも、列挙型、構造体、クラス、またはインターフェイスの名前を指定することもできます。  
  
     @No__t_0 ステートメントで `returntype` が指定されていない場合、プロシージャは `Object` を返します。  
  
## <a name="behavior"></a>動作  
  
- **プロシージャからを返します。** @No__t_0 プロシージャが呼び出し元のコードに戻ると、プロパティ値を要求したステートメント内で実行が続行されます。  
  
     `Get` のプロパティプロシージャは、 [Return ステートメント](../../../visual-basic/language-reference/statements/return-statement.md)を使用するか、プロパティ名に戻り値を割り当てることによって、値を返すことができます。 詳細については、「 [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)」の「戻り値」を参照してください。  
  
     @No__t_0 ステートメントおよび `Return` ステートメントでは、プロパティプロシージャがすぐに終了します。 プロシージャ内の任意の場所で任意の数の `Exit Property` および `Return` ステートメントを使用できます。また、`Exit Property` と `Return` のステートメントを混在させることができます。  
  
- **戻り値。** @No__t_0 プロシージャから値を返すには、プロパティ名に値を割り当てるか、 [Return ステートメント](../../../visual-basic/language-reference/statements/return-statement.md)に含めることができます。 @No__t_0 ステートメントでは、`Get` プロシージャの戻り値が同時に割り当てられ、プロシージャが終了します。  
  
     プロパティ名に値を割り当てずに `Exit Property` を使用する場合、`Get` プロシージャは、プロパティのデータ型の既定値を返します。 詳細については、「 [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)」の「戻り値」を参照してください。  
  
     次の例は、読み取り専用プロパティ `quoteForTheDay` が、プライベート変数 `quoteValue` に保持されている値を返す方法を示しています。  
  
     [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]  
  
     [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]  
  
     [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]  
  
## <a name="example"></a>例  
 次の例では、`Get` ステートメントを使用して、プロパティの値を返します。  
  
 [!code-vb[VbVbalrStatements#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#30)]  
  
## <a name="see-also"></a>関連項目

- [Set ステートメント](../../../visual-basic/language-reference/statements/set-statement.md)
- [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)
- [Exit ステートメント](../../../visual-basic/language-reference/statements/exit-statement.md)
- [クラスとオブジェクト](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [チュートリアル : クラスの定義](../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)
