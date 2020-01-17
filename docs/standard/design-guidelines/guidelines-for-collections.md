---
title: コレクションに関するガイドライン
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 297b8f1d-b11f-4dc6-960a-8e990817304e
ms.openlocfilehash: 231d8b04c11f19c4440e184533e1eeaded72b70b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709323"
---
# <a name="guidelines-for-collections"></a>コレクションに関するガイドライン
一般的な特性を持つオブジェクトのグループを操作するために特に設計された型はすべて、コレクションと見なすことができます。 ほとんどの場合、このような型は <xref:System.Collections.IEnumerable> または <xref:System.Collections.Generic.IEnumerable%601>を実装するのに適しています。したがって、このセクションでは、これらのインターフェイスのいずれかまたは両方を実装する型のみをコレクションにすることを検討します。  
  
 **X DO NOT** パブリック Api で弱く型指定されたコレクションを使用します。  
  
 コレクションアイテムを表すすべての戻り値とパラメーターの型は、その基本型ではなく、完全な項目の種類である必要があります (これはコレクションのパブリックメンバーにのみ適用されます)。  
  
 **X DO NOT** 使用<xref:System.Collections.ArrayList>または<xref:System.Collections.Generic.List%601>パブリック Api でします。  
  
 これらの型は、パブリック Api ではなく、内部実装で使用するように設計されたデータ構造です。 `List<T>` は、Api と柔軟性を cleanness 使用することで、パフォーマンスと性能が最適化されています。 たとえば、`List<T>`を返した場合、クライアントコードがコレクションを変更したときに通知を受け取ることはできません。 また、`List<T>` は、多くのシナリオでは役に立たない、または適用できない多くのメンバー (<xref:System.Collections.Generic.List%601.BinarySearch%2A>など) を公開します。 次の2つのセクションでは、パブリック Api 専用に設計された型 (抽象化) について説明します。  
  
 **X DO NOT** 使用`Hashtable`または`Dictionary<TKey,TValue>`パブリック Api でします。  
  
 これらの型は、内部実装で使用するように設計されたデータ構造体です。 パブリック Api では、インターフェイスの1つまたは両方を実装する <xref:System.Collections.IDictionary>、`IDictionary <TKey, TValue>`、またはカスタム型を使用する必要があります。  
  
 **X DO NOT** 使用<xref:System.Collections.Generic.IEnumerator%601>、 <xref:System.Collections.IEnumerator>、またはその他の型以外の戻り値の型として実装する、これらのインターフェイスのいずれかを`GetEnumerator`メソッドです。  
  
 `GetEnumerator` 以外のメソッドから列挙子を返す型は、`foreach` ステートメントと共に使用することはできません。  
  
 **X DO NOT** 両方を実装する`IEnumerator<T>`と`IEnumerable<T>`と同じ型にします。 これは、非ジェネリックインターフェイス `IEnumerator` および `IEnumerable`にも当てはまります。  
  
## <a name="collection-parameters"></a>コレクションパラメーター  
 **✓ DO** パラメーター型として型の最小に特化した可能性のあるを使用します。 コレクションをパラメーターとして受け取るほとんどのメンバーは、`IEnumerable<T>` インターフェイスを使用します。  
  
 **X AVOID** を使用して<xref:System.Collections.Generic.ICollection%601>または<xref:System.Collections.ICollection>にアクセスするだけのパラメーターとして、`Count`プロパティです。  
  
 代わりに、`IEnumerable<T>` または `IEnumerable` を使用し、オブジェクトが `ICollection<T>` または `ICollection`を実装しているかどうかを動的に確認することを検討してください。  
  
## <a name="collection-properties-and-return-values"></a>コレクションのプロパティと戻り値  
 **X DO NOT** 設定可能なコレクション プロパティを提供します。  
  
 コレクションの内容を置き換えるには、まずコレクションをクリアしてから、新しい内容を追加します。 コレクション全体を置き換えることが一般的なシナリオである場合は、コレクションに `AddRange` メソッドを指定することを検討してください。  
  
 **✓ DO** を使用して`Collection<T>`またはそのサブクラスの`Collection<T>`プロパティまたは戻り値を表す読み取り/書き込みコレクション用です。  
  
 `Collection<T>` がいくつかの要件を満たしていない場合 (たとえば、コレクションで <xref:System.Collections.IList>を実装する必要がない場合) は、`IEnumerable<T>`、`ICollection<T>`、または <xref:System.Collections.Generic.IList%601>を実装してカスタムコレクションを使用します。  
  
 **✓ DO** 使用<xref:System.Collections.ObjectModel.ReadOnlyCollection%601>のサブクラス`ReadOnlyCollection<T>`、まれなケースとして、または`IEnumerable<T>`プロパティまたは戻り値を表す読み取り専用のコレクションのです。  
  
 一般に、`ReadOnlyCollection<T>`をお勧めします。 いくつかの要件を満たしていない場合 (コレクションで `IList`を実装する必要がない場合など) は、`IEnumerable<T>`、`ICollection<T>`、または `IList<T>`を実装してカスタムコレクションを使用します。 カスタムの読み取り専用コレクションを実装する場合は、`ICollection<T>.IsReadOnly` を実装して `true`を返します。  
  
 サポートするシナリオが、順方向専用イテレーションだけであることが確実な場合は、単に `IEnumerable<T>`を使用できます。  
  
 **✓ CONSIDER** ジェネリックの基本コレクションのサブクラスを使用して、コレクションを直接使用する代わりにします。  
  
 これにより、より適切な名前を使用したり、基本コレクション型に存在しないヘルパーメンバーを追加したりすることができます。 これは、特に高レベルの Api に適用されます。  
  
 **✓ CONSIDER** のサブクラスを返す`Collection<T>`または`ReadOnlyCollection<T>`から非常に一般的に使用されるメソッドとプロパティ。  
  
 これにより、後でヘルパーメソッドを追加したり、コレクションの実装を変更したりできるようになります。  
  
 **✓ CONSIDER** コレクションに格納されている項目が一意キーを持つ場合、キー付きコレクションを使用する (名前、Id などです。)。 キー付きコレクションは、整数とキーの両方でインデックスを作成できるコレクションで、通常は `KeyedCollection<TKey,TItem>`から継承することによって実装されます。  
  
 キー付きコレクションは、通常、メモリフットプリントが大きいため、メモリのオーバーヘッドがキーの利点よりも大きなメリットを上回る場合は使用しないでください。  
  
 **X DO NOT** コレクション プロパティまたはコレクションを返すメソッドから null 値を返します。 代わりに空のコレクションまたは空の配列を返します。  
  
 一般的な規則として、null と空の (0 項目) のコレクションまたは配列は同じように扱う必要があります。  
  
### <a name="snapshots-versus-live-collections"></a>スナップショットとライブコレクション  
 ある時点の状態を表すコレクションは、スナップショットコレクションと呼ばれます。 たとえば、データベースクエリから返された行を含むコレクションはスナップショットです。 常に現在の状態を表すコレクションは、live collections と呼ばれます。 たとえば、`ComboBox` 項目のコレクションはライブコレクションです。  
  
 **X DO NOT** プロパティからスナップショットのコレクションを返します。 プロパティはライブコレクションを返します。  
  
 プロパティの getter は、非常に軽量な操作である必要があります。 スナップショットを返すには、O (n) 操作で内部コレクションのコピーを作成する必要があります。  
  
 **✓ DO** スナップショット コレクションまたはライブのいずれかを使用して`IEnumerable<T>`(またはそのサブタイプ) は揮発性であるコレクションを表現する (つまり、変更可能なコレクションを明示的に変更することがなく)。  
  
 一般に、共有リソース (ディレクトリ内のファイルなど) を表すすべてのコレクションは揮発性です。 このようなコレクションは、実装が単なる順方向専用列挙子の場合を除き、ライブコレクションとして実装するのは非常に困難または不可能です。  
  
## <a name="choosing-between-arrays-and-collections"></a>配列とコレクションの選択  
 **✓ DO** コレクションを配列よりも優先されます。  
  
 コレクションを使用すると、コンテンツの制御が強化され、時間の経過と共に進化して、より使いやすくなります。 また、配列の複製にかかるコストが膨大であるため、読み取り専用のシナリオに配列を使用することはお勧めしません。 使いやすさの研究では、コレクションベースの Api を使用する開発者の方が快適であることがわかりました。  
  
 ただし、低レベルの Api を開発している場合は、読み取り/書き込みのシナリオで配列を使用する方が適切な場合があります。 配列のメモリフットプリントは小さくなるため、ワーキングセットを減らすことができます。また、配列内の要素へのアクセスは、ランタイムによって最適化されるため、より高速になります。  
  
 **✓ CONSIDER** 低レベルの Api でのメモリ消費量を最小限に抑えるし、パフォーマンスを最大化する配列を使用します。  
  
 **✓ DO** バイトのコレクションではなくバイト配列を使用します。  
  
 **X DO NOT** プロパティをプロパティ getter を呼び出すたびに新しい配列 (内部の配列のコピーなど) を返す必要がある場合、プロパティの配列を使用します。  
  
## <a name="implementing-custom-collections"></a>カスタムコレクションの実装  
 **✓ CONSIDER** から継承する`Collection<T>`、 `ReadOnlyCollection<T>`、または`KeyedCollection<TKey,TItem>`新しいコレクションを設計するとき。  
  
 **✓ DO** 実装`IEnumerable<T>`新しいコレクションを設計するとき。 `ICollection<T>` または `IList<T>` を実装することを検討してください。  
  
 このようなカスタムコレクションを実装する場合は、`Collection<T>` によって確立された API パターンに従い、できるだけ近い方法で `ReadOnlyCollection<T>` します。 つまり、同じメンバーを明示的に実装し、これらの2つのコレクションのようなパラメーターに名前を付けるなどです。  
  
 **✓ CONSIDER** 非ジェネリック コレクション インターフェイスを実装する (`IList`と`ICollection`) 場合は、コレクションは多くの場合する Api に渡される入力としてこれらのインターフェイスを取得します。  
  
 **X AVOID** コレクションの概念とは無関係な複雑な Api を使用した型にコレクション インターフェイスを実装します。  
  
 **X DO NOT** など非ジェネリックの基本コレクションから継承`CollectionBase`です。 代わりに `Collection<T>`、`ReadOnlyCollection<T>`、および `KeyedCollection<TKey,TItem>` 型を使用してください。  
  
### <a name="naming-custom-collections"></a>カスタムコレクションの名前付け  
 コレクション (`IEnumerable`を実装する型) は主に次の2つの理由で作成されます。 (1) 構造固有の操作を使用して新しいデータ構造を作成し、多くの場合、既存のデータ構造 (<xref:System.Collections.Generic.List%601>、<xref:System.Collections.Generic.LinkedList%601>、<xref:System.Collections.Generic.Stack%601>など) とは異なるパフォーマンス特性を作成する (例: <xref:System.Collections.Specialized.StringCollection>) データ構造は、アプリケーションとライブラリの内部実装で最もよく使用されます。 特に、特化されたコレクションは Api で公開されます (プロパティとパラメーターの型として)。  
  
 **✓ DO** を実装する抽象クラスの名前に「ディクショナリ」サフィックスを使用`IDictionary`または`IDictionary<TKey,TValue>`です。  
  
 **✓ DO** を実装する型の名前に「コレクション」サフィックスを使用`IEnumerable`(またはその子孫のいずれかの) 項目のリストを表すとします。  
  
 **✓ DO** カスタム データ構造に対する、適切なデータ構造の名前を使用します。  
  
 **X AVOID** コレクションの抽象化の名前に"LinkedList"または「ハッシュ テーブル、」などの特定の実装の暗黙的な任意のサフィックスを使用します。  
  
 **✓ CONSIDER** 項目の種類の名前を持つコレクションの名前を付けることです。 たとえば、`Address` 型の項目を格納するコレクション (`IEnumerable<Address>`を実装する) の名前は `AddressCollection`にする必要があります。 項目の種類がインターフェイスの場合は、項目の種類の "I" プレフィックスを省略できます。 したがって、<xref:System.IDisposable> 項目のコレクションを `DisposableCollection`と呼び出すことができます。  
  
 **✓ CONSIDER** 対応する書き込み可能なコレクションが追加されるか、フレームワークに既に存在する場合に、読み取り専用コレクションの名前に"ReadOnly"プレフィックスを使用します。  
  
 たとえば、文字列の読み取り専用コレクションを `ReadOnlyStringCollection`と呼び出す必要があります。  
  
 *©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*  
  
 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*  
  
## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
- [使用方法のガイドライン](../../../docs/standard/design-guidelines/usage-guidelines.md)
