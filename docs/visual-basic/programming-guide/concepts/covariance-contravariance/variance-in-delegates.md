---
title: デリゲート (Visual Basic) の分散
ms.date: 07/20/2015
ms.assetid: 38e9353f-74f8-4211-a8f0-7a495414df4a
ms.openlocfilehash: 6d341c7c2b5adeebcafc5b0787b132ab6bd57e41
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61787232"
---
# <a name="variance-in-delegates-visual-basic"></a>デリゲート (Visual Basic) の分散

.NET framework 3.5 には、すべてのデリゲートでのデリゲート型をメソッド シグネチャを一致させる分散サポートが導入されました。C#および Visual Basic です。 つまり、シグネチャが一致するメソッドだけでなく、デリゲート型で指定された型よりも強い派生型を返す (共変性) メソッドや、弱い派生型のパラメーターを受け取る (反変性) メソッドを、デリゲートに割り当てることができます。 これには、汎用デリゲートと非汎用デリゲートの両方が含まれます。

たとえば、次のコードについて考えます。このコードには、2 つのクラスと、汎用と非汎用の 2 つのデリゲートが含まれています。

```vb
Public Class First
End Class

Public Class Second
    Inherits First
End Class

Public Delegate Function SampleDelegate(ByVal a As Second) As First
Public Delegate Function SampleGenericDelegate(Of A, R)(ByVal a As A) As R
```

`SampleDelegate` 型または `SampleDelegate(Of A, R)` 型のデリゲートを作成する場合、そのデリゲートには、次のいずれかのメソッドを割り当てることができます。

```vb
' Matching signature.
Public Shared Function ASecondRFirst(
    ByVal second As Second) As First
    Return New First()
End Function

' The return type is more derived.
Public Shared Function ASecondRSecond(
    ByVal second As Second) As Second
    Return New Second()
End Function

' The argument type is less derived.
Public Shared Function AFirstRFirst(
    ByVal first As First) As First
    Return New First()
End Function

' The return type is more derived
' and the argument type is less derived.
Public Shared Function AFirstRSecond(
    ByVal first As First) As Second
    Return New Second()
End Function
```

次のコード例は、メソッド シグネチャとデリゲート型の間の暗黙的な変換を示しています。

```vb
' Assigning a method with a matching signature
' to a non-generic delegate. No conversion is necessary.
Dim dNonGeneric As SampleDelegate = AddressOf ASecondRFirst
' Assigning a method with a more derived return type
' and less derived argument type to a non-generic delegate.
' The implicit conversion is used.
Dim dNonGenericConversion As SampleDelegate = AddressOf AFirstRSecond

' Assigning a method with a matching signature to a generic delegate.
' No conversion is necessary.
Dim dGeneric As SampleGenericDelegate(Of Second, First) = AddressOf ASecondRFirst
' Assigning a method with a more derived return type
' and less derived argument type to a generic delegate.
' The implicit conversion is used.
Dim dGenericConversion As SampleGenericDelegate(Of Second, First) = AddressOf AFirstRSecond
```

例については、次を参照してください。[デリゲート (Visual Basic) を使用して分散](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)と[Func および Action 汎用デリゲート (Visual Basic) を使用して分散](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)します。

## <a name="variance-in-generic-type-parameters"></a>ジェネリック型パラメーターの分散

.NET Framework 4 およびそれ以降、型が規定のとおり相互から継承されている場合、相互にジェネリック型パラメーターで指定された別の型を持つ汎用デリゲートを割り当てることができるように、デリゲートの間の暗黙的な変換が有効にできます。分散。

暗黙的な変換を有効にするには、`in` キーワードまたは `out` キーワードを使用して、デリゲートでジェネリック パラメーターを共変または反変として明示的に宣言する必要があります。

次のコード例は、共変のジェネリック型パラメーターが指定されたデリゲートを作成する方法を示しています。

```vb
' Type T is declared covariant by using the out keyword.
Public Delegate Function SampleGenericDelegate(Of Out T)() As T
Sub Test()
    Dim dString As SampleGenericDelegate(Of String) = Function() " "
    ' You can assign delegates to each other,
    ' because the type T is declared covariant.
    Dim dObject As SampleGenericDelegate(Of Object) = dString
End Sub
```

分散サポートのみを使用してメソッド シグネチャをデリゲート型に一致させ、`in` キーワードと `out` キーワードを使用しない場合、同等のラムダ式かメソッドを使用すれば、デリゲートをインスタンス化できることがありますが、デリゲートを別のデリゲートに割り当てることはできません。

次のコード例で`SampleGenericDelegate(Of String)`に明示的に変換することはできません`SampleGenericDelegate(Of Object)`ですが、`String`継承`Object`します。 この問題を修正するには、ジェネリック パラメーター `T` を `out` キーワードでマークします。

```vb
Public Delegate Function SampleGenericDelegate(Of T)() As T
Sub Test()
    Dim dString As SampleGenericDelegate(Of String) = Function() " "

    ' You can assign the dObject delegate
    ' to the same lambda expression as dString delegate
    ' because of the variance support for
    ' matching method signatures with delegate types.
    Dim dObject As SampleGenericDelegate(Of Object) = Function() " "

    ' The following statement generates a compiler error
    ' because the generic type T is not marked as covariant.
    ' Dim dObject As SampleGenericDelegate(Of Object) = dString

End Sub
```

### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a>.NET Framework のバリアント型パラメーターが含まれる汎用デリゲート

.NET Framework 4 では、既存の複数の汎用デリゲートで、ジェネリック型パラメーターに対して分散サポートが導入されました。

- <xref:System> 名前空間の `Action` デリゲート。<xref:System.Action%601>、<xref:System.Action%602> など

- <xref:System> 名前空間の `Func` デリゲート。<xref:System.Func%601>、<xref:System.Func%602> など

- <xref:System.Predicate%601> デリゲート

- <xref:System.Comparison%601> デリゲート

- <xref:System.Converter%602> デリゲート

詳細と例については、次を参照してください。 [Func および Action 汎用デリゲート (Visual Basic) を使用して分散](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)します。

### <a name="declaring-variant-type-parameters-in-generic-delegates"></a>汎用デリゲートのバリアント型パラメーターの宣言

汎用デリゲートに共変または反変のジェネリック型パラメーターがある場合、そのデリゲートは "*バリアント汎用デリゲート*" と呼ばれます。

汎用デリゲートのジェネリック型パラメーターを共変として宣言するには、`out` キーワードを使用します。 共変の型は、メソッドの戻り値の型としてのみ使用できます。メソッド引数の型として使用することはできません。 共変の汎用デリゲートを宣言する方法を次のコード例に示します。

```vb
Public Delegate Function DCovariant(Of Out R)() As R
```

汎用デリゲートのジェネリック型パラメーターを反変として宣言するには、`in` キーワードを使用します。 反変の型は、メソッド引数の型としてのみ使用できます。メソッドの戻り値の型として使用することはできません。 反変の汎用デリゲートを宣言する方法を次のコード例に示します。

```vb
Public Delegate Sub DContravariant(Of In A)(ByVal a As A)
```

> [!IMPORTANT]
> `ByRef` Visual Basic でのパラメーターは、バリアントとしてマークすることはできません。

同じデリゲートで、型パラメーターが異なる場合は、分散と共変性の両方をサポートすることもできます。 これを次の例に示します。

```vb
Public Delegate Function DVariant(Of In A, Out R)(ByVal a As A) As R
```

### <a name="instantiating-and-invoking-variant-generic-delegates"></a>バリアント汎用デリゲートのインスタンス化と呼び出し

バリアント デリゲートのインスタンス化および呼び出しは、インバリアント デリゲートのインスタンス化および呼び出しと同様に行うことができます。 次の例では、ラムダ式によってデリゲートをインスタンス化します。

```vb
Dim dvariant As DVariant(Of String, String) = Function(str) str + " "
dvariant("test")
```

### <a name="combining-variant-generic-delegates"></a>バリアント汎用デリゲートの結合

バリアント デリゲートの結合はお勧めしません。 <xref:System.Delegate.Combine%2A> メソッドはバリアント デリゲートの変換をサポートしていないため、デリゲートが厳密に同じ型である必要があります。 使用してデリゲートを結合するときに、実行時例外が発生する可能性、<xref:System.Delegate.Combine%2A>メソッド (でC#および Visual Basic) またはを使用して、`+`演算子 (でC#) の次のコード例に示すようにします。

```vb
Dim actObj As Action(Of Object) = Sub(x) Console.WriteLine("object: {0}", x)
Dim actStr As Action(Of String) = Sub(x) Console.WriteLine("string: {0}", x)

' The following statement throws an exception at run time.
' Dim actCombine = [Delegate].Combine(actStr, actObj)
```

## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a>値型と参照型でのジェネリック型パラメーターの分散

ジェネリック型パラメーターの分散がサポートされるのは参照型だけです。 たとえば、`DVariant(Of Int)`に暗黙的に変換できない`DVariant(Of Object)`または`DVariant(Of Long)`整数は値型であるためです。

次の例は、値型ではジェネリック型パラメーターの分散がサポートされないことを示しています。

```vb
' The type T is covariant.
Public Delegate Function DVariant(Of Out T)() As T
' The type T is invariant.
Public Delegate Function DInvariant(Of T)() As T
Sub Test()
    Dim i As Integer = 0
    Dim dInt As DInvariant(Of Integer) = Function() i
    Dim dVariantInt As DVariant(Of Integer) = Function() i

    ' All of the following statements generate a compiler error
    ' because type variance in generic parameters is not supported
    ' for value types, even if generic type parameters are declared variant.
    ' Dim dObject As DInvariant(Of Object) = dInt
    ' Dim dLong As DInvariant(Of Long) = dInt
    ' Dim dVariantObject As DInvariant(Of Object) = dInt
    ' Dim dVariantLong As DInvariant(Of Long) = dInt
End Sub
```

## <a name="relaxed-delegate-conversion-in-visual-basic"></a>Visual Basic での厳密でないデリゲート変換

厳密でないデリゲート変換によりより柔軟にメソッド シグネチャをデリゲート型と一致します。 たとえば、パラメーターの指定を省略してメソッドをデリゲートに割り当てるときに、関数の戻り値を省略できます。 詳細については、次を参照してください。[厳密でないデリゲート変換](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)します。

## <a name="see-also"></a>関連項目

- [ジェネリック](~/docs/standard/generics/index.md)
- [Func および Action 汎用デリゲートでの分散の使用 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
