---
title: 抽象クラス
description: 一部またはすべてのメンバーを実装しないままにして F# 抽象クラスをについて説明し、多様な種類のオブジェクトのセットの共通の機能を表します。
ms.date: 05/16/2016
ms.openlocfilehash: 8251d481c9056d40a0b13ae3c89353406986c116
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645541"
---
# <a name="abstract-classes"></a>抽象クラス

*抽象クラス*は派生クラスによって実装を提供できるように実装されていません、一部またはすべてのメンバーのままにするクラス。

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

オブジェクト指向プログラミングでは、抽象クラスは、階層の基本クラスとして使用され、オブジェクトの種類の多様な一連の共通機能を表します。 「抽象」という名前からわかるように、抽象クラス多くの場合、対応していない問題ドメインの具体的なエンティティに直接します。 ただし、どのような多くのさまざまな具体的なエンティティが共通を表すこれらの操作を行います。

抽象クラスがあります、`AbstractClass`属性。 実装し、メンバーが実装されていませんができます。 用語の使用*抽象*クラスは、他の .NET 言語と同様に適用するとただし、用語の使用*抽象*メソッド (およびプロパティ) に適用する場合からの F# で少し異なりますが、他の .NET 言語で使用します。 F#でメソッドをマークすると、`abstract`キーワードでは、このことを示しますメンバーと呼ばれる、エントリ、*仮想ディスパッチ スロット*、その型の仮想関数の内部テーブルでします。 メソッドが仮想、つまり、ですが、`virtual`キーワードは、F# 言語では使用されません。 キーワード`abstract`メソッドを実装するかどうかに関係なく、仮想メソッドで使用されます。 仮想ディスパッチ スロットの宣言は、そのディスパッチ スロットのメソッドの定義とは別です。 そのため、抽象メソッドの宣言といずれかを別の定義の両方の組み合わせは、仮想メソッドの宣言と定義を別の .NET 言語での F# と同じ、`default`キーワードまたは`override`キーワード。 詳細と例については、次を参照してください。[メソッド](members/methods.md)します。

クラスは、宣言が定義されていない抽象メソッドがある場合にのみ抽象と見なされます。 したがって、抽象メソッドを使用するクラスは、必ずしも抽象クラスではできません。 クラスが抽象メソッドを定義されていない場合は使用しないでください、 **AbstractClass**属性。

前の構文で*アクセシビリティ修飾子*できる`public`、`private`または`internal`します。 詳細については、「[Access Control](access-control.md)」(アクセス制御) を参照してください。

他の種類と同様、基底クラスと 1 つ以上のインターフェイスの基本抽象クラスことができます。 と共に別々 の行に各基底クラスまたはインターフェイスが表示されます、`inherit`キーワード。

抽象クラスの型定義は、完全に定義されたメンバーを含めることができますが、抽象メンバーを含めることもできます。 抽象メンバーの構文は、前の構文とは別に示しています。 この構文では、*型シグネチャ*のメンバーを含む一覧、パラメーターの順序と戻り値の型で型で区切られている`->`トークンや`*`カリー化を適切なトークンとタプルパラメーター。 抽象メンバー型のシグネチャの構文は、シグネチャ ファイルで使用して、Visual Studio コード エディターでの IntelliSense によって表示されるのと同じです。

次のコードでは、抽象クラスが 2 つ非抽象派生クラス、四角形や円の図形を示します。 この例では、抽象クラス、メソッド、およびプロパティを使用する方法を示します。 例では、抽象クラスの図形は、具体的なエンティティの円、四角形の共通の要素を表します。 (2 次元座標システム) のすべての図形の一般的な機能はアウト、Shape クラスに抽象化します。 グリッド、回転の角度と面積と周プロパティ上の位置。 これは、オーバーライドできます、位置、個々 の図形を変更できませんが、動作を除く。

インバリアントの回転は、その対称性のため、Circle クラスのように、回転メソッドをオーバーライドできます。 ように、Circle クラスでは、回転メソッドは何も実行しないメソッドに置換されます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2901.fs)]

**出力:**

```
Perimeter of square with side length 10.000000 is 40.000000
Circumference of circle with radius 5.000000 is 31.415927
Area of Square: 100.000000
Area of Circle: 78.539816
```

## <a name="see-also"></a>関連項目

- [クラス](classes.md)
- [メンバー](members/index.md)
- [メソッド](members/methods.md)
- [Properties](members/Properties.md)
