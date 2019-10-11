---
title: 制約
description: ジェネリック型F#パラメーターに適用される制約について説明し、ジェネリック型または関数の型引数の要件を指定します。
ms.date: 05/16/2016
ms.openlocfilehash: 9912ba63138d893a7c616661dd2b1cbdbe51916c
ms.sourcegitcommit: 878ca7550b653114c3968ef8906da2b3e60e3c7a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736789"
---
# <a name="constraints"></a>制約

このトピックでは、ジェネリック型パラメーターに適用して、ジェネリック型またはジェネリック関数の型引数の要件を指定できる制約について説明します。

## <a name="syntax"></a>構文

```fsharp
type-parameter-list when constraint1 [ and constraint2]
```

## <a name="remarks"></a>コメント

ジェネリック型で使用できる型を制限するために、いくつかの異なる制約を適用できます。 次の表に、これらの制約の一覧とその説明を示します。

|制約|構文|説明|
|----------|------|-----------|
|型の制約|*型パラメーター* : &gt;*型*|指定された型は、指定された型と同じか、または指定された型と同じである必要があります。または、型がインターフェイスの場合は、指定された型がインターフェイスを実装する必要があります。|
|Null 制約|*型パラメーター* : null|指定された型は、null リテラルをサポートしている必要があります。 これには、すべての .NET オブジェクトF#の種類が含まれますが、list、tuple、function、class、record、または union 型は含まれません。|
|明示的なメンバー制約|[(]*型パラメーター* [または... または*型パラメーター*)]: (*メンバー シグネチャ*)|指定された型引数の少なくとも1つに、指定されたシグネチャを持つメンバーが必要です。一般的な使用を目的としたものではありません。 メンバーは、明示的なメンバー制約の有効なターゲットとなるように、型または暗黙的な型拡張の一部に対して明示的に定義する必要があります。|
|コンストラクターの制約|*型パラメーター* : (new: unit-&gt; ' a)|指定された型には、パラメーターなしのコンストラクターが必要です。|
|値型の制約|: struct|指定された型は .NET 値型である必要があります。|
|参照型の制約|: 構造体ではありません。|指定された型は .NET 参照型である必要があります。|
|列挙型の制約|: enum @ no__t-0*基になる型*&gt;|指定された型は、指定された基になる型を持つ列挙型でなければなりません。一般的な使用を目的としたものではありません。|
|デリゲート制約|: delegate @ no__t-0*タプル-パラメーターの型*、*戻り値の型*&gt;|指定された型は、指定された引数と戻り値を持つデリゲート型である必要があります。一般的な使用を目的としたものではありません。|
|比較制約|: 比較|指定された型は、比較をサポートする必要があります。|
|等値制約|: 等値|指定された型は、等価性をサポートする必要があります。|
|アンマネージド制約|: アンマネージド|指定された型はアンマネージ型でなければなりません。 アンマネージ型は、特定のプリミティブ型 (`sbyte`、`byte`、`char`、`nativeint`、`unativeint`、`float32`、`float`、`int16`、`uint16`、`int32`、0、1、2、3)、列挙型、4 または非ジェネリックです。すべてのアンマネージ型のフィールドを持つ構造体。|

制約を追加する必要があるのは、制約の種類では使用できても、一般的な型では使用できない機能をコードで使用する必要がある場合です。 たとえば、型制約を使用してクラス型を指定する場合は、ジェネリック関数またはジェネリック型で、そのクラスのメソッドのいずれかを使用できます。

制約を指定することは、型パラメーターを明示的に記述するときに必要になることがあります。これは、制約がないため、コンパイラは、実行時に型に対して提供される可能性があるすべての型で使用できることを検証する方法がないためです。引き.

コードでF#使用する最も一般的な制約は、基本クラスまたはインターフェイスを指定する型制約です。 他の制約は、特定の機能F#を実装するためにライブラリによって使用されます。たとえば、算術演算子に対して演算子のオーバーロードを実装するためにF#使用される明示的なメンバー制約や、主に共通言語ランタイムでサポートされている制約の完全なセットをサポートします。

型の推論プロセスでは、一部の制約がコンパイラによって自動的に推論されます。 たとえば、関数で `+` 演算子を使用すると、コンパイラは、式で使用されている変数型の明示的なメンバー制約を推論します。

次のコードは、いくつかの制約宣言を示しています。

```fsharp
// Base Type Constraint
type Class1<'T when 'T :> System.Exception> =
class end

// Interface Type Constraint
type Class2<'T when 'T :> System.IComparable> = 
class end

// Null constraint
type Class3<'T when 'T : null> =
class end

// Member constraint with instance member
type Class5<'T when 'T : (member Method1 : 'T -> int)> =
class end

// Member constraint with property
type Class6<'T when 'T : (member Property1 : int)> =
class end

// Constructor constraint
type Class7<'T when 'T : (new : unit -> 'T)>() =
member val Field = new 'T()

// Reference type constraint
type Class8<'T when 'T : not struct> =
class end

// Enumeration constraint with underlying value specified
type Class9<'T when 'T : enum<uint32>> =
class end

// 'T must implement IComparable, or be an array type with comparable
// elements, or be System.IntPtr or System.UIntPtr. Also, 'T must not have
// the NoComparison attribute.
type Class10<'T when 'T : comparison> =
class end

// 'T must support equality. This is true for any type that does not
// have the NoEquality attribute.
type Class11<'T when 'T : equality> =
class end

type Class12<'T when 'T : delegate<obj * System.EventArgs, unit>> =
class end

type Class13<'T when 'T : unmanaged> =
class end

// Member constraints with two type parameters
// Most often used with static type parameters in inline functions
let inline add(value1 : ^T when ^T : (static member (+) : ^T * ^T -> ^T), value2: ^T) =
value1 + value2

// ^T and ^U must support operator +
let inline heterogenousAdd(value1 : ^T when (^T or ^U) : (static member (+) : ^T * ^U -> ^T), value2 : ^U) =
value1 + value2

// If there are multiple constraints, use the and keyword to separate them.
type Class14<'T,'U when 'T : equality and 'U : equality> =
class end
```

## <a name="see-also"></a>関連項目

- [ジェネリック](index.md)
- [制約](constraints.md)
