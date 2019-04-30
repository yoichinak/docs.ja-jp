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
author: KrzysztofCwalina
ms.openlocfilehash: 530c68ea5342263acd07f8dc8a8c8ce889652503
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026446"
---
# <a name="event-design"></a>イベントのデザイン
イベントは、コールバック (ユーザー コードを呼び出すために、フレームワークを許可するコンストラクト) の最もよく使用される形式です。 その他のコールバック メカニズムには、デリゲート、仮想メンバー、およびインターフェイス ベースのプラグインを取得するメンバーが含まれます。ユーザビリティ調査からのデータは、開発者の大部分が快適よりも、その他のコールバック メカニズムを使用しているイベントを使用することを示します。 イベントは、Visual Studio と多くの言語で適切に統合されています。  
  
 イベントの 2 つのグループがあることに注意してください。 前のイベントと状態が変更した後に発生したイベントと呼ばれる、システムの変更の状態の前に発生したイベントには後のイベントが呼び出されます。 イベントの前の例があります`Form.Closing`フォームが閉じられる前にこれが発生します。 後のイベントの例となります`Form.Closed`フォームが閉じられた後にこれが発生します。  
  
 **✓ DO** イベントではなく「"発生させる」や「トリガー」の「生成」という用語を使用  
  
 **✓ DO** 使用<xref:System.EventHandler%601?displayProperty=nameWithType>イベント ハンドラーとして使用する新しいデリゲートを手動で作成する代わりにします。  
  
 **✓ CONSIDER** のサブクラスを使用して<xref:System.EventArgs>イベントの引数としてイベントをイベント メソッドを処理するデータを実行する必要はありませんが確実でない限り、その場合は行うこともできます、`EventArgs`を直接入力します。  
  
 API を使用して、お送りいただいた場合`EventArgs`互換性を損なうことがなく、イベントに実行されるようにデータを追加できなくを直接します。 サブクラスを使用する場合でも、最初に完全に空をできなく、サブクラス化するために必要なときにプロパティを追加します。  
  
 **✓ DO** 各イベントを生成するプロテクト仮想メソッドを使用します。 これは、封印されていないクラス、構造体、シール クラス、または静的イベントが上の非静的イベントに適用のみです。  
  
 メソッドの目的は、上書きを使用して、イベントを処理するために派生クラスの手段を提供します。 オーバーライドは、派生クラスで基底クラスのイベントを処理する柔軟性、高速化、およびより自然な方法です。 慣例により、メソッドの名前は"On"で開始する必要があり、イベントの名前の後にします。  
  
 派生クラスは、そのオーバーライドで、メソッドの基本実装を呼び出していないを選択できます。 正常に機能する基底クラスに必要なメソッドでどのような処理を含めないことでこれを準備します。  
  
 **✓ DO** イベントを発生させる保護されたメソッドを 1 つのパラメーターを取得します。  
  
 パラメーターを指定する必要があります`e`と、イベント引数クラスとして入力する必要があります。  
  
 **X DO NOT** 静的でないイベントを発生させる場合するセンダとして null を渡します。  
  
 **✓ DO** 静的イベントを発生させる場合するセンダとして null を渡します。  
  
 **X DO NOT** イベントを発生させるときにイベント データ パラメーターとして null を渡します。  
  
 渡す必要があります`EventArgs.Empty`イベント処理メソッドに、データの受け渡ししたくない場合。 開発者は、このパラメーターを null にするのにはないを期待します。  
  
 **✓ CONSIDER** エンドユーザーが取り消すことができるイベントを発生させます。 これは、前のイベントにのみ適用されます。  
  
 使用<xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType>またはエンドユーザーのイベントをキャンセルできるイベントの引数としてそのサブクラスです。  
  
### <a name="custom-event-handler-design"></a>カスタム イベント ハンドラーのデザイン  
 場合がある`EventHandler<T>`framework がジェネリックをサポートしていませんでしたが、CLR の以前のバージョンを使用する必要がある場合など、使用することはできません。 このような場合は、デザインおよびカスタム イベント ハンドラー デリゲートを作成する必要があります。  
  
 **✓ DO** イベント ハンドラーの void の戻り値の型を使用します。  
  
 イベント ハンドラーは、おそらく複数のオブジェクト上のメソッドを処理する複数のイベントを呼び出すことができます。 イベント処理メソッドが戻り値が許可された場合は、イベントの呼び出しごとの複数の戻り値があります。  
  
 **✓ DO** を使用して`object`イベント ハンドラーの最初のパラメーターの型としてそれを呼び出すと`sender`です。  
  
 **✓ DO** を使用して<xref:System.EventArgs?displayProperty=nameWithType>またはそのサブクラスをイベント ハンドラーの 2 番目のパラメーターの型としてそれを呼び出すと`e`です。  
  
 **X DO NOT** イベント ハンドラーに次の 2 つ以上のパラメーターがあります。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *Pearson Education, Inc. からのアクセス許可によって了承を得て転載[Framework デザイン ガイドライン。規則、手法、および再利用可能な .NET ライブラリの第 2 版のパターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina、Brad 内容では、Microsoft Windows の開発シリーズの一部として、Addison-wesley Professional、2008 年 10 月 22日を公開します。*  
  
## <a name="see-also"></a>関連項目

- [メンバーのデザインのガイドライン](../../../docs/standard/design-guidelines/member.md)
- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
