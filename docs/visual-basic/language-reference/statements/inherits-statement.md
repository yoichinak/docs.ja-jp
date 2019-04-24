---
title: Inherits ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Inherits
- Inherits
helpviewer_keywords:
- Inherits statement [Visual Basic]
- Inherits statement [Visual Basic], syntax
ms.assetid: 9e6fe042-9af3-4341-8093-fc3537770cf2
ms.openlocfilehash: 5ab90e44e2809c1e71d7f100970b7be73af4a732
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58817098"
---
# <a name="inherits-statement"></a>Inherits ステートメント
現在のクラスまたは属性、変数、プロパティ、プロシージャ、およびイベントを別のクラスまたはインターフェイスのセットから継承するインターフェイスとします。  
  
## <a name="syntax"></a>構文  
  
```  
Inherits basetypenames  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`basetypenames`|必須。 このクラスの派生元クラスの名前。<br /><br /> - または -<br /><br /> このインターフェイスの派生元のインターフェイスの名前。 コンマを使用して、複数の名前を区切ります。|  
  
## <a name="remarks"></a>Remarks  
 使用する場合、`Inherits`ステートメントはクラスまたはインターフェイスの定義では、最初の空白、コメント以外の次の行である必要があります。 すぐに従ってください、`Class`または`Interface`ステートメント。  
  
 使用することができます`Inherits`クラスまたはインターフェイスでのみです。 つまり、継承の宣言のコンテキストがソース ファイル、名前空間、構造体、モジュール、プロシージャ、またはブロックすることはできません。  
  
## <a name="rules"></a>ルール  
  
-   **クラスの継承します。** クラスで使用する場合、`Inherits`ステートメントでは、1 つだけの基本クラスを指定することができます。  
  
     クラスは、その中に入れ子になったクラスから継承できません。  
  
-   **インターフェイスの継承します。** インターフェイスで使用する場合、`Inherits`ステートメントでは、1 つまたは複数の基底インターフェイスを指定することができます。 同じ名前のメンバーが定義されている場合でも、2 つのインターフェイスから継承できます。 これを行う場合、実装コードは、実装しています。 どのメンバーを指定する名前の修飾を使用する必要があります。  
  
     インターフェイスより制限の厳しいアクセス レベルを持つ別のインターフェイスから継承できません。 たとえば、`Public`インターフェイスから継承することはできません、`Friend`インターフェイス。  
  
     インターフェイスは、内部に入れ子になったインターフェイスから継承できません。  
  
 .NET Framework におけるクラス継承の例は、<xref:System.ArgumentException>から継承されるクラス、<xref:System.SystemException>クラス。 これにより、<xref:System.ArgumentException>すべての定義済みプロパティとなどのシステム例外によって必要な手順、<xref:System.Exception.Message%2A>プロパティおよび<xref:System.Exception.ToString%2A>メソッド。  
  
 .NET Framework のインターフェイスの継承の例は、<xref:System.Collections.ICollection>から継承するインターフェイスを<xref:System.Collections.IEnumerable>インターフェイス。 これにより、<xref:System.Collections.ICollection>コレクションを走査するために必要な列挙子の定義を継承します。  
  
## <a name="example"></a>例  
 次の例では、`Inherits`クラスの名前付け方法を表示するステートメント`thisClass`という名前の基本クラスのすべてのメンバーを継承できる`anotherClass`します。  
  
 [!code-vb[VbVbalrStatements#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#37)]  
  
## <a name="example"></a>例  
 次の例では、複数のインターフェイスの継承を示します。  
  
 [!code-vb[VbVbalrStatements#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#38)]  
  
 という名前のインターフェイス`thisInterface`内のすべての定義が含まれています、 <xref:System.IComparable>、 <xref:System.IDisposable>、および<xref:System.IFormattable>継承されたメンバーでは、それぞれ 2 つのオブジェクトの種類に固有の比較を解放するインターフェイスには、リソースが割り当てられますをオブジェクトとしての値を表現して、`String`します。 実装するクラス`thisInterface`すべて基底インターフェイスのすべてのメンバーを実装する必要があります。  
  
## <a name="see-also"></a>関連項目

- [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)
- [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [クラスとオブジェクト](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [継承の基本](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [インターフェイス](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
