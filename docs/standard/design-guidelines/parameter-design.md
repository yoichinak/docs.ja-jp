---
title: パラメーターのデザイン
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines [.NET Framework], parameters
- members [.NET Framework], parameters
- names [.NET Framework], parameters
- parameters, design guidelines
- reserved parameters
ms.assetid: 3f33bf46-4a7b-43b3-bb78-1ffebe0dcfa6
author: KrzysztofCwalina
ms.openlocfilehash: 5a0f6e0fab5d0f2fe8574e348fc6b8ae726eeb99
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757405"
---
# <a name="parameter-design"></a>パラメーターのデザイン
このセクションでは、引数をチェックするためのガイドラインにセクションを含むパラメーターのデザインの大まかなガイドラインを提供します。 さらで説明されているガイドラインを参照する必要があります[パラメーターの名前付け](../../../docs/standard/design-guidelines/naming-parameters.md)します。  
  
 **✓ DO** メンバーで必要な機能を提供する少なくとも派生パラメーター型を使用します。  
  
 たとえば、コレクションを列挙し、コンソールには、各項目を印刷する方法を設計する必要があるとします。 このようなメソッドが受け取る必要があります<xref:System.Collections.IEnumerable>、パラメーターとしていない<xref:System.Collections.ArrayList>または<xref:System.Collections.IList>など。  
  
 **X DO NOT** 予約済みのパラメーターを使用します。  
  
 メンバーへの複数の入力は、将来のバージョンで必要な場合は、新しいオーバー ロードを追加できます。  
  
 **X DO NOT** ポインター、ポインターの配列または多次元配列をパラメーターとして受け取るメソッドがパブリックに公開します。  
  
 ポインターと多次元配列が正しく使用する比較的困難です。 ほとんどの場合、Api をパラメーターとしてこれらの型を防ぐために再設計できます。  
  
 **✓ DO** すべて配置`out`で値をすべてのパラメーターと`ref`パラメーター (除外パラメーター配列) のパラメーターの順序のオーバー ロード間の不整合が発生する場合でも (を参照してください[メンバーオーバー ロード](../../../docs/standard/design-guidelines/member-overloading.md))。  
  
 `out`パラメーターは、余分な戻り値として見なすことができ、理解しやすく、メソッドのシグネチャは、グループ化することです。  
  
 **✓ DO** メンバーをオーバーライドするときに名前のパラメーターまたはインターフェイス メンバーの実装で一貫しています。  
  
 これには、メソッド間の関係向上と通信します。  
  
### <a name="choosing-between-enum-and-boolean-parameters"></a>列挙型とブール型パラメーターの選択  
 **✓ DO** メンバーが 2 つ以上のブール型パラメーターを持っている場合は、列挙型を使用します。  
  
 **X DO NOT** ブール値を使用してない場合は、絶対に 3 つ以上の値が必要な表示できなくなります。  
  
 列挙型は、今後追加するため、値の余地を与えるので説明する列挙型に値を追加するすべての影響を考慮する必要があります[列挙型デザイン](../../../docs/standard/design-guidelines/enum.md)します。  
  
 **✓ CONSIDER** は本当に 2 つの状態の値であり、のみを使用してブール型プロパティを初期化するコンス トラクターのパラメーターのブール値を使用します。  
  
### <a name="validating-arguments"></a>引数の検証  
 **✓ DO** パブリック、プロテクト、または明示的に実装されたメンバーに渡される引数を検証します。 スロー <xref:System.ArgumentException?displayProperty=nameWithType>、または検証に失敗した場合、そのサブクラスのいずれか。  
  
 パブリックまたはプロテクト メンバー自体で発生する必ずしも必要はありません、実際の検証に注意してください。 プライベートまたは内部ルーチン内の下位レベルで実行できます。 重要な点は、エンドユーザーに公開されている領域全体が、引数を確認します。  
  
 **✓ DO** スロー <xref:System.ArgumentNullException> null 引数が渡され、メンバーが null の引数をサポートしていない場合。  
  
 **✓ DO** 列挙型のパラメーターを検証します。  
  
 列挙型の引数は列挙型で定義された範囲内になりますとは限りません。 CLR では、値が列挙型で定義されていない場合でも、任意の整数値を列挙型の値にキャストします。  
  
 **X DO NOT** 使用<xref:System.Enum.IsDefined%2A?displayProperty=nameWithType>enum の範囲を確認します。  
  
 **✓ DO** 変更可能な引数がありますが変更されている検証後に注意してください。  
  
 メンバーが機密性の高いセキュリティの場合は、コピーを作成し、検証および引数を処理することが推奨されます。  
  
### <a name="parameter-passing"></a>パラメーターの引き渡し  
 Framework デザイナーの観点からは、パラメーターの 3 つの主なグループ: 値渡しのパラメーター、`ref`パラメーター、および`out`パラメーター。  
  
 引数が値渡しのパラメーターで渡されると、メンバーは、実際に渡された引数のコピーを受け取ります。 引数が値型の場合、引数のコピーは、スタックに配置します。 引数が参照型の場合は、参照のコピーは、スタックに配置します。 パラメーターの値渡しを c#、VB.NET、および C++ では、既定値などの最も人気のある CLR 言語。  
  
 引数が渡された場合、`ref`パラメーター、メンバーはで渡される実際の引数への参照を受け取ります。 引数が値型の場合、引数への参照はスタックに配置します。 引数が参照型の場合は、参照への参照はスタックに配置します。 `Ref` パラメーターは、メンバーの呼び出し元によって渡される引数を変更する許可を使用できます。  
  
 `Out` パラメーターはのような`ref`パラメーターは、小さな違いがあります。 割り当てられていないし、前に、いくつかの値が割り当てられているメンバーの本文で読み取ることができません、パラメーターが最初と見なされます。 また、パラメーターは、メンバーを返す前に、いくつかの値を割り当てられるがあります。  
  
 **X AVOID** を使用して`out`または`ref`パラメーター。  
  
 使用して`out`または`ref`パラメーターには、ポインター、値型と参照型の違いの理解および複数の戻り値を持つメソッドの処理の使用経験が必要です。 また、間の差`out`と`ref`パラメーターはあまり理解されていません。 フレームワークの設計者、一般向けの設計ではユーザーがマスターの操作は期待できません`out`または`ref`パラメーター。  
  
 **X DO NOT** 参照型を参照渡しされます。  
  
 いくつかの例外の参照を交換するのに使用できるメソッドなど、規則があります。  
  
### <a name="members-with-variable-number-of-parameters"></a>可変個のパラメーターを持つメンバー  
 メンバーを可変個の引数を受け取ることができますが、配列パラメーターを提供することによって表現されます。 たとえば、<xref:System.String>次のメソッドを提供します。  
  
```  
public class String {  
    public static string Format(string format, object[] parameters);  
}  
```  
  
 ユーザーが呼び出すことができますし、<xref:System.String.Format%2A?displayProperty=nameWithType>メソッドは、次のようにします。  
  
 `String.Format("File {0} not found in {1}",new object[]{filename,directory});`  
  
 配列パラメーターに c# params キーワードを追加すると、いわゆる params 配列パラメーターにパラメーターを変更し、一時配列を作成するショートカットを提供します。  
  
```  
public class String {  
    public static string Format(string format, params object[] parameters);  
}  
```  
  
 これにより、引数リスト内で直接、配列要素を渡すことによって、メソッドを呼び出すユーザー。  
  
 `String.Format("File {0} not found in {1}",filename,directory);`  
  
 パラメーター リストの最後のパラメーターにのみ、params キーワードを追加できることに注意してください。  
  
 **✓ CONSIDER** 要素の数が少ない配列を渡すエンドユーザーが予想される場合、配列パラメーターに、params キーワードを追加します。 多数の要素が渡されることに共通のシナリオと予想される場合は、ユーザーが、これら要素をインラインを渡していない可能性がありますし、そのため、params キーワードは必要はありません。  
  
 **X AVOID** があれば、呼び出し元はほとんどの場合、入力既に配列内に params 配列を使用します。  
  
 たとえば、バイトの配列パラメーターを持つメンバーは、個々 のバイトを渡すことによってほとんどないというは。 このため、.NET Framework でバイト配列パラメーターは、params キーワードを使用しないでください。  
  
 **X DO NOT** params 配列パラメーターを受け取るメンバーによって、配列が変更された場合、params 配列を使用します。  
  
 多くのコンパイラが呼び出しサイトで一時配列に、メンバーの引数を有効にするため、配列は、一時オブジェクトである可能性があり、そのため、配列への変更は失われます。  
  
 **✓ CONSIDER** 単純なオーバー ロードで、params キーワードを使用する場合でもより複雑なオーバー ロードでは使用できませんでした。  
  
 すべてのオーバー ロードである場合でも、1 つのオーバー ロードで params 配列を持つユーザーは値のかどうかを自問します。  
  
 **✓ DO** パラメーターを params キーワードを使用できるようにすることです。  
  
 **✓ CONSIDER** 非常にパフォーマンスが重視される Api の引数の数が少ない呼び出しに対して特別なオーバー ロードとコード パスを提供します。  
  
 これにより、引数の数が少ない、API が呼び出されたときに、配列オブジェクトを作成しないようにします。 配列パラメーターの単数形を取得し、数値のサフィックスを追加することによって、パラメーターの名前を形成します。  
  
 全体のコード パスを特別なケースに配列を作成するだけでなくより一般的なメソッドを呼び出す場合、これを行うだけする必要があります。  
  
 **✓ DO** params 配列引数として null を渡すことがあります。  
  
 配列が処理する前に null でないことを検証する必要があります。  
  
 **X DO NOT** を使用して、`varargs`メソッド、それ以外の場合、省略記号と呼ばれます。  
  
 C++ などのいくつかの CLR 言語という変数パラメーター リストを渡すための別の規則のサポート`varargs`メソッド。 CLS 準拠ではないために、規則は、フレームワークでは使用されませんする必要があります。  
  
### <a name="pointer-parameters"></a>ポインター パラメーター  
 一般に、ポインターがマネージ コードを適切に設計されたフレームワークのパブリック アクセスの領域には表示されません。 ほとんどの場合、ポインターをカプセル化する必要があります。 ただし、ポインターは相互運用性の理由から、必要な場合によっては、適切なポインターを使用して、このような場合は。  
  
 **✓ DO** ポインターが CLS 準拠ではないために、ポインター引数を受け取り、メンバーの代替を提供します。  
  
 **X AVOID** 高い引数のポインター引数のチェックを実行します。  
  
 **✓ DO** 共通ポインターに関連する規則を伴うメンバーをデザインするときに従う必要です。  
  
 たとえばは、開始インデックスを渡す必要が単純なポインターの算術演算は、同じ結果に使用できるため、  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *Pearson Education, Inc. からのアクセス許可によって了承を得て転載[Framework デザイン ガイドライン。規則、手法、および再利用可能な .NET ライブラリの第 2 版のパターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina、Brad 内容では、Microsoft Windows の開発シリーズの一部として、Addison-wesley Professional、2008 年 10 月 22日を公開します。*  
  
## <a name="see-also"></a>関連項目

- [メンバーのデザインのガイドライン](../../../docs/standard/design-guidelines/member.md)
- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
