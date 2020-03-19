---
title: クラス、構造体、およびインターフェイスの名前
ms.date: 10/22/2008
helpviewer_keywords:
- type names, guidelines
- classes [.NET Framework], names
- enumerations [.NET Framework], names
- names [.NET Framework], interfaces
- common type names
- names [.NET Framework], type names
- names [.NET Framework], classes
- interfaces [.NET Framework], names
- generic type parameters
ms.assetid: 87a4b0da-ed64-43b1-ac43-968576c444ce
ms.openlocfilehash: 2c528348c0e84037a80df9797c56f03b51c73adc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401239"
---
# <a name="names-of-classes-structs-and-interfaces"></a>クラス、構造体、およびインターフェイスの名前
次の命名規則は、一般的な型の命名に適用されます。

 クラスや構造体に、PascalCasing を使用して、名詞または名詞句を使用して✔️します。

 これにより、型名とメソッドが動詞句で指定されているのが区別されます。

 ✔️は、形容詞句、または名詞や名詞句を使用してインタフェースに名前を付けます。

 名詞や名詞句はめったに使用されず、型がインターフェイスではなく抽象クラスであるべきであることを示している場合があります。

 ❌クラス名にプレフィックス ("C"など) を付けないでください。

 ✔️ CONSIDER 基底クラスの名前で派生クラスの名前を終了します。

 これは非常に読みやすく、関係を明確に説明します。 コードの例としては`ArgumentOutOfRangeException`、`Exception`の一種である、 と`SerializableAttribute`の一種である`Attribute`、 が挙げられます。 しかし、このガイドラインを適用する際には、合理的な判断を下す必要があります。たとえば、`Button`クラスは一種の`Control`イベントですが`Control`、その名前には表示されません。

 型がインターフェイスであることを示すために、DO プレフィックスインターフェイス名を I という文字で✔️します。

 例えば、(`IComponent`名詞)、(`ICustomAttributeProvider`名詞句)、および`IPersistable`(形容詞)は適切なインタフェース名である。 他の型名と同様に、省略形は避けてください。

 ✔️は、クラスがインターフェイスの標準実装である class-interface ペアを定義する場合、インターフェイス名の "I" プレフィックスだけが名前を異なることを確認します。

## <a name="names-of-generic-type-parameters"></a>ジェネリック型パラメーターの名前
 ジェネリックは .NET Framework 2.0 に追加されました。 この機能は、*型パラメーター*と呼ばれる新しい種類の識別子を導入しました。

 ✔️は、単一文字の名前が完全にわかりやすい名前であり、わかりやすい名前が値を追加しない限り、ジェネリック型パラメーターにわかりやすい名前を付けます。

 ✔️ 1`T`文字の型パラメーターを持つ型の型パラメーター名として使用することを検討してください。

```csharp
public int IComparer<T> { ... }
public delegate bool Predicate<T>(T item);
public struct Nullable<T> where T:struct { ... }
```

 ✔️ DO プレフィックスの説明型`T`パラメーター名に.

```csharp
public interface ISessionChannel<TSession> where TSession : ISession {
    TSession Session { get; }
}
```

 ✔️ CONSIDER は、パラメーターの名前の型パラメーターに配置される制約を示します。

 たとえば、制約された`ISession`パラメーターは 、 という`TSession`名前になることがあります。

## <a name="names-of-common-types"></a>共通型の名前
 ✔️は、特定の .NET Framework 型から派生した型に名前を付ける場合、または特定の .NET Framework 型を実装する場合に、次の表で説明されているガイドラインに従います。

|基本型|派生/実装型ガイドライン|
|---------------|------------------------------------------|
|`System.Attribute`|✔️は、カスタム属性クラスの名前に接尾辞 "Attribute" を追加します。|
|`System.Delegate`|イベントで使用されるデリゲートの名前にサフィックス "EventHandler" を追加✔️。<br /><br /> ✔️は、イベント ハンドラとして使用されるデリゲート以外のデリゲートの名前にサフィックス "Callback" を追加します。<br /><br /> ❌デリゲートに "Delegate" というサフィックスを追加しないでください。|
|`System.EventArgs`|✔️は、サフィックス "EventArgs" を追加します。|
|`System.Enum`|❌このクラスから派生しないでください。代わりに、使用する言語でサポートされているキーワードを使用します。たとえば、C# では、キーワードを`enum`使用します。<br /><br /> ❌"列挙" または "フラグ" というサフィックスを追加しないでください。|
|`System.Exception`|✔️ DO は、"例外" というサフィックスを追加します。|
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|✔️は、"辞書" というサフィックスを追加します。 これは`IDictionary`特定の種類のコレクションですが、このガイドラインは、次に示す一般的なコレクションのガイドラインよりも優先されます。|
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|✔️は、"コレクション" というサフィックスを追加します。|
|`System.IO.Stream`|✔️は、サフィックス"Stream"を追加します。|
|`CodeAccessPermission IPermission`|✔️は、"アクセス許可" というサフィックスを追加します。|

## <a name="naming-enumerations"></a>列挙体の名前付け
 列挙型の名前 (enum) は、一般に、標準の型の名前付け規則 (PascalCasing など) に従う必要があります。 ただし、列挙型に特に適用される追加のガイドラインがあります。

 ✔️値がビット フィールドでない限り、列挙型には単数型名を使用します。

 ✔️ DO では、値としてビット フィールドを持つ列挙体に複数形の型名を使用します。

 ❌列挙型名に "Enum" サフィックスを使用しないでください。

 ❌列挙型名に "フラグ" または "フラグ" サフィックスを使用しないでください。

 ❌列挙値名にプレフィックスを使用しないでください (たとえば、ADO 列挙型の "ad" やリッチ テキストの列挙型の場合は "rtf" など)。

 *2005年、2009年©マイクロソフト株式会社。すべての権利が予約されています。*

 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*

## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
- [名前付けのガイドライン](../../../docs/standard/design-guidelines/naming-guidelines.md)
