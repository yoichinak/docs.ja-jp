---
title: "Out (ジェネリック修飾子) (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.VarianceOut
helpviewer_keywords:
- Out keyword [Visual Basic]
- covariance, Out keyword [Visual Basic]
ms.assetid: c4418369-1518-4a46-9a1e-054c61038eca
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4e54504cd65b78846af41692f39899140a6d99b5
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="out-generic-modifier-visual-basic"></a>Out (ジェネリック修飾子) (Visual Basic)
ジェネリック型パラメーターで、`Out`キーワードは、型が共変であることを指定します。  
  
## <a name="remarks"></a>コメント  
 共変性は、ジェネリック パラメーターによって指定された型よりも強い派生型を使用できるようにする機能です。 これにより、バリアント インターフェイスを実装するクラスの暗黙の型変換とデリゲート型の暗黙の型変換が可能となります。  
  
 詳細については、「[共変性と反変性](../../programming-guide/concepts/covariance-contravariance/index.md)」を参照してください。  
  
## <a name="rules"></a>ルール  
 `Out` キーワードは、ジェネリック インターフェイスとデリゲートで使用できます。  
  
 ジェネリック インターフェイスでは、次の条件を満たす場合に型パラメーターを共変として宣言できます。  
  
-   型パラメーターがインターフェイス メソッドの戻り値の型としてのみ使用され、メソッド引数の型として使用されない。  
  
    > [!NOTE]
    >  この規則には例外が 1 つあります。 共変のインターフェイスで反変の汎用デリゲートをメソッド パラメーターとして使用する場合は、共変の型をこのデリゲートのジェネリック型パラメーターとして使用できます。 共変および反変の汎用デリゲートの詳細については、「[デリゲートの分散](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)」および「[Func および Action 汎用デリゲートでの分散の使用](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)」を参照してください。  
  
-   型パラメーターがインターフェイス メソッドのジェネリック制約として使用されない。  
  
 汎用デリゲートの型パラメーター宣言できます共変はメソッドの戻り値の型としてのみ使用し、メソッドの引数は使用されません。  
  
 共変性および反変性は参照型ではサポートされますが、値の型ではサポートされません。  
  
 Visual basic では、デリゲート型を指定せず共変のインターフェイスのイベントを宣言できません。 また、共変のインターフェイスは、クラス、列挙型、または構造体、入れ子ことはできませんが、入れ子になんだインターフェイスを持つことができます。  
  
## <a name="behavior"></a>動作  
 共変の型パラメーターを持つインターフェイスを使用すると、そのインターフェイスのメソッドは、型パラメーターによって指定された型よりも強い派生型を返すことができます。 たとえば、.NET Framework 4 の <xref:System.Collections.Generic.IEnumerable%601> では T 型が共変なので、特別な変換メソッドを使用しなくても `IEnumerabe(Of String)` 型のオブジェクトを `IEnumerable(Of Object)` 型のオブジェクトに割り当てることができます。  
  
 共変のデリゲートには、型は同じでありながらより強い派生ジェネリック型パラメーターを持つ別のデリゲートを割り当てることができます。  
  
## <a name="example"></a>例  
 次の例では、共変のジェネリック インターフェイスを宣言、拡張、および実装する方法を示します。 また、共変のインターフェイスを実装するクラスの暗黙的な変換を使用する方法も示します。  
  
 [!code-vb[vbVarianceKeywords#3](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/out-generic-modifier_1.vb)]  
  
## <a name="example"></a>例  
 次の例では、共変の汎用デリゲートを宣言、インスタンス化、および呼び出す方法を示します。 デリゲート型の暗黙的な変換を使用する方法も示しています。  
  
 [!code-vb[vbVarianceKeywords#4](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/out-generic-modifier_2.vb)]  
  
## <a name="see-also"></a>参照  
 [ジェネリック インターフェイスの分散](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
