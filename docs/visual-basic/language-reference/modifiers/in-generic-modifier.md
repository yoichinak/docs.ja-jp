---
title: In (ジェネリック修飾子) (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.VarianceIn
helpviewer_keywords:
- contravariance, In keyword [Visual Basic]
- In keyword [Visual Basic]
ms.assetid: 59bb13c5-fe96-42b8-8286-86293d1661c5
ms.openlocfilehash: 91a0b9c1188820f8fc466ce1bb123b704fcd94b7
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972515"
---
# <a name="in-generic-modifier-visual-basic"></a>In (ジェネリック修飾子) (Visual Basic)
ジェネリック型パラメーターの `In` キーワードは、型パラメーターが反変であることを指定します。  
  
## <a name="remarks"></a>Remarks  
 反変性は、ジェネリック パラメーターによって指定された型よりも弱い派生型を使用できるようにする機能です。 これにより、バリアント インターフェイスを実装するクラスの暗黙の型変換とデリゲート型の暗黙の型変換が可能となります。  
  
 詳細については、「[共変性と反変性](../../programming-guide/concepts/covariance-contravariance/index.md)」を参照してください。  
  
## <a name="rules"></a>ルール  
 `In` キーワードは、ジェネリック インターフェイスとデリゲートで使用できます。  
  
 メソッド引数の型としてのみ使用され、メソッドの戻り値の型として使用されない場合に、型パラメーターがジェネリック インターフェイスまたはデリゲートで反変を宣言することができます。 `ByRef` パラメーターを共変にすることはできませんまたは反変です。  
  
 共変性と反変性は参照型のサポートされているし、値の型はサポートされていません。  
  
 Visual basic では、デリゲート型を指定せず反変のインターフェイスのイベントを宣言できません。 また、反変のインターフェイスは、クラス、列挙型、または構造体、入れ子にできませんが、インターフェイスを入れ子にできます。  
  
## <a name="behavior"></a>動作  
 反変の型パラメーターを持つインターフェイスを使用すると、そのインターフェイスのメソッドは、インターフェイス型パラメーターによって指定された型よりも弱い派生型の引数を受け取ることができます。 たとえば、.NET Framework 4 の <xref:System.Collections.Generic.IComparer%601> インターフェイスでは T 型が反変なので、`Person` が `Employee` を継承する場合、特別な変換メソッドを使用しなくても `IComparer(Of Person)` 型のオブジェクトを `IComparer(Of Employee)` 型のオブジェクトに割り当てることができます。  
  
 反変のデリゲートには、型は同じでありながらより弱い派生ジェネリック型パラメーターを持つ別のデリゲートを割り当てることができます。  
  
## <a name="example"></a>例  
 次の例では、反変のジェネリック インターフェイスを宣言、拡張、および実装する方法を示します。 また、このインターフェイスを実装するクラスの暗黙的な変換を使用する方法も示します。  
  
 [!code-vb[vbVarianceKeywords#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#1)]  
  
## <a name="example"></a>例  
 次の例では、反変の汎用デリゲートを宣言、インスタンス化、および呼び出す方法を示します。 また、デリゲート型を暗黙的に変換する方法も示します。  
  
 [!code-vb[vbVarianceKeywords#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#2)]  
  
## <a name="see-also"></a>関連項目
- [ジェネリック インターフェイスの分散](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
