---
title: コレクションに関するガイドライン
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 297b8f1d-b11f-4dc6-960a-8e990817304e
author: KrzysztofCwalina
ms.openlocfilehash: a8e8672d71500478dbbe28512e413e8ada501f45
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61669050"
---
# <a name="guidelines-for-collections"></a>コレクションに関するガイドライン
具体的には、共通の特性を持つオブジェクトのグループを操作するように設計する任意の型は、コレクションを見なすことができます。 ほとんどを実装するには、このような型に適した<xref:System.Collections.IEnumerable>または<xref:System.Collections.Generic.IEnumerable%601>ので、このセクションでは私たちだけを検討するコレクションには、それらのインターフェイスの一方または両方を実装する型。  
  
 **X DO NOT** パブリック Api で弱く型指定されたコレクションを使用します。  
  
 すべての戻り値およびコレクションの項目を表すパラメーターの型 (これは、コレクションのパブリック メンバーにのみ適用) その基本型の正確な項目の種類があります。  
  
 **X DO NOT** 使用<xref:System.Collections.ArrayList>または<xref:System.Collections.Generic.List%601>パブリック Api でします。  
  
 これらの型は、パブリック Api ではなく、内部の実装で使用するためのデータ構造です。 `List<T>` パフォーマンスと電源の Api や柔軟性 cleanness を犠牲に最適です。 たとえば、値を返す場合`List<T>`はこれまでできませんをクライアント コードは、コレクションを変更すると、通知を受信できます。 また、`List<T>`など、多くのメンバーを公開する<xref:System.Collections.Generic.List%601.BinarySearch%2A>、便利なまたは多くのシナリオで適用可能ではないです。 次の 2 つのセクションでは、具体的にはパブリック Api で使用するために設計されています (抽象化) の種類について説明します。  
  
 **X DO NOT** 使用`Hashtable`または`Dictionary<TKey,TValue>`パブリック Api でします。  
  
 これらの型は、データ構造の内部の実装で使用するように設計します。 パブリック Api を使用する必要があります<xref:System.Collections.IDictionary>、 `IDictionary <TKey, TValue>`、またはいずれかまたは両方のインターフェイスを実装するカスタム型。  
  
 **X DO NOT** 使用<xref:System.Collections.Generic.IEnumerator%601>、 <xref:System.Collections.IEnumerator>、またはその他の型以外の戻り値の型として実装する、これらのインターフェイスのいずれかを`GetEnumerator`メソッドです。  
  
 型以外のメソッドから列挙子を返す`GetEnumerator`では使用できません、`foreach`ステートメント。  
  
 **X DO NOT** 両方を実装する`IEnumerator<T>`と`IEnumerable<T>`と同じ型にします。 非ジェネリック インターフェイスに適用される同じ`IEnumerator`と`IEnumerable`します。  
  
## <a name="collection-parameters"></a>コレクションのパラメーター  
 **✓ DO** パラメーター型として型の最小に特化した可能性のあるを使用します。 ほとんどのメンバーのパラメーターを使用して、コレクションを取得、`IEnumerable<T>`インターフェイス。  
  
 **X AVOID** を使用して<xref:System.Collections.Generic.ICollection%601>または<xref:System.Collections.ICollection>にアクセスするだけのパラメーターとして、`Count`プロパティです。  
  
 代わりに、`IEnumerable<T>`または`IEnumerable`と動的にオブジェクトが実装されているかどうかをチェック`ICollection<T>`または`ICollection`します。  
  
## <a name="collection-properties-and-return-values"></a>コレクションのプロパティと戻り値  
 **X DO NOT** 設定可能なコレクション プロパティを提供します。  
  
 ユーザーは、最初、コレクションをクリアし、新しい内容を追加して、コレクションの内容を置き換えることができます。 コレクション全体を置き換える一般的なシナリオがある場合は、提供することを検討してください、`AddRange`コレクション メソッド。  
  
 **✓ DO** を使用して`Collection<T>`またはそのサブクラスの`Collection<T>`プロパティまたは戻り値を表す読み取り/書き込みコレクション用です。  
  
 場合`Collection<T>`いくつかの要件を満たしていません (など、コレクションを実装する必要がありますいない<xref:System.Collections.IList>)、カスタム コレクションを使用して実装することによって`IEnumerable<T>`、 `ICollection<T>`、または<xref:System.Collections.Generic.IList%601>します。  
  
 **✓ DO** 使用<xref:System.Collections.ObjectModel.ReadOnlyCollection%601>のサブクラス`ReadOnlyCollection<T>`、まれなケースとして、または`IEnumerable<T>`プロパティまたは戻り値を表す読み取り専用のコレクションのです。  
  
 一般に、必要に応じて`ReadOnlyCollection<T>`します。 いくつかの要件を満たしていない場合 (など、コレクションを実装する必要がありますいない`IList`)、カスタム コレクションを使用して実装することによって`IEnumerable<T>`、 `ICollection<T>`、または`IList<T>`します。 カスタムの読み取り専用コレクションを実装する場合は、実装`ICollection<T>.IsReadOnly`を返す`true`します。  
  
 唯一のシナリオをサポートすることが順方向専用のイテレーションであることを確認する場所の場合、単に使用できます`IEnumerable<T>`します。  
  
 **✓ CONSIDER** ジェネリックの基本コレクションのサブクラスを使用して、コレクションを直接使用する代わりにします。  
  
 これによりより良い名前と、基本コレクション型に存在しないヘルパー メンバーを追加します。 これは高レベルの Api に特に当てはまります。  
  
 **✓ CONSIDER** のサブクラスを返す`Collection<T>`または`ReadOnlyCollection<T>`から非常に一般的に使用されるメソッドとプロパティ。  
  
 これにより、ヘルパー メソッドを追加またはコレクションの実装を将来を変更することが可能。  
  
 **✓ CONSIDER** コレクションに格納されている項目が一意キーを持つ場合、キー付きコレクションを使用する (名前、Id などです。)。 キー付きコレクションは、整数値とキーの両方でインデックスを作成できるを通常実装から継承することによってコレクション`KeyedCollection<TKey,TItem>`します。  
  
 キー付きコレクションは、通常より大きなメモリ フット プリントとには、メモリのオーバーヘッドが、キーを持つことのメリットを上回る場合、使用できません。  
  
 **X DO NOT** コレクション プロパティまたはコレクションを返すメソッドから null 値を返します。 代わりに、空のコレクションまたは空の配列を返します。  
  
 一般的な規則は、null および空の (アイテム 0) コレクションまたは配列があることと、同じ扱われます。  
  
### <a name="snapshots-versus-live-collections"></a>ライブのコレクションとスナップショット  
 時点の状態を表すコレクションは、スナップショットのコレクションと呼ばれます。 たとえば、データベース クエリから返される行を格納するコレクションは、スナップショットになります。 常に現在の状態を表すコレクションは、ライブのコレクションと呼ばれます。 たとえばのコレクション`ComboBox`項目は、ライブのコレクション。  
  
 **X DO NOT** プロパティからスナップショットのコレクションを返します。 プロパティは、ライブのコレクションを返す必要があります。  
  
 プロパティの getter の非常に軽量な操作があります。 スナップショットを返すには、o (n) 操作の内部コレクションのコピーを作成する必要があります。  
  
 **✓ DO** スナップショット コレクションまたはライブのいずれかを使用して`IEnumerable<T>`(またはそのサブタイプ) は揮発性であるコレクションを表現する (つまり、変更可能なコレクションを明示的に変更することがなく)。  
  
 一般に、共有リソース (ディレクトリ内のファイルなど) を表すすべてのコレクションは、揮発性です。 などのコレクションは、非常に困難か不可能な実装は単純に順方向専用の列挙しない限り、ライブのコレクションとして実装されます。  
  
## <a name="choosing-between-arrays-and-collections"></a>配列とコレクションの選択  
 **✓ DO** コレクションを配列よりも優先されます。  
  
 コレクションの内容をより細かく制御するには、時間の経過と共に進化させることができますおよびがより使いやすくします。 さらに、読み取り専用のシナリオの配列を使用するのでお勧め、配列の複製のコストは膨大です。 使いやすさの調査によると、一部の開発者は安心コレクション ベースの Api を使用します。  
  
 ただし、低レベルの Api を開発している場合、読み取り/書き込みシナリオの配列を使用する方がよい場合があります。 配列である、小さいメモリ フット プリント、ワーキング セットを軽減して、配列内の要素へのアクセスが高速、ランタイムによって最適化されています。  
  
 **✓ CONSIDER** 低レベルの Api でのメモリ消費量を最小限に抑えるし、パフォーマンスを最大化する配列を使用します。  
  
 **✓ DO** バイトのコレクションではなくバイト配列を使用します。  
  
 **X DO NOT** プロパティをプロパティ getter を呼び出すたびに新しい配列 (内部の配列のコピーなど) を返す必要がある場合、プロパティの配列を使用します。  
  
## <a name="implementing-custom-collections"></a>カスタム コレクションを実装します。  
 **✓ CONSIDER** から継承する`Collection<T>`、 `ReadOnlyCollection<T>`、または`KeyedCollection<TKey,TItem>`新しいコレクションを設計するとき。  
  
 **✓ DO** 実装`IEnumerable<T>`新しいコレクションを設計するとき。 実装を検討`ICollection<T>`またはでも`IList<T>`適切な場所。  
  
 このようなカスタム コレクションを実装する場合を確立する API パターンに従う`Collection<T>`と`ReadOnlyCollection<T>`可能な限りです。 つまり、同じメンバーを明示的に実装する、これら 2 つのコレクション名、およびのように、パラメーターの名前を付けます。  
  
 **✓ CONSIDER** 非ジェネリック コレクション インターフェイスを実装する (`IList`と`ICollection`) 場合は、コレクションは多くの場合する Api に渡される入力としてこれらのインターフェイスを取得します。  
  
 **X AVOID** コレクションの概念とは無関係な複雑な Api を使用した型にコレクション インターフェイスを実装します。  
  
 **X DO NOT** など非ジェネリックの基本コレクションから継承`CollectionBase`です。 使用`Collection<T>`、 `ReadOnlyCollection<T>`、および`KeyedCollection<TKey,TItem>`代わりにします。  
  
### <a name="naming-custom-collections"></a>カスタム コレクションの名前を付ける  
 コレクション (実装する型`IEnumerable`) 主に 2 つの理由が作成されます。(既存のデータ構造とは別のパフォーマンス特性構造固有の操作と多くの場合は、新しいデータ構造を作成するには 1) (例: <xref:System.Collections.Generic.List%601>、 <xref:System.Collections.Generic.LinkedList%601>、 <xref:System.Collections.Generic.Stack%601>)、および (2) の特殊なコレクションを作成するには特定の項目セットを保持する (例: <xref:System.Collections.Specialized.StringCollection>)。 データ構造は、アプリケーションとライブラリの内部の実装で最もよく使用されます。 特殊化されたコレクションは、(プロパティとパラメーターの型) として Api で公開するには、主にします。  
  
 **✓ DO** を実装する抽象クラスの名前に「ディクショナリ」サフィックスを使用`IDictionary`または`IDictionary<TKey,TValue>`です。  
  
 **✓ DO** を実装する型の名前に「コレクション」サフィックスを使用`IEnumerable`(またはその子孫のいずれかの) 項目のリストを表すとします。  
  
 **✓ DO** カスタム データ構造に対する、適切なデータ構造の名前を使用します。  
  
 **X AVOID** コレクションの抽象化の名前に"LinkedList"または「ハッシュ テーブル、」などの特定の実装の暗黙的な任意のサフィックスを使用します。  
  
 **✓ CONSIDER** 項目の種類の名前を持つコレクションの名前を付けることです。 たとえば、型の項目を格納するコレクション`Address`(実装`IEnumerable<Address>`) 名前を指定する必要があります`AddressCollection`します。 プレフィックス"I"、項目の種類がインターフェイスである場合は、項目の型を省略できます。 コレクションではそのため、<xref:System.IDisposable>項目を呼び出すことができる`DisposableCollection`します。  
  
 **✓ CONSIDER** 対応する書き込み可能なコレクションが追加されるか、フレームワークに既に存在する場合に、読み取り専用コレクションの名前に"ReadOnly"プレフィックスを使用します。  
  
 たとえば、文字列の読み取り専用コレクションを呼び出す必要がある`ReadOnlyStringCollection`します。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *Pearson Education, Inc. からのアクセス許可によって了承を得て転載[Framework デザイン ガイドライン。規則、手法、および再利用可能な .NET ライブラリの第 2 版のパターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina、Brad 内容では、Microsoft Windows の開発シリーズの一部として、Addison-wesley Professional、2008 年 10 月 22日を公開します。*  
  
## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
- [使用方法のガイドライン](../../../docs/standard/design-guidelines/usage-guidelines.md)
