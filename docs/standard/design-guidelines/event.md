---
title: イベントのデザイン
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- pre-events
- events [.NET Framework], design guidelines
- member design guidelines, events
- event handlers [.NET Framework], event design guidelines
- post-events
- signatures, event handling
ms.assetid: 67b3c6e2-6a8f-480d-a78f-ebeeaca1b95a
ms.openlocfilehash: 78d765a7af77b1e6a6ecd483677cea2d4c6b0d5b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709427"
---
# <a name="event-design"></a>イベントのデザイン
イベントは、最も一般的に使用されるコールバックの形式です (フレームワークがユーザーコードを呼び出すことを許可するコンストラクト)。 その他のコールバックメカニズムには、デリゲート、仮想メンバー、およびインターフェイスベースのプラグインを使用するメンバーが含まれます。ユーザビリティ研究からのデータは、開発者の大半が、他のコールバック機構を使用しているよりもイベントを使用した方が快適であることを示しています. イベントは、Visual Studio と多くの言語に適切に統合されています。  
  
 イベントのグループは2つあることに注意してください。システムの状態が変更される前に発生するイベント (前のイベントと呼ばれます) と、状態の変更後に発生するイベント (ポストイベント) です。 前のイベントの例としては、`Form.Closing`があります。これは、フォームを閉じる前に発生します。 ポストイベントの例としては、`Form.Closed`があります。これは、フォームが閉じられた後に発生します。  
  
 **✓ DO** イベントではなく「"発生させる」や「トリガー」の「生成」という用語を使用  
  
 **✓ DO** 使用<xref:System.EventHandler%601?displayProperty=nameWithType>イベント ハンドラーとして使用する新しいデリゲートを手動で作成する代わりにします。  
  
 **✓ CONSIDER** のサブクラスを使用して<xref:System.EventArgs>イベントの引数としてイベントをイベント メソッドを処理するデータを実行する必要はありませんが確実でない限り、その場合は行うこともできます、`EventArgs`を直接入力します。  
  
 `EventArgs` を使用して API を直接発送した場合、互換性を損なうことなく、イベントに含まれるデータを追加することはできません。 サブクラスを使用する場合、最初は完全に空であっても、必要に応じてサブクラスにプロパティを追加できます。  
  
 **✓ DO** 各イベントを生成するプロテクト仮想メソッドを使用します。 これは、構造体、シールクラス、または静的イベントではなく、シールされていないクラスの非静的イベントにのみ適用されます。  
  
 メソッドの目的は、派生クラスがオーバーライドを使用してイベントを処理する方法を提供することです。 オーバーライドは、派生クラスの基底クラスのイベントを処理するための、より柔軟で高速で、より自然な方法です。 慣例として、メソッドの名前は "On" で始まり、その後にイベントの名前を指定する必要があります。  
  
 派生クラスは、オーバーライドでメソッドの基本実装を呼び出さないことを選択できます。 基底クラスが正常に動作するために必要なメソッドに処理を含めないで、これを準備してください。  
  
 **✓ DO** イベントを発生させる保護されたメソッドを 1 つのパラメーターを取得します。  
  
 パラメーターには `e` という名前を付け、イベント引数クラスとして型指定する必要があります。  
  
 **X DO NOT** 静的でないイベントを発生させる場合するセンダとして null を渡します。  
  
 **✓ DO** 静的イベントを発生させる場合するセンダとして null を渡します。  
  
 **X DO NOT** イベントを発生させるときにイベント データ パラメーターとして null を渡します。  
  
 イベント処理メソッドにデータを渡さない場合は、`EventArgs.Empty` を渡す必要があります。 開発者は、このパラメーターを null にすることを想定していません。  
  
 **✓ CONSIDER** エンドユーザーが取り消すことができるイベントを発生させます。 これは、前のイベントにのみ適用されます。  
  
 エンドユーザーがイベントをキャンセルできるようにするには、<xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> またはそのサブクラスをイベント引数として使用します。  
  
### <a name="custom-event-handler-design"></a>カスタムイベントハンドラーのデザイン  
 ジェネリックをサポートしていない以前のバージョンの CLR をフレームワークで使用する必要がある場合など、`EventHandler<T>` を使用できない場合があります。 このような場合は、カスタムイベントハンドラーデリゲートの設計と開発が必要になることがあります。  
  
 **✓ DO** イベント ハンドラーの void の戻り値の型を使用します。  
  
 イベントハンドラーは複数のイベント処理メソッド (場合によっては複数のオブジェクト) を呼び出すことができます。 イベント処理メソッドで値を返すことが許可された場合、イベントの呼び出しごとに複数の戻り値が返されます。  
  
 **✓ DO** を使用して`object`イベント ハンドラーの最初のパラメーターの型としてそれを呼び出すと`sender`です。  
  
 **✓ DO** を使用して<xref:System.EventArgs?displayProperty=nameWithType>またはそのサブクラスをイベント ハンドラーの 2 番目のパラメーターの型としてそれを呼び出すと`e`です。  
  
 **X DO NOT** イベント ハンドラーに次の 2 つ以上のパラメーターがあります。  
  
 *©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*  
  
 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*  
  
## <a name="see-also"></a>関連項目

- [メンバーのデザインのガイドライン](../../../docs/standard/design-guidelines/member.md)
- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
