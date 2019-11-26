---
title: 共通の属性
ms.date: 07/20/2015
ms.assetid: 11fe4894-1bf9-4525-a36b-cddcd3a5d22b
ms.openlocfilehash: 2889411779a275baa8c91862d4cac2f820d660d0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353528"
---
# <a name="common-attributes-visual-basic"></a>Common Attributes (Visual Basic)

This topic describes the attributes that are most commonly used in Visual Basic programs.

- [グローバル属性](#Global)

- [Obsolete 属性](#Obsolete)

- [Conditional 属性](#Conditional)

- [呼び出し元情報属性](#CallerInfo)

- [Visual Basic Attributes](#VB)

## <a name="Global"></a> グローバル属性

ほとんどの属性は、クラスやメソッドなど、特定の言語要素に適用されます。ただし、属性の中にはグローバルなものがあり、アセンブリまたはモジュール全体に適用されます。 たとえば、<xref:System.Reflection.AssemblyVersionAttribute> 属性は、次のように、バージョン情報をアセンブリに埋め込むときに使用できます。

```vb
<Assembly: AssemblyVersion("1.0.0.0")>
```

Global attributes appear in the source code after any top-level `Imports` statements and before any type, module, or namespace declarations. グローバル属性は複数のソース ファイルに指定できますが、それらのファイルは、1 つのコンパイル パスでコンパイルする必要があります。 For Visual Basic projects, global attributes are generally put in the AssemblyInfo.vb file (the file is created automatically when you create a project in Visual Studio).

アセンブリの属性は、アセンブリに関する情報を提供する値です。 これらは次のカテゴリに分けられます。

- アセンブリ ID 属性

- 情報属性

- アセンブリ マニフェスト属性

### <a name="assembly-identity-attributes"></a>アセンブリ ID 属性

アセンブリの ID は、名前、バージョン、カルチャの 3 つの属性によって識別されます (適用できる場合は厳密な名前も使用されます)。 アセンブリの完全な名前を形成するこれらの属性は、コード内でアセンブリを参照するときに必要になります。 アセンブリのバージョンとカルチャは、属性を使用して設定できます。 ただし名前の値は、コンパイラ、Visual Studio IDE の [[アセンブリ情報]](/visualstudio/ide/reference/assembly-information-dialog-box) ダイアログ ボックス、またはアセンブリ リンカー (AI.exe) によってアセンブリの作成時に設定されます。このとき、設定はアセンブリ マニフェストが含まれたファイルに基づきます。 <xref:System.Reflection.AssemblyFlagsAttribute> 属性は、アセンブリの複数のコピーが共存できるかどうかを指定します。

次の表に ID 属性を示します。

|属性|目的|
|---------------|-------------|
|<xref:System.Reflection.AssemblyName>|アセンブリの ID を完全に記述します。|
|<xref:System.Reflection.AssemblyVersionAttribute>|アセンブリのバージョンを指定します。|
|<xref:System.Reflection.AssemblyCultureAttribute>|アセンブリがサポートするカルチャを指定します。|
|<xref:System.Reflection.AssemblyFlagsAttribute>|同じコンピューター、同じプロセス、または同じアプリケーション ドメインでの side-by-side 実行をアセンブリがサポートするかどうかを指定します。|

### <a name="informational-attributes"></a>情報属性

情報属性は、追加の会社情報または製品情報をアセンブリに指定する場合に使用できます。 次の表は、<xref:System.Reflection?displayProperty=nameWithType> 名前空間で定義されている情報属性を示しています。

|属性|目的|
|---------------|-------------|
|<xref:System.Reflection.AssemblyProductAttribute>|アセンブリ マニフェストの製品名を指定するカスタム属性を定義します。|
|<xref:System.Reflection.AssemblyTrademarkAttribute>|アセンブリ マニフェストの商標を指定するカスタム属性を定義します。|
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|アセンブリ マニフェストの補足バージョンを指定するカスタム属性を定義します。|
|<xref:System.Reflection.AssemblyCompanyAttribute>|アセンブリ マニフェストの会社名を指定するカスタム属性を定義します。|
|<xref:System.Reflection.AssemblyCopyrightAttribute>|アセンブリ マニフェストの著作権を指定するカスタム属性を定義します。|
|<xref:System.Reflection.AssemblyFileVersionAttribute>|Win32 ファイル バージョン リソースの特定のバージョン番号を使用するようコンパイラに指示します。|
|<xref:System.CLSCompliantAttribute>|アセンブリが共通言語仕様 (CLS) に準拠しているかどうかを示します。|

### <a name="assembly-manifest-attributes"></a>アセンブリ マニフェスト属性

アセンブリ マニフェスト属性を使用すると、アセンブリ マニフェストの情報を指定できます。 ここには、タイトル、説明、既定の別名、構成が含まれます。 次の表は、<xref:System.Reflection?displayProperty=nameWithType> 名前空間で定義されているアセンブリ マニフェスト属性を示しています。

|属性|目的|
|---------------|-------------|
|<xref:System.Reflection.AssemblyTitleAttribute>|アセンブリ マニフェストのアセンブリのタイトルを指定するカスタム属性を定義します。|
|<xref:System.Reflection.AssemblyDescriptionAttribute>|アセンブリ マニフェストのアセンブリの説明を指定するカスタム属性を定義します。|
|<xref:System.Reflection.AssemblyConfigurationAttribute>|アセンブリ マニフェストのアセンブリの構成 (製品版やデバッグなど) を指定するカスタム属性を定義します。|
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|アセンブリ マニフェストのわかりやすい既定の別名を定義します。|

## <a name="Obsolete"></a> Obsolete 属性

`Obsolete` 属性は、使用が推奨されなくなったプログラム エンティティをマークします。 その後、非推奨の印が付いたエンティティが使用されるたびに、この属性の構成に従って警告かエラーが生成されます。 (例:

```vb
<System.Obsolete("use class B")>
Class A
    Sub Method()
    End Sub
End Class

Class B
    <System.Obsolete("use NewMethod", True)>
    Sub OldMethod()
    End Sub

    Sub NewMethod()
    End Sub
End Class
```

この例では、`Obsolete` 属性はクラス `A` とメソッド `B.OldMethod` に適用されています。 `B.OldMethod` に適用された属性コンストラクターの 2 番目の引数が `true` に設定されているため、このメソッドではコンパイル エラーが発生します。一方、クラス `A` が使用されると、警告が生成されます。 しかし、`B.NewMethod` の呼び出しでは、警告もエラーも生成されません。

最初の引数として属性コンストラクターに指定された文字列は、警告またはエラーの一部として表示されます。 たとえば、前の定義でこれを使用すると、次のコードで 2 つの警告と 1 つのエラーが生成されます。

```vb
' Generates 2 warnings:
' Dim a As New A
' Generate no errors or warnings:

Dim b As New B
b.NewMethod()

' Generates an error, terminating compilation:
' b.OldMethod()
```

クラス `A` の警告が 2 つ生成されます。1 つはクラス参照の宣言の警告で、もう 1 つはクラス コンストラクターの警告です。

`Obsolete` 属性は引数なしで使用できますが、対象の項目が古い理由と代用する項目の説明を加えておくことをお勧めします。

`Obsolete` 属性は、1 回だけ使用できる属性であり、属性を使用できる任意のエンティティに適用できます。 `Obsolete` は <xref:System.ObsoleteAttribute> の別名です。

## <a name="Conditional"></a> Conditional 属性

`Conditional` 属性を使用すると、プリプロセス識別子に依存したメソッドの実行を指定できます。 `Conditional` 属性は <xref:System.Diagnostics.ConditionalAttribute> の別名であり、メソッドまたは属性クラスに適用できます。

この例では、`Conditional` は、プログラム固有の診断情報の表示を有効または無効にするメソッドに適用されています。

```vb
#Const TRACE_ON = True
Imports System.Diagnostics

Module TestConditionalAttribute
    Public Class Trace
        <Conditional("TRACE_ON")>
        Public Shared Sub Msg(ByVal msg As String)
            Console.WriteLine(msg)
        End Sub

    End Class

    Sub Main()
        Trace.Msg("Now in Main...")
        Console.WriteLine("Done.")
    End Sub
End Module
```

`TRACE_ON` 識別子が定義されていない場合、トレース出力は表示されません。

`Conditional` 属性は、(リリース ビルドではなく) デバッグ ビルドのトレース機能とログ機能を有効にするために、`DEBUG` 識別子と共によく使用されます。これは次のようになります。

```vb
<Conditional("DEBUG")>
Shared Sub DebugMethod()

End Sub
```

条件付きの印が付いたメソッドが呼び出されると、指定のプリプロセッサ シンボルの有無に従って、呼び出しの実行か省略が決定されます。 シンボルが定義されている場合は呼び出しが実行され、定義されていない場合は省略されます。 次のように、`#if…#endif` ブロック内でメソッドを囲むよりも `Conditional` を使用した方が、すっきりとして洗練されているうえ、エラーも少なくなります。

```vb
#If DEBUG Then
    Sub ConditionalMethod()
    End Sub
#End If
```

条件付きメソッドは、クラスまたは構造体の宣言内のメソッドである必要があります。また、戻り値を持つことはできません。

### <a name="using-multiple-identifiers"></a>複数の識別子の使用

メソッドに複数の `Conditional` 属性が付いている場合、そのメソッドの呼び出しは、1 つ以上の条件付きシンボルが定義されているときに実行されます (つまり、シンボルは OR 演算子によって論理的にリンクされています)。 この例では、`A` と `B` のどちらかがあると、メソッドの呼び出しが実行されます。

```vb
<Conditional("A"), Conditional("B")>
Shared Sub DoIfAorB()

End Sub
```

AND 演算子で論理的にリンクされたシンボルの効果を実現するには、条件付きメソッドを連続して定義します。 たとえば、次の 2 番目のメソッドは、`A` と `B` が両方定義されている場合にのみ実行されます。

```vb
<Conditional("A")>
Shared Sub DoIfA()
    DoIfAandB()
End Sub

<Conditional("B")>
Shared Sub DoIfAandB()
    ' Code to execute when both A and B are defined...
End Sub
```

### <a name="using-conditional-with-attribute-classes"></a>属性クラスでの Conditional の使用

`Conditional` 属性は、属性クラスの定義にも適用できます。 この例では、カスタム属性 `Documentation` は、DEBUG が定義されている場合にのみ、情報をメタデータに追加します。

```vb
<Conditional("DEBUG")>
Public Class Documentation
    Inherits System.Attribute
    Private text As String
    Sub New(ByVal doc_text As String)
        text = doc_text
    End Sub
End Class

Class SampleClass
    ' This attribute will only be included if DEBUG is defined.
    <Documentation("This method displays an integer.")>
    Shared Sub DoWork(ByVal i As Integer)
        System.Console.WriteLine(i)
    End Sub
End Class
```

## <a name="CallerInfo"></a> 呼び出し元情報属性

呼び出し元情報の属性を使用すると、メソッドへの呼び出し元に関する情報を取得できます。 ソース コードのファイル パス、ソース コードの行番号、呼び出し元のメンバー名を取得できます。

メンバー呼び出し元情報を取得するには、省略可能なパラメーターに適用される属性を使用します。 省略可能な各パラメーターでは既定値が指定されます。 次の表は、<xref:System.Runtime.CompilerServices?displayProperty=nameWithType> 名前空間で定義されている呼び出し元情報の属性の一覧です。

|属性|説明|[種類]|
|---|---|---|
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|呼び出し元を含むソース ファイルのフル パスです。 これはコンパイル時のパスです。|`String`|
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|メソッドの呼び出し元であるソース ファイルの行番号。|`Integer`|
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|呼び出し元のメソッド名またはプロパティ名。 For more information, see [Caller Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).|`String`|

For more information about the Caller Info attributes, see [Caller Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).

## <a name="VB"></a> Visual Basic Attributes

The following table lists the attributes that are specific to Visual Basic.

|属性|目的|
|---------------|-------------|
|<xref:Microsoft.VisualBasic.ComClassAttribute>|Indicates to the compiler that the class should be exposed as a COM object.|
|<xref:Microsoft.VisualBasic.HideModuleNameAttribute>|Allows module members to be accessed using only the qualification needed for the module.|
|<xref:Microsoft.VisualBasic.VBFixedStringAttribute>|Specifies the size of a fixed-length string in a structure for use with file input and output functions.|
|<xref:Microsoft.VisualBasic.VBFixedArrayAttribute>|Specifies the size of a fixed array in a structure for use with file input and output functions.|

### <a name="comclassattribute"></a>COMClassAttribute

Use `COMClassAttribute` to simplify the process of creating COM components from Visual Basic. COM objects are considerably different from .NET Framework assemblies, and without `COMClassAttribute`, you need to follow a number of steps to generate a COM object from Visual Basic. For classes marked with `COMClassAttribute`, the compiler performs many of these steps automatically.

### <a name="hidemodulenameattribute"></a>HideModuleNameAttribute

Use `HideModuleNameAttribute` to allow module members to be accessed by using only the qualification needed for the module.

### <a name="vbfixedstringattribute"></a>VBFixedStringAttribute

Use `VBFixedStringAttribute` to force Visual Basic to create a fixed-length string. Strings are of variable length by default, and this attribute is useful when storing strings to files. The following code demonstrates this:

```vb
Structure Worker
    ' The runtime uses VBFixedString to determine
    ' if the field should be written out as a fixed size.
    <VBFixedString(10)> Public LastName As String
    <VBFixedString(7)> Public Title As String
    <VBFixedString(2)> Public Rank As String
End Structure
```

### <a name="vbfixedarrayattribute"></a>VBFixedArrayAttribute

Use `VBFixedArrayAttribute` to declare arrays that are fixed in size. Like Visual Basic strings, arrays are of variable length by default. This attribute is useful when serializing or writing data to files.

## <a name="see-also"></a>関連項目

- <xref:System.Reflection>
- <xref:System.Attribute>
- [Visual Basic のプログラミング ガイド](../../../../visual-basic/programming-guide/index.md)
- [属性](../../../../standard/attributes/index.md)
- [リフレクション (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [リフレクションを使用した属性へのアクセス (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
