---
title: 属性
description: 属性がF#プログラミングコンストラクトにメタデータを適用できるようにする方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 223263f5789b0fc7eb2b3ef2905f6436980bd14a
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424797"
---
# <a name="attributes"></a>属性

属性を使用すると、プログラミング構成要素にメタデータを適用できます。

## <a name="syntax"></a>構文

```fsharp
[<target:attribute-name(arguments)>]
```

## <a name="remarks"></a>Remarks

前の構文では、*ターゲット*は省略可能であり、存在する場合は、属性が適用されるプログラムエンティティの種類を指定します。 *Target*の有効な値は、このドキュメントの後半で示す表に示されています。

*属性名*は、有効な属性型の名前 (名前空間で修飾されている可能性があります) を参照します。この名前は、通常、属性の型名で使用される `Attribute` サフィックスはありません。 たとえば、`ObsoleteAttribute` 型を短縮して、このコンテキストで `Obsolete` だけにすることができます。

*引数*は、属性の型のコンストラクターへの引数です。 属性にパラメーターなしのコンストラクターがある場合は、引数リストとかっこを省略できます。 属性は、位置指定引数と名前付き引数の両方をサポートします。 *位置指定引数*は、出現する順序で使用される引数です。 名前付き引数は、属性にパブリックプロパティがある場合に使用できます。 これらを設定するには、引数リストで次の構文を使用します。

```fsharp
property-name = property-value
```

このようなプロパティの初期化は任意の順序で行うことができますが、任意の位置指定引数に従う必要があります。 位置指定引数とプロパティの初期化を使用する属性の例を次に示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6202.fs)]

この例では、属性は `DllImportAttribute`であり、短縮形で使用されています。 最初の引数は位置指定パラメーターで、2番目の引数はプロパティです。

属性は、*属性*と呼ばれるオブジェクトが型または他のプログラム要素に関連付けられるようにする .net プログラミングコンストラクトです。 属性が適用されるプログラム要素は、*属性ターゲット*と呼ばれます。 属性には、通常、ターゲットに関するメタデータが含まれます。 このコンテキストでは、メタデータは、フィールドやメンバー以外の型に関する任意のデータにすることができます。

のF#属性は、関数、メソッド、アセンブリ、モジュール、型 (クラス、レコード、構造体、インターフェイス、デリゲート、列挙体、共用体など)、コンストラクター、プロパティ、フィールド、およびの各プログラミング構成要素に適用できます。パラメーター、型パラメーター、および戻り値。 属性は、クラス、式、またはワークフロー式内の `let` バインドでは許可されていません。

通常、属性の宣言は、属性ターゲットの宣言の直前に記述されます。 複数の属性宣言は、次のように組み合わせて使用できます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6603.fs)]

.NET リフレクションを使用すると、実行時に属性に対してクエリを実行できます。

前のコード例のように、複数の属性を個別に宣言することも、セミコロンを使用して個々の属性とコンストラクターを区切る場合は、1組の角かっこで宣言することもできます。次に例を示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6604.fs)]

通常、属性には、`Obsolete` 属性、セキュリティに関する考慮事項の属性、COM サポートの属性、コードの所有権に関連する属性、および型をシリアル化できるかどうかを示す属性があります。 次の例では、`Obsolete` 属性の使用方法を示します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6605.fs)]

属性ターゲット `assembly` および `module`については、アセンブリ内の最上位 `do` バインディングに属性を適用します。 次のように、属性の宣言に word `assembly` または `module` を含めることができます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6606.fs)]

`do` バインディングに適用されている属性の属性ターゲットを省略したF#場合、コンパイラはその属性に対して意味のある属性ターゲットを特定しようとします。 多くの属性クラスには、その属性でサポートされているターゲットに関する情報を含む `System.AttributeUsageAttribute` 型の属性があります。 `System.AttributeUsageAttribute` が、属性がターゲットとしての関数をサポートしていることを示している場合、属性はプログラムのメインエントリポイントに適用されます。 属性がターゲットとしてのアセンブリをサポートしていることが `System.AttributeUsageAttribute` によって示された場合、コンパイラは、アセンブリに適用する属性を受け取ります。 ほとんどの属性は、関数とアセンブリの両方には適用されませんが、その場合、属性はプログラムの main 関数に適用されます。 属性ターゲットが明示的に指定されている場合は、指定されたターゲットに属性が適用されます。

通常、属性ターゲットを明示的に指定する必要はありませんが、次の表に示すように、属性の*target*に有効な値を使用例と共に示します。

<table>
  <tr>
    <th>属性のターゲット</td>
    <th>例</td>
  </tr>
  <tr>
    <td>アセンブリ</td>
    <td><pre lang="fsharp"><code>[&lt;assembly: AssemblyVersionAttribute("1.0.0.0")&gt;]</code></pre></td>
  </tr>
  <tr>
    <td>return</td>
    <td><pre lang="fsharp"><code>let function1 x : [&lt;return: Obsolete&gt;] int = x + 1</code></pre></td>
  </tr>
  <tr>
    <td>のフィールド</td>
    <td><pre lang="fsharp"><code>[&lt;field: DefaultValue&gt;] val mutable x: int</code></pre></td>
  </tr>
  <tr>
    <td>プロパティ</td>
    <td><pre lang="fsharp"><code>[&lt;property: Obsolete&gt;] this.MyProperty = x</code></pre></td>
  </tr>
  <tr>
    <td>param</td>
    <td><pre lang="fsharp"><code>member this.MyMethod([&lt;param: Out&gt;] x : ref&lt;int&gt;) = x := 10</code></pre></td>
  </tr>
  <tr>
    <td>type</td>
    <td>
        <pre lang="fsharp"><code>
[&lt;type: StructLayout(Sequential)&gt;]
type MyStruct =
struct
x : byte
y : int
end</code></pre>
    </td>
  </tr>
</table>

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
