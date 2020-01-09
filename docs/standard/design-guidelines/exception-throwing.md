---
title: 例外のスロー
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions, throwing
- explicitly throwing exceptions
- throwing exceptions, design guidelines
ms.assetid: 5388e02b-52f5-460e-a2b5-eeafe60eeebe
ms.openlocfilehash: 7d1b63e5fde57cbe37a1250d16b6bf74a2d5dc8e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709401"
---
# <a name="exception-throwing"></a>例外のスロー
このセクションで説明する例外をスローするガイドラインでは、実行エラーの意味を適切に定義する必要があります。 実行エラーは、メンバーが実行するように設計された処理を実行できない場合 (メンバー名が示すもの) に発生します。 たとえば、`OpenFile` メソッドが、開いているファイルハンドルを呼び出し元に返すことができない場合、実行エラーと見なされます。  
  
 ほとんどの開発者は、0または null 参照による除算などの使用エラーに対して、例外を使用することに慣れています。 フレームワークでは、実行エラーを含むすべてのエラー条件に対して例外が使用されます。  
  
 **X DO NOT** エラー コードを返します。  
  
 例外は、フレームワークでエラーを報告するための主な手段です。  
  
 **✓ DO** 例外をスローして、実行の失敗を報告します。  
  
 **✓ CONSIDER** 呼び出すことによって、プロセスを終了して`System.Environment.FailFast`(.NET Framework 2.0 の機能)、コードが安全に実行をさらにはない状況が発生すると、例外をスローする代わりにします。  
  
 **X DO NOT** 可能であれば、コントロールの通常のフローの例外を使用します。  
  
 システムエラーや潜在的な競合状態による操作を除き、フレームワークデザイナーは、ユーザーが例外をスローしないコードを記述できるように Api を設計する必要があります。 たとえば、例外をスローしないコードをユーザーが記述できるように、メンバーを呼び出す前に事前条件を確認する方法を提供できます。  
  
 別のメンバーの事前条件を確認するために使用されるメンバーは、テスト担当者と呼ばれることもあり、実際に作業を行うメンバーは doer と呼ばれます。  
  
 テスト担当者-Doer パターンでは、許容できないパフォーマンスのオーバーヘッドが発生する場合があります。 このような場合は、いわゆる Try 解析パターンを考慮する必要があります (詳細については、「[例外とパフォーマンス](../../../docs/standard/design-guidelines/exceptions-and-performance.md)」を参照してください)。  
  
 **✓ CONSIDER** パフォーマンス上の違いの例外をスローします。 1秒あたり100を超えるレートをスローすると、ほとんどのアプリケーションのパフォーマンスが著しく低下する可能性があります。  
  
 **✓ DO** ドキュメントによって公開されている呼び出し可能なメンバー、メンバーの違反のためにスローされる例外すべてではなく、システム障害) コントラクトおよびコントラクトの一部として扱われるようにします。  
  
 コントラクトの一部である例外は、あるバージョンから次のバージョンに変更することはできません (つまり、例外の種類を変更することはできません。また、新しい例外は追加しないでください)。  
  
 **X DO NOT** かどうか throw をできるパブリック メンバーに基づいてにいくつかのオプションです。  
  
 **X DO NOT** パブリック メンバーの戻り値として例外を返すをまたは`out`パラメーター。  
  
 例外をスローするのではなくパブリック Api から例外を返すと、例外ベースのエラー報告の多くの利点が損なわれます。  
  
 **✓ CONSIDER** 例外ビルダー メソッドを使用します。  
  
 さまざまな場所から同じ例外をスローするのが一般的です。 コードの肥大化を回避するには、例外を作成してプロパティを初期化するヘルパーメソッドを使用します。  
  
 また、例外をスローするメンバーはインライン展開されません。 ビルダー内で throw ステートメントを移動すると、メンバーをインライン化できる可能性があります。  
  
 **X DO NOT** 例外フィルター ブロックから例外をスローします。  
  
 例外フィルターによって例外が発生した場合、CLR によって例外がキャッチされ、フィルターは false を返します。 この動作は、実行中のフィルターと区別できないため、明示的に false を返すため、デバッグが非常に困難です。  
  
 **X AVOID** 明示的に finally ブロックからの例外をスローします。 暗黙的にスローされた例外は、スローするメソッドの呼び出しによって返されます。  
  
 *©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*  
  
 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*  
  
## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
- [例外のデザインのガイドライン](../../../docs/standard/design-guidelines/exceptions.md)
