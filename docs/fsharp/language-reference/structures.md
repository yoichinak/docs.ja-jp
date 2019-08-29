---
title: 構造体
description: F#構造について説明します。これは、多くの場合、少量のデータと単純な動作を持つ型のクラスよりも効率的です。
ms.date: 05/16/2016
ms.openlocfilehash: 1e9652cc4776e4d1d52eb20e41b6dd87a6c5ba05
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106825"
---
# <a name="structures"></a>構造体

*構造体*は、少量のデータと単純な動作を持つ型のクラスよりも効率的な、コンパクトなオブジェクト型です。

## <a name="syntax"></a>構文

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    struct
        type-definition-elements-and-members
    end
// or
[ attributes ]
[<StructAttribute>]
type [accessibility-modifier] type-name =
    type-definition-elements-and-members
```

## <a name="remarks"></a>Remarks

構造体は*値型*であり、スタックに直接格納されるか、または、フィールドまたは配列要素として使用される場合は親の型にインラインで格納されることを意味します。 クラスやレコードとは異なり、構造体のセマンティクスは値渡しです。 これは、主にアクセスおよびコピーが頻繁に行われるデータの小規模な集約に有用であることを意味します。

上記の構文では、2 つの形式が示されています。 1 番目のものは軽量構文ではないものの、頻繁に使用されます。これは、`struct` キーワードと `end` キーワードを使用する場合に、2 番目のものに出現する `StructAttribute` 属性を省略できるためです。 `StructAttribute` は省略して単に `Struct` とすることができます。

前の構文の*型定義の要素とメンバー*は、メンバーの宣言と定義を表します。 構造体にはコンストラクター、可変フィールド、および不変フィールドを含めることができ、メンバーとインターフェイス実装を宣言できます。 詳細については、「[メンバー](./members/index.md)」を参照してください。

構造体は、継承に参加することも、`let` または `do` バインディングを含めることも、それ自身の型のフィールドを再帰的に含めることもできません (ただし、それ自身の型を参照する参照セルを含めることができます)。

構造体では `let` バインディングは使用できないため、`val` キーワードを使用して構造体のフィールドを宣言する必要があります。 `val` キーワードではフィールドとその型が定義されますが、初期化は実行できません。 代わりに、`val` 宣言がゼロまたは null に初期化されます。 このため、暗黙のコンストラクター (宣言で構造体名の直後に指定されるパラメーター) を含む構造体では、`val` 宣言に `DefaultValue` 属性で注釈を付ける必要があります。 定義されたコンストラクターを含む構造体でも、ゼロ初期化がサポートされます。 したがって、`DefaultValue` 属性は、このようなゼロ値がフィールドに対して有効であることの宣言になります。 構造体の暗黙的なコンストラクターでは動作は実行されません。これは、`let` バインディングと `do` バインディングがその型では許可されていないためですが、渡された暗黙のコンストラクターのパラメーター値はプライベート フィールドとして使用できます。

明示的なコンストラクターにフィールド値の初期化が含まれる場合があります。 明示的なコンストラクターを含む構造体がある場合も、ゼロ初期化がサポートされます。ただし、明示的なコンストラクターと競合するため、`DefaultValue` 宣言では `val` 属性を使用しません。 `val`宣言の詳細については[、「明示的なフィールド:`val`キーワード](./members/explicit-fields-the-val-keyword.md)します。

構造体では属性およびアクセシビリティ修飾子が許可されており、その他の型と同じ規則に従います。 詳細については、「[属性](attributes.md)と[Access Control](access-control.md)」を参照してください。

次のコード例は構造体の定義を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2501.fs)]

## <a name="byreflike-structs"></a>ByRefLike 構造体

に似たセマンティクスに`byref`従うことができる独自の構造体を定義できます。詳細については、 [byref](byrefs.md)を参照してください。 これは、属性を<xref:System.Runtime.CompilerServices.IsByRefLikeAttribute>使用して行います。

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsByRefLike`はを意味`Struct`しません。 両方とも型に存在する必要があります。

A"`byref`のような"F# の構造体はスタック バインド値の型。 マネージヒープに割り当てられることはありません。 `byref`と同様の構造体は、有効期間と非キャプチャに関する厳密なチェックセットによって適用されるため、ハイパフォーマンスプログラミングに役立ちます。 規則は次のとおりです。

- これらは、関数パラメーター、メソッドパラメーター、ローカル変数、メソッドが返す値として使用できます。
- これらは、クラスまたは通常の構造体の静的メンバーまたはインスタンスメンバーにすることはできません。
- これらは、クロージャコンストラクト (`async`メソッドまたはラムダ式) によってキャプチャすることはできません。
- これらは、ジェネリックパラメーターとして使用することはできません。

これらのルールでは使用法が非常に厳密に制限されていますが、高パフォーマンスコンピューティングの約束を安全な方法で実現するために、これらのルールが使用されます。

## <a name="readonly-structs"></a>ReadOnly 構造体

<xref:System.Runtime.CompilerServices.IsReadOnlyAttribute>属性を使用して構造体に注釈を付けることができます。 例:

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsReadOnly`はを意味`Struct`しません。 `IsReadOnly`構造体を持つには、両方を追加する必要があります。

この属性の使用は、F# と C# として扱い、他人に把握できるようにすることのメタデータを出力`inref<'T>`と`in ref`、それぞれします。

Readonly 構造体の内部で変更可能な値を定義すると、エラーが発生します。

## <a name="struct-records-and-discriminated-unions"></a>構造体レコードと判別共用体

`[<Struct>]`属性を使用して、[レコード](records.md)と[判別共用](discriminated-unions.md)体を構造体として表すことができます。  詳細については、各記事をご覧ください。

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
- [クラス](classes.md)
- [レコード](records.md)
- [メンバー](./members/index.md)
