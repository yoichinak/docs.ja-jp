---
title: Object Data Type
ms.date: 07/20/2015
f1_keywords:
- vb.Object
- vb.Variant
helpviewer_keywords:
- object variables [Visual Basic], Object type
- data types [Visual Basic], assigning
- Object data type
- Object data type [Visual Basic], reference
ms.assetid: 61ea4a7c-3b3d-48d4-adc4-eacfa91779b2
ms.openlocfilehash: 2ccb9b69b865c259d078ed9642d63c7f83514756
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343966"
---
# <a name="object-data-type"></a>Object Data Type

Holds addresses that refer to objects. You can assign any reference type (string, array, class, or interface) to an `Object` variable. An `Object` variable can also refer to data of any value type (numeric, `Boolean`, `Char`, `Date`, structure, or enumeration).

## <a name="remarks"></a>Remarks

The `Object` data type can point to data of any data type, including any object instance your application recognizes. Use `Object` when you do not know at compile time what data type the variable might point to.

The default value of `Object` is `Nothing` (a null reference).

## <a name="data-types"></a>データの種類

You can assign a variable, constant, or expression of any data type to an `Object` variable. To determine the data type an `Object` variable currently refers to, you can use the <xref:System.Type.GetTypeCode%2A> method of the <xref:System.Type?displayProperty=nameWithType> class. 次に例を示します。

```vb
Dim myObject As Object
' Suppose myObject has now had something assigned to it.
Dim datTyp As Integer
datTyp = Type.GetTypeCode(myObject.GetType())
```

The `Object` data type is a reference type. However, Visual Basic treats an `Object` variable as a value type when it refers to data of a value type.

## <a name="storage"></a>記憶域

Whatever data type it refers to, an `Object` variable does not contain the data value itself, but rather a pointer to the value. It always uses four bytes in computer memory, but this does not include the storage for the data representing the value of the variable. Because of the code that uses the pointer to locate the data, `Object` variables holding value types are slightly slower to access than explicitly typed variables.

## <a name="programming-tips"></a>プログラミングのヒント

- **Interop Considerations.** If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that pointer types in other environments are not compatible with the Visual Basic `Object` type.

- **パフォーマンス。** A variable you declare with the `Object` type is flexible enough to contain a reference to any object. However, when you invoke a method or property on such a variable, you always incur *late binding* (at run time). To force *early binding* (at compile time) and better performance, declare the variable with a specific class name, or cast it to the specific data type.

  When you declare an object variable, try to use a specific class type, for example <xref:System.OperatingSystem>, instead of the generalized `Object` type. You should also use the most specific class available, such as <xref:System.Windows.Forms.TextBox> instead of <xref:System.Windows.Forms.Control>, so that you can access its properties and methods. You can usually use the **Classes** list in the **Object Browser** to find available class names.

- **Widening.** All data types and all reference types widen to the `Object` data type. This means you can convert any type to `Object` without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.

  However, if you convert between value types and `Object`, Visual Basic performs operations called *boxing* and *unboxing*, which make execution slower.

- **Type Characters.** `Object` has no literal type character or identifier type character.

- **Framework Type.** The corresponding type in the .NET Framework is the <xref:System.Object?displayProperty=nameWithType> class.

## <a name="example"></a>例

The following example illustrates an `Object` variable pointing to an object instance.

```vb
Dim objDb As Object
Dim myCollection As New Collection()
' Suppose myCollection has now been populated.
objDb = myCollection.Item(1)
```

## <a name="see-also"></a>関連項目

- <xref:System.Object>
- [データの種類](../../../visual-basic/language-reference/data-types/index.md)
- [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [データ型の有効な使用方法](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [方法: 2 つのオブジェクトが関連しているかどうかを決める](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [方法: 2 つのオブジェクトが同一であるかどうか判別する](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
