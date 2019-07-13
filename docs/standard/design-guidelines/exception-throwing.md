---
title: 例外のスロー
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions, throwing
- explicitly throwing exceptions
- throwing exceptions, design guidelines
ms.assetid: 5388e02b-52f5-460e-a2b5-eeafe60eeebe
author: KrzysztofCwalina
ms.openlocfilehash: 74eee418a3c87b335cdf96557c4e17b95aff7b58
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61669070"
---
# <a name="exception-throwing"></a>例外のスロー
このセクションで説明されている例外のスローのガイドラインには、実行エラーの意味を適切な定義が必要です。 メンバーが実行できないときに、実行エラーが発生します (どのようなメンバー名を意味します) を実行するように設計します。 たとえば場合、`OpenFile`メソッドが呼び出し元に、開いているファイル ハンドルを返すことはできませんで実行エラーと思われることです。  
  
 ほとんどの開発者には、0 または null 参照による除算などの使用状況のエラーの例外の使用に慣れてになります。 Framework では、例外は、実行エラーを含むすべてのエラー条件に対して使用されます。  
  
 **X DO NOT** エラー コードを返します。  
  
 例外は、フレームワークでエラーをレポートの主要な手段です。  
  
 **✓ DO** 例外をスローして、実行の失敗を報告します。  
  
 **✓ CONSIDER** 呼び出すことによって、プロセスを終了して`System.Environment.FailFast`(.NET Framework 2.0 の機能)、コードが安全に実行をさらにはない状況が発生すると、例外をスローする代わりにします。  
  
 **X DO NOT** 可能であれば、コントロールの通常のフローの例外を使用します。  
  
 を除き、システム障害と潜在的な競合状態の操作では、ユーザーは、例外をスローしないコードを記述できますよう、フレームワークの設計者は Api を設計する必要があります。 たとえば、ユーザーは、例外をスローしないコードを記述できますようにメンバーを呼び出す前に前提条件をチェックする方法を行うことができます。  
  
 別のメンバーの状態をチェックするために使用するメンバーは、テスト担当者と呼ばし、実際に作業を行うメンバーは、渡ってと呼ばれます。  
  
 Tester-doer パターンが、許容できないパフォーマンスのオーバーヘッドを持つことができます可能性があります。 このような場合は、いわゆる Try Parse パターンを考慮する必要があります (を参照してください[例外とパフォーマンス](../../../docs/standard/design-guidelines/exceptions-and-performance.md)詳細については)。  
  
 **✓ CONSIDER** パフォーマンス上の違いの例外をスローします。 1 秒あたり 100 を超える throw レートは、ほとんどのアプリケーションのパフォーマンスに著しい影響を与える可能性があります。  
  
 **✓ DO** ドキュメントによって公開されている呼び出し可能なメンバー、メンバーの違反のためにスローされる例外すべてではなく、システム障害) コントラクトおよびコントラクトの一部として扱われるようにします。  
  
 コントラクトの一部である例外は、[次へ] を 1 つのバージョンから変更しないでください (つまり、例外の種類を変更しないでください、および新しい例外を追加しない必要があります)。  
  
 **X DO NOT** かどうか throw をできるパブリック メンバーに基づいてにいくつかのオプションです。  
  
 **X DO NOT** パブリック メンバーの戻り値として例外を返すをまたは`out`パラメーター。  
  
 それらをスローする代わりに、パブリック Api からの例外を返すには、例外ベースのエラー報告のメリットが多数達成できないからです。  
  
 **✓ CONSIDER** 例外ビルダー メソッドを使用します。  
  
 さまざまな場所から同じ例外をスローする一般的です。 コードの肥大化を回避するには、例外を作成し、そのプロパティを初期化するヘルパー メソッドを使用します。  
  
 また、例外をスローするメンバーが得られないインライン化します。 Throw ステートメント ビルダー内を移動するインライン化するメンバーを許可する可能性があります。  
  
 **X DO NOT** 例外フィルター ブロックから例外をスローします。  
  
 例外フィルターで例外が発生、CLR で例外をキャッチし、フィルターは false を返します。 この動作は、フィルター実行して、明示的に false を返すことと区別することであり、デバッグが困難になります。  
  
 **X AVOID** 明示的に finally ブロックからの例外をスローします。 スローするメソッドの呼び出しから暗黙的にスローされた例外では、許容されます。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *Pearson Education, Inc. からのアクセス許可によって了承を得て転載[Framework デザイン ガイドライン。規則、手法、および再利用可能な .NET ライブラリの第 2 版のパターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina、Brad 内容では、Microsoft Windows の開発シリーズの一部として、Addison-wesley Professional、2008 年 10 月 22日を公開します。*  
  
## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
- [例外のデザインのガイドライン](../../../docs/standard/design-guidelines/exceptions.md)
