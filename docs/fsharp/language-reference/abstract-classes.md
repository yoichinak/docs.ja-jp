---
title: 抽象クラス
description: 一部またはすべてのメンバーを実装しないままにして F# 抽象クラスをについて説明し、多様な種類のオブジェクトのセットの共通の機能を表します。
ms.date: 05/16/2016
ms.openlocfilehash: d7fc87178cff7c5c824992c97198b49f87025f00
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2019
ms.locfileid: "71082949"
---
# <a name="abstract-classes"></a>抽象クラス

*抽象クラス*は、一部またはすべてのメンバーを実装しないままにして、派生クラスによって実装を提供できるようにするクラスです。

## <a name="syntax"></a>構文

```fsharp
// Abstract class syntax.
[<AbstractClass>]
type [ accessibility-modifier ] abstract-class-name =
[ inherit base-class-or-interface-name ]
[ abstract-member-declarations-and-member-definitions ]

// Abstract member syntax.
abstract member member-name : type-signature
```

## <a name="remarks"></a>Remarks

オブジェクト指向プログラミングでは、抽象クラスが階層の基底クラスとして使用され、さまざまな種類のオブジェクトの共通機能を表します。 "Abstract" という名前が示すとおり、多くの場合、抽象クラスは問題ドメインの具象エンティティに直接対応していません。 ただし、共通のさまざまな具象エンティティの数を表すことができます。

抽象クラスに`AbstractClass`は属性が必要です。 実装および実装されていないメンバーを持つことができます。 用語の使用*抽象*クラスは、他の .NET 言語と同様に適用するとただし、用語の使用*抽象*メソッド (およびプロパティ) に適用する場合からの F# で少し異なりますが、他の .NET 言語で使用します。 でF#は、メソッドが`abstract`キーワードでマークされている場合、その型の仮想関数の内部テーブルに、メンバーに*仮想ディスパッチスロット*と呼ばれるエントリがあることを示します。 メソッドが仮想、つまり、ですが、`virtual`キーワードは、F# 言語では使用されません。 キーワード`abstract`は、メソッドが実装されているかどうかに関係なく、仮想メソッドで使用されます。 仮想ディスパッチスロットの宣言は、そのディスパッチスロットのメソッドの定義とは別のものです。 そのため、抽象メソッドの宣言といずれかを別の定義の両方の組み合わせは、仮想メソッドの宣言と定義を別の .NET 言語での F# と同じ、`default`キーワードまたは`override`キーワード。 詳細と例については、「[メソッド](./members/methods.md)」を参照してください。

クラスは、宣言されているが定義されていない抽象メソッドがある場合にのみ、抽象と見なされます。 したがって、抽象メソッドを持つクラスは、必ずしも抽象クラスではありません。 クラスに未定義の抽象メソッドがある場合を除き、 **AbstractClass**属性は使用しないでください。

前の構文では、*アクセシビリティ-修飾子*に`public`は`private` 、 `internal`、またはを指定できます。 詳細については、「[Access Control](access-control.md)」(アクセス制御) を参照してください。

他の型と同様に、抽象クラスは基底クラスと1つ以上の基本インターフェイスを持つことができます。 各基底クラスまたはインターフェイスは、 `inherit`キーワードと共に個別の行に表示されます。

抽象クラスの型定義には、完全に定義されたメンバーを含めることができますが、抽象メンバーを含めることもできます。 抽象メンバーの構文は、前の構文で個別に表示されます。 この構文では、メンバーの*型シグネチャ*は、列挙型と戻り値の型を含むリストであり、カリー化および`->`タプルのパラメーターに`*`は、トークンまたはトークンで区切られています。 抽象メンバー型シグネチャの構文は、署名ファイルで使用される構文と、Visual Studio Code エディターで IntelliSense によって示されるシグネチャと同じです。

次のコードは、抽象クラスの図形を示しています。抽象クラスには、2つの非抽象派生クラス (Square と Circle) があります。 この例は、抽象クラス、メソッド、およびプロパティの使用方法を示しています。 この例では、抽象クラスのシェイプは、具象エンティティの circle と square の共通要素を表しています。 (2 次元座標系内の) すべての図形の共通機能は、形状クラスに抽象化されます。これは、グリッド上の位置、回転角度、および領域と境界のプロパティです。 これらは、位置、つまり個々の図形が変更できない動作を除き、オーバーライドできます。

回転メソッドは、対称軸クラスのようにオーバーライドできます。これは、対称によって回転が不変です。 そのため、Circle クラスでは、ローテーションメソッドは何も実行しないメソッドに置き換えられます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2901.fs)]

**出力:**

```console
Perimeter of square with side length 10.000000 is 40.000000
Circumference of circle with radius 5.000000 is 31.415927
Area of Square: 100.000000
Area of Circle: 78.539816
```

## <a name="see-also"></a>関連項目

- [クラス](classes.md)
- [メンバー](./members/index.md)
- [メソッド](./members/methods.md)
- [Properties](./members/Properties.md)
