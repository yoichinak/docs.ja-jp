---
title: Visual Basic でのタプル
ms.date: 04/23/2017
helpviewer_keywords:
- tuples [Visual Basic]
ms.assetid: 3e66cd1b-3432-4e1d-8c37-5ebacae8f53f
ms.openlocfilehash: 146e9c2360cea153d2f487769d5b983516861e8d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663298"
---
# <a name="tuples-visual-basic"></a>タプル (Visual Basic)

Visual Basic 2017 以降、Visual Basic 言語ではタプルのための組み込みサポートが提供され、タプルの作成や、タプルの要素へのアクセスが簡略化されます。 タプルとは、値の特定の数とシーケンスを持つ軽量のデータ構造です。 タプルをインスタンス化する場合は、数とそれぞれの値 (または要素) のデータ型を定義します。 たとえば、2 タプル (またはペア) には、2 つの要素があります。 最初の要素は `Boolean` 値で、2 つ目の要素は `String`となる場合があります。 タプルを使用すると 1 つのオブジェクトに複数の値を格納するのが簡単になるため、メソッドから複数の値を返すための気軽な方法としてよく使用されます。

> [!IMPORTANT]
> タプルのサポートが必要です、<xref:System.ValueTuple>型。 .NET Framework 4.7 がインストールされていない場合は、NuGet パッケージを追加する必要があります`System.ValueTuple`、これは、NuGet ギャラリーで使用できます。 このパッケージは、せず可能性がありますエラーが発生したコンパイル"定義済みの型 'ValueTuple(Of,,,)' は定義されている、またはインポートされていません"に似ています

## <a name="instantiating-and-using-a-tuple"></a>タプルのインスタンス化と使用

タプルをインスタンス化するには、外側の値のコンマ区切りの im かっこ。 これらの値の各し、タプルのフィールドになります。 次のコードが 3 回 (または 3 タプル) を定義するなど、`Date`その最初の値として、 `String` 、2 番目のオペランドとして、 `Boolean` 3 つ目として。

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#1)]

既定では、タプル内の各フィールドの名前から成る文字列`Item`と共に、タプルのフィールドの 1 から始まる位置。 この 3 タプルの`Date`フィールドは`Item1`、`String`フィールドは`Item2`、および`Boolean`フィールドは`Item3`します。 次の例は、前のコード行でインスタンス化するタプルのフィールドの値を表示します。

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#2)]

Visual Basic のタプルのフィールドは読み取り/書き込みです。タプルをインスタンス化した後は、その値を変更できます。 次の例では、前の例で作成されたタプルの 3 つのフィールドのうち 2 つを変更し、結果を表示します。

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#3)]

## <a name="instantiating-and-using-a-named-tuple"></a>インスタンス化し、名前付きタプルを使用します。

インスタンス化、タプルのフィールドの既定の名前を使用してではなく、*名前付きタプル*タプルの要素を独自の名前を割り当てることで。 タプルのフィールドは割り当てられている名前でアクセスできます*または*によって既定の名前。 次の例では、最初のフィールドを明示的に指定する点を除いて前と同じ 3 つのタプルをインスタンス化`EventDate`、2 番目の`Name`、3 番目の`IsHoliday`します。 フィールドの値が表示されます、それらを変更し、フィールドの値が再び表示されます。

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#4)]

## <a name="inferred-tuple-element-names"></a>推論されたタプル要素の名前

Visual Basic 15.3 以降、Visual Basic はタプルの要素の名前を推測できます。明示的に割り当てる必要はありません。 推論されたタプル名は、変数のセットから組を初期化して、同じ変数名であるタプル要素名を使用する場合に便利です。 

次の例では、作成、`stateInfo`という名前の要素を明示的に 3 つを含むタプルが`state`、 `stateName`、および`capital`します。 要素の名前付けに注意してください、タプルの初期化ステートメントが同じ名前の変数の値だけの名前付き要素に割り当てられます。

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#1)]
 
要素と変数の名前が同じであるため、Visual Basic コンパイラは、次の例として、フィールドの名前を推測できます。

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#2)]

推論されたタプル要素名を有効にするには、Visual Basic プロジェクトで使用する Visual Basic コンパイラのバージョンを定義する必要があります (\*.vbproj) ファイル。 

```xml 
<PropertyGroup> 
  <LangVersion>15.3</LangVersion> 
</PropertyGroup> 
```

バージョン番号は 15.3 以降、Visual Basic コンパイラの任意のバージョンを指定できます。 特定のコンパイラ バージョンをハードコーディングするのではなく指定することも"Latest"の値として`LangVersion`システムにインストールされている Visual Basic コンパイラの最新バージョンでコンパイルします。

詳細については、次を参照してください。 [Visual Basic の言語バージョンを設定](../../../language-reference/configure-language-version.md)します。

場合によっては、Visual Basic コンパイラが、候補名からタプル要素名を推論できませんなどを使用して、既定の名前は、タプルのフィールドを参照のみ`Item1`、`Item2`など。不足している機能には次が含まれます。

- 候補名は、`Item3`、`Rest`、`ToString` などのように、タプルのメンバーの名前と同じです。

- 候補名がタプルで重複しています。
 
フィールドの名前の推論が失敗すると、Visual Basic は、コンパイラ エラーを生成しませんもは実行時にスローされる例外です。 代わりに、タプルのフィールド参照する必要が、定義済みの名前でなど`Item1`と`Item2`します。 
  
## <a name="tuples-versus-structures"></a>構造体とタプル

Visual Basic のタプルは、**System.ValueTuple** ジェネリック型の 1 つのインスタンスであるタイプ型です。 たとえば、前の例で定義された `holiday`のタプルは <xref:System.ValueTuple%603> 構造体のインスタンスです。 データ用の軽量コンテナーとなるように設計されています。 タプルは簡単に複数のデータ項目を含むオブジェクトを作成することを目的としているため、カスタム構造の持ついくつかの機能が不足している可能性があります。 不足している機能には次が含まれます。

- カスタム メンバー。 タプルの独自のプロパティ、メソッド、またはイベントを定義することはできません。

- 検証します。 フィールドに割り当てられているデータを検証することはできません。

- 不変性。 Visual Basic のタプルは変更可能です。 これに対し、カスタム構造ではインスタンスを変更できるようにするかどうかを制御できます。

カスタム メンバー、プロパティやフィールドの検証、不変性が重要な場合は、Visual Basic を使用する必要があります[構造](../../../language-reference/statements/structure-statement.md)カスタム値の型を定義するステートメント。

Visual Basic のタプルのメンバーを継承してその**ValueTuple**型。 フィールドだけでなく、次のメソッドが含まれます。

| メンバー | 説明 |
| ---|---|
| CompareTo | 現在のタプルを同じ数の要素を持つ別のタプルと比較します。 |
| Equals | 現在のタプルが別のタプルまたはオブジェクトと等しいかどうかを判断します。 |
| GetHashCode | 現在のインスタンスのハッシュ コードを計算します。 |
| ToString | このタプルでは、形式の文字列表現を返します`(Item1, Item2...)`ここで、`Item1`と`Item2`タプルのフィールドの値を表します。 |

さらに、 **ValueTuple**型実装<xref:System.Collections.IStructuralComparable>と<xref:System.Collections.IStructuralEquatable>インターフェイスで、使用する顧客の比較子を定義できます。

## <a name="assignment-and-tuples"></a>割り当てとタプル

Visual Basic では、同じ数のフィールドがあるタプル型間での割り当てをサポートします。 次のいずれかが true の場合、フィールドの型を変換できます。

- ソースとターゲットのフィールドは、同じ型です。

- ターゲットの型に、ソースの種類の拡大 (または暗黙的な) 変換が定義されます。 

- `Option Strict` `On`対象の型に、元の型の縮小 (または明示的な) 変換が定義されているとします。 この変換は、元の値が対象の型の範囲外の場合、例外をスローできます。

他の変換は、割り当てでは考慮されません。 タプル型間で許可されている割り当ての種類を見てみましょう。

以降の例で使用されている変数について考えます。

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#1)]

最初の 2 つの変数では、`unnamed`と`anonymous`、セマンティック名が、フィールドはありません。 フィールド名は、既定`Item1`と`Item2`します。 最後の 2 つの変数では、`named`と`differentName`セマンティック フィールドの名前します。 この 2 つのタプルでは、フィールド名が異なっていることに注意してください。

すべての 4 つのタプルは同じ呼ばれるフィールド (「アリティ」)、数を持ち、これらのフィールドの型は同じです。 このため、これらの割り当てはすべて機能します。

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#2)]

タプルの名前が割り当てられていないことに注意してください。 フィールドの値は、タプルのフィールドの順序に従って割り当てられます。

最後に、割り当てることができることに注意してください、`named`するタプル、`conversion`タプル、にもかかわらずの最初のフィールド`named`は、`Integer`の最初のフィールドと`conversion`は、 `Long`。 変換するために、この割り当てが成功、`Integer`を`Long`は拡大変換です。

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#3)]

異なる数のフィールドを持つタプルを割り当てることはできません。

```vb
' Does not compile.
' VB30311: Value of type '(Integer, Integer, Integer)' cannot be converted
'          to '(Answer As Integer, Message As String)'
var differentShape = (1, 2, 3)
named = differentShape
```

## <a name="tuples-as-method-return-values"></a>メソッドの戻り値としてのタプル

メソッドは、値は 1 つだけを返すことができます。 多くの場合、ただしたいメソッドの呼び出しを複数の値を返します。 この制限を回避するいくつかの方法はあります。

- できるプロパティを作成するカスタム クラスまたは構造体がまたはのフィールドは、メソッドによって返される値。 つまり、重量級のソリューションです。メソッドの呼び出しから値を取得するが唯一の目的は、カスタム型を定義することが必要です。

- メソッドから 1 つの値を返すし、メソッドへの参照で渡すことによって、残りの値を返すことができます。 これには、変数と参照渡しで渡す変数の値を上書きしてしまうリスクをインスタンス化のオーバーヘッドが含まれます。

- 複数の戻り値を取得するライトウェイト ソリューションを提供するタプルを使用できます。

たとえば、 **TryParse** .NET の戻り値でメソッドを`Boolean`解析操作が成功したかどうかを示す値です。 メソッドへの参照によって渡された変数では、解析操作の結果が返されます。 呼び出しでは通常などの解析メソッド<xref:System.Int32.TryParse%2A?displayProperty=nameWithType>次のようになります。

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#1)]

呼び出しのラップがある場合、解析操作からタプルを返しますことができます、<xref:System.Int32.TryParse%2A?displayProperty=nameWithType>方法では、独自のメソッド。 次の例では、`NumericLibrary.ParseInteger`呼び出し、<xref:System.Int32.TryParse%2A?displayProperty=nameWithType>メソッドを 2 つの要素で名前付きタプルを返します。 

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#2)]

次のようなコードでメソッドを呼び出してことができます。

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#3)]

## <a name="visual-basic-tuples-and-tuples-in-the-net-framework"></a>Visual Basic のタプルと、.NET Framework 内のタプル

Visual Basic のタプルは、.NET Framework 4.7 で導入された **System.ValueTuple** ジェネリック型の 1 つのインスタンスです。 .NET Framework には、汎用の **System.Tuple** クラスのセットも含まれます。 ただし、これらのクラスは Visual Basic のタプルおよび **System.ValueTuple** とは次のいくつかの面で異なります。

- **タプル** クラスの要素は、`Item1`、`Item2`などの名前を持つプロパティです。 Visual Basic のタプルおよび **ValueTuple** においてタプル要素はフィールドです。

- 要素にわかりやすい名前を割り当てることはできません、**タプル**インスタンスまたはを**ValueTuple**インスタンス。 Visual Basic を使用すると、フィールドの意味を伝える名前を割り当てることができます。

- **タプル** インスタンスのプロパティは読み取り専用で、タプルは変更できません。 Visual Basic のタプルおよび **ValueTuple** 型では、タプルのフィールドは読み取り/書き込み可能で、タプルは変更できます。

- 汎用の**タプル**型は参照型です。 これらの**タプル**型を使用することはオブジェクトの割り当てを意味します。 ホット パスでは、これがアプリケーションのパフォーマンスに大きな影響を与えることがあります。 Visual Basic のタプルと **ValueTuple** 型は値型です。

<xref:System.TupleExtensions> クラスの拡張メソッドによって、簡単に Visual Basic のタプルと .NET **タプル** オブジェクト間の変換がしやすくなります。 **ToTuple** メソッドは、Visual Basic のタプルを .NET **タプル** オブジェクトに変換し、**ToValueTuple** メソッドは .NET **タプル** オブジェクトを Visual Basic のタプルに変換します。

次の例ではタプルを作成し、.NET **タプル** オブジェクトを変換し、Visual Basic のタプルに変換し直します。 この例では、このタプルを元のタプルと比較して、それらが等しいことを確認します。

[!code-vb[Convert](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple2.vb#1)]

## <a name="see-also"></a>関連項目

- [Visual Basic の言語リファレンス](index.md)
