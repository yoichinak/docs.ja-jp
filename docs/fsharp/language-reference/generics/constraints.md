---
title: 制約
description: についてF#ジェネリック型または関数の型引数の要件を指定するジェネリック型パラメーターに適用される制約。
ms.date: 05/16/2016
ms.openlocfilehash: 1bf5c6fc4df6c8f2f7f969bd13030172c6b8aab9
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645282"
---
# <a name="constraints"></a>制約

このトピックでは、ジェネリックに適用できる制約を説明します、ジェネリック型または関数の型引数の要件を指定するパラメーターを入力します。

## <a name="syntax"></a>構文

```fsharp
type-parameter-list when constraint1 [ and constraint2]
```

## <a name="remarks"></a>Remarks

ジェネリック型で使用できる型の制限に適用できるいくつかのさまざまな制約があります。 次の表は、これらの制約の一覧です。

|制約|構文|説明|
|----------|------|-----------|
|型制約|*type-parameter* :&gt; *type*|指定された型は、指定した型から同じか、または派生をする必要があります。 または、型がインターフェイスである場合は、指定された型がインターフェイスを実装する必要があります。|
|Null の制約|*型パラメーター* : null|指定された型には、null リテラルをサポートする必要があります。 これには、すべて .NET オブジェクトの種類がない F# リスト、タプル、関数、クラス、レコード、または共用体の型が含まれます。|
|明示的なメンバー制約|[(]*型パラメーター* [または... または*型パラメーター*)]: (*メンバー シグネチャ*)|指定された型引数の少なくとも 1 つを指定したシグネチャを持つメンバーがあります。一般的な用途は想定されていません。 メンバーする必要がありますか、明示的に定義するメンバーの明示的な制約の有効なターゲットにするには、型または暗黙的な型の拡張機能の一部です。|
|コンス トラクターの制約|*type-parameter* : ( new : unit -&gt; 'a )|指定された型には、既定のコンス トラクターが必要です。|
|値型の制約|: 構造体|指定された型は、.NET 値型である必要があります。|
|参照型の制約|: 構造体ではありません|指定された型は、.NET 参照型である必要があります。|
|列挙型の制約|: enum&lt;*underlying-type*&gt;|指定された型を指定した基になる型を持つ列挙型である必要があります。一般的な用途は想定されていません。|
|デリゲートの制約|: delegate&lt;*tuple-parameter-type*, *return-type*&gt;|必要がありますを指定した引数を持つデリゲート型であるし、戻り値を指定された型一般的な用途は想定されていません。|
|比較の制約|: 比較|指定された型には、比較をサポートする必要があります。|
|等しいかどうかの制約|: 等しいかどうか|指定された型には、等しいかどうかをサポートする必要があります。|
|アンマネージド制約|: 管理されていません。|指定された型は、アンマネージ型である必要があります。 アンマネージ型は、プリミティブ型 (`sbyte`、 `byte`、 `char`、 `nativeint`、 `unativeint`、 `float32`、 `float`、 `int16`、 `uint16`、 `int32`、 `uint32`、 `int64`、 `uint64`、または`decimal`)、列挙型、 `nativeptr<_>`、または非ジェネリック構造体のフィールドは、すべてのアンマネージ型。|

一般に、制約の種類がない型で使用できる機能を使用するコードがある場合に制約を追加する必要があります。 たとえば、クラス型を指定する型の制約を使用する場合は、ジェネリック関数または型では、そのクラスのメソッドのいずれかを使用できます。

制約を指定する場合があります必要な型パラメーターを明示的に記述する場合、制約、コンパイラがあるないため使用している機能は型の実行時に指定する場合がある任意の型では使用できないことを検証する方法にパラメーター。

使用する最も一般的な制約F#コードが型制約が基底クラスまたはインターフェイスを指定します。 その他の制約が、演算子、算術演算子のオーバー ロードを実装するために使用または主に F# をサポート、完了するために提供される明示的なメンバー制約など、特定の機能を実装するために F# ライブラリによって使用されるか、共通言語ランタイムでサポートされている制約のセット。

型の推論プロセス中にいくつかの制約は、コンパイラによって自動的に推論されます。 たとえば、使用する場合、`+`演算子関数で、コンパイラは、明示的なメンバー制約式で使用される変数の型を推測します。

次のコードは、いくつかの制約の宣言を示しています。

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

// Member constraint with static member
type Class4<'T when 'T : (static member staticMethod1 : unit -> 'T) > =
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
