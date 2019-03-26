---
title: 属性
description: 学習方法F#属性を使用するプログラミング コンストラクトに適用されるメタデータ。
ms.date: 05/16/2016
ms.openlocfilehash: 6e80bc4e32ee4ff5ff132270bde8e2fd018369e1
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/26/2019
ms.locfileid: "58464659"
---
# <a name="attributes"></a>属性

属性は、プログラミング コンストラクトに適用されるメタデータを有効にします。

## <a name="syntax"></a>構文

```fsharp
[<target:attribute-name(arguments)>]
```

## <a name="remarks"></a>Remarks

前の構文で、*ターゲット*省略可能ですが、存在する場合は、属性が適用されるプログラム エンティティの種類を指定します。 有効な値*ターゲット*このドキュメントの後半で表示されるテーブルに表示されます。

*属性名*サフィックスの有無で、有効な属性型の名前 (場合によっては名前空間を持つ修飾名) を指す`Attribute`属性の型名で通常使用されています。 たとえば、型`ObsoleteAttribute`だけに短縮できます`Obsolete`このコンテキストでします。

*引数*属性型のコンス トラクターへの引数です。 属性に既定のコンス トラクターがある場合は、引数リストとかっこを省略できます。 属性は、位置指定引数と名前付き引数の両方をサポートします。 *位置指定引数*が出現する順序で使用される引数。 属性は、パブリック プロパティを持つ場合、名前付き引数を使用できます。 引数リストで、次の構文を使用して、これらを設定することができます。

```
*property-name* = *property-value*
```

このようなプロパティの初期化は、任意の順序で指定できますが、位置引数に従う必要があります。 位置指定引数とプロパティの初期化を使用する属性の例を次に示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6202.fs)]

この例では、属性は`DllImportAttribute`、ここで短縮形で使用します。 最初の引数が位置指定パラメーターと、2 番目のプロパティです。

属性は、.NET のプログラミング コンストラクトと呼ばれる、オブジェクトを有効にする、*属性*型またはその他のプログラム要素に関連付けられる。 属性が適用されるプログラム要素と呼ばれる、*属性ターゲット*します。 属性には、通常は、ターゲットに関するメタデータが含まれています。 このコンテキストでは、メタデータは、フィールドやメンバー以外の種類に関するすべてのデータになります。

属性F#次のプログラミング構成要素に適用できます: 関数、メソッド、アセンブリ、モジュール、型 (クラス、レコード、構造体、インターフェイス、デリゲート、列挙体、共用体、およびなど)、コンス トラクター、プロパティ、フィールド、パラメーターは、入力パラメーター、および戻り値。 属性では許可されません`let`クラス、式、またはワークフローの式内でバインドします。

通常、属性の宣言は、属性ターゲット宣言の前に直接表示されます。 複数の属性宣言は、次のように使用できます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6603.fs)]

.NET リフレクションを使用して、実行時に属性を照会できます。

前のコード例のように複数の属性を個別に宣言または次に示すように個々 の属性と、コンス トラクターを分離する、セミコロンを使用する場合は、1 つの組の角かっこで宣言することができます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6604.fs)]

よく発生属性が含まれます、`Obsolete`属性、セキュリティの考慮事項は、属性は、COM サポート、コードの所有権に関連する属性および属性の型をシリアル化できるかどうかを示す属性です。 次の例では、使用、`Obsolete`属性。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6605.fs)]

属性の対象の`assembly`と`module`、最上位に属性を適用する`do`アセンブリにバインドします。 単語を含めることができます`assembly`または`module`属性の宣言で、次のようにします。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6606.fs)]

適用する属性の属性のターゲットを省略したかどうか、 `do` 、バインド、その属性の意味のある属性のターゲットを特定しようと試みます F# コンパイラ。 多くの属性クラスは、型の属性を持つ`System.AttributeUsageAttribute`その属性のサポートされている対象に関する情報を含むです。 場合、`System.AttributeUsageAttribute`属性には、ターゲットとしての関数がサポートされています、プログラムのメイン エントリ ポイントに適用する属性が実行されることを示します。 場合、`System.AttributeUsageAttribute`属性は、ターゲットとしてのアセンブリをサポートしています、コンパイラがアセンブリに適用する属性を受け取ることを示します。 関数と、アセンブリの両方にほとんどの属性は適用されませんが、プログラムの main 関数に適用する場合で属性が取得されます。 属性ターゲットを明示的に指定した場合は、属性が指定したターゲットに適用されます。

属性が対象の有効な値で明示的に、通常指定する必要はありませんが*ターゲット*属性での使用状況の例と、次の表に示します。

<table>
  <tr>
    <th>属性ターゲット</td>
    <th>例</td> 
  </tr>
  <tr>
    <td>アセンブリ</td>
    <td><pre lang="fsharp"><code>[&lt;assembly: AssemblyVersionAttribute("1.0.0.0")&gt;]<code></pre></td> 
  </tr>
  <tr>
    <td>return</td>
    <td><pre lang="fsharp"><code>let function1 x : [&lt;return: Obsolete&gt;] int = x + 1<code></pre></td> 
  </tr>
  <tr>
    <td>フィールド</td>
    <td><pre lang="fsharp"><code>[&lt;field: DefaultValue&gt;] val mutable x: int<code></pre></td> 
  </tr>
  <tr>
    <td>property</td>
    <td><pre lang="fsharp"><code>[&lt;property: Obsolete&gt;] this.MyProperty = x<code></pre></td> 
  </tr>
  <tr>
    <td>param</td>
    <td><pre lang="fsharp"><code>member this.MyMethod([&lt;param: Out&gt;] x : ref&lt;int&gt;) = x := 10<code></pre></td> 
  </tr>
  <tr>
    <td>型</td>
    <td>
        <pre lang="fsharp"><code>
        [&lt;type: StructLayout(Sequential)&gt;] 
        type MyStruct = 
        struct 
        x : byte
        y : int
        end
        <code></pre>
    </td>
  </tr>
</table>

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)