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
author: KrzysztofCwalina
ms.openlocfilehash: c0790cd20daf859ec81e2252dc9bce46673daf90
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945510"
---
# <a name="names-of-classes-structs-and-interfaces"></a>クラス、構造体、およびインターフェイスの名前
次の名前付けのガイドラインは、一般的な種類の名前付けに適用されます。  
  
 **✓ DO** 名前をクラスと構造体には名詞または名詞句を使用して pascal 表記を使用します。  
  
 これは、動詞句がという名前のメソッドと型名を区別します。  
  
 **✓ DO** 形容詞句、または場合によっては名詞または名詞句とインターフェイスの名前します。  
  
 名詞と名詞句をめったに使用する必要があり、抽象クラスとインターフェイスではなく、型があることを示している可能性があります。  
  
 **X DO NOT** クラス名のプレフィックス ("C"など) を指定します。  
  
 **✓ CONSIDER** 基底クラスの名前のクラスを派生の名前を終了します。  
  
 これは非常に読み取り可能であり、関係を明確に説明します。 これには、コードの例を示します:`ArgumentOutOfRangeException`は一種の`Exception`と`SerializableAttribute`が付いていないの`Attribute`します。 ただし、することが重要です。 このガイドラインを適用することで、適切な判断たとえば、`Button`クラスは、一種の`Control`イベントが`Control`名前に表示されません。  
  
 **✓ DO** インターフェイス名のプレフィックス文字では、型がインターフェイスであることを示します。  
  
 たとえば、 `IComponent` (わかりやすい名詞) `ICustomAttributeProvider` (名詞句) と`IPersistable`(形容詞) は適切なインターフェイスの名前です。 その他の型名と同様の省略形を回避します。  
  
 **✓ DO** だけで、"I"プレフィックスのインターフェイスの名前、クラスがインターフェイスの標準的な実装であるクラス – インターフェイスのペアを定義するときに名前が異なることを確認してください。  
  
## <a name="names-of-generic-type-parameters"></a>ジェネリック型パラメーターの名前  
 ジェネリックは、.NET Framework 2.0 に追加されました。 機能の導入と呼ばれる識別子の新しい種類*パラメーター入力*します。  
  
 **✓ DO** 1 文字の名前が完全にわかり、わかりやすい名前と値を追加していない場合を除き、わかりやすい名前を持つジェネリック型パラメーターの名前します。  
  
 **✓ CONSIDER** を使用して`T`の 1 文字の型パラメーターを 1 つの種類の型パラメーター名として。  
  
```  
public int IComparer<T> { ... }  
public delegate bool Predicate<T>(T item);  
public struct Nullable<T> where T:struct { ... }  
```  
  
 **✓ DO** 説明的な型パラメーター名をプレフィックス`T`です。  
  
```  
public interface ISessionChannel<TSession> where TSession : ISession {  
    TSession Session { get; }  
}  
```  
  
 **✓ CONSIDER** 制約を示す名前、パラメーターの型パラメーター上に配置します。  
  
 パラメーターの制約など`ISession`という`TSession`します。  
  
## <a name="names-of-common-types"></a>一般的な種類の名前  
 **✓ DO** から派生または特定の .NET Framework 型を実装する型の名前を付けるときは、次の表に説明されているガイドラインに従ってください。  
  
|基本型|型の派生実装ガイドライン|  
|---------------|------------------------------------------|  
|`System.Attribute`|**✓ DO** カスタム属性クラスの名前にサフィックス"Attribute"を追加します。|  
|`System.Delegate`|**✓ DO** イベントで使用されるデリゲートの名前にサフィックス"EventHandler"を追加します。<br /><br /> **✓ DO** 以外のイベント ハンドラーとして使用されているデリゲートの名前に"Callback"サフィックスを追加します。<br /><br /> **X DO NOT** 「代理」サフィックスをデリゲートに追加します。|  
|`System.EventArgs`|**✓ DO** "EventArgs です"というサフィックスを追加。|  
|`System.Enum`|**X DO NOT** 代わりに使用する言語でサポートされているキーワードを使用して; たとえば、C# の場合、次のように使用します。 このクラスから派生、`enum`キーワード。<br /><br /> **X DO NOT** 「列挙」または"Flag"サフィックスを追加|  
|`System.Exception`|**✓ DO** "Exception"サフィックスを追加|  
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|**✓ DO** 「ディクショナリ」というサフィックスを追加。 なお`IDictionary`は、コレクションの特定の型ですが、このガイドラインは次の一般的なコレクション ガイドラインより優先されます。|  
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|**✓ DO** 「コレクション」サフィックスを追加|  
|`System.IO.Stream`|**✓ DO** 「ストリームです」というサフィックスを追加。|  
|`CodeAccessPermission IPermission`|**✓ DO** 「権限」というサフィックスを追加。|  
  
## <a name="naming-enumerations"></a>名前付けの列挙型  
 一般に (列挙型とも呼ばれます) 列挙型の名前にすることは (pascal 表記を使用など) 標準型の名前付け規則に従う必要があります。 ただし、具体的には列挙型に適用される追加のガイドラインがあります。  
  
 **✓ DO** ビット フィールドがその値がない限り、列挙体の単数形の型名を使用します。  
  
 **✓ DO** ビット フィールドを持つ列挙体の複数形の型名を使用して値として、フラグ列挙型とも呼ばれます。  
  
 **X DO NOT** 列挙型の型名で、「列挙」サフィックスを使用します。  
  
 **X DO NOT** 「フラグを設定」を使用して、または"Flags"サフィックス列挙型では、名前を入力します。  
  
 **X DO NOT** リッチ テキストの列挙型などの列挙値の名前 (例:"ad"ADO 列挙型の場合。)、"rtf"に対して、プレフィックスを使用します。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *Pearson Education, Inc. からのアクセス許可によって了承を得て転載[Framework デザイン ガイドライン。規則、手法、および再利用可能な .NET ライブラリの第 2 版のパターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina、Brad 内容では、Microsoft Windows の開発シリーズの一部として、Addison-wesley Professional、2008 年 10 月 22日を公開します。*  
  
## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
- [名前付けのガイドライン](../../../docs/standard/design-guidelines/naming-guidelines.md)
