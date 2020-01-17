---
title: イベントとコールバック
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- events [.NET Framework], extensibility
- methods [.NET Framework], callback
- callback methods
- callbacks
ms.assetid: 48b55c60-495f-4089-9396-97f9122bba7c
ms.openlocfilehash: 80c16e29f1d8a0653295ebc3cf25be6fb78b7dc9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709414"
---
# <a name="events-and-callbacks"></a>イベントとコールバック
コールバックは、フレームワークがデリゲートを通じてユーザーコードにコールバックすることを可能にする拡張ポイントです。 これらのデリゲートは、通常、メソッドのパラメーターを使用してフレームワークに渡されます。  
  
 イベントは、デリゲート (イベントハンドラー) を提供するための便利で一貫性のある構文をサポートする、特殊なコールバックのケースです。 さらに、Visual Studio のステートメント入力候補とデザイナーは、イベントベースの Api の使用に関するヘルプを提供します。 (「[イベントの設計](../../../docs/standard/design-guidelines/event.md)」を参照してください)。  
  
 **✓ CONSIDER** コールバックを使用して、フレームワークによって実行されるカスタム コードを提供できるようにします。  
  
 **✓ CONSIDER** イベントを使用したオブジェクト指向設計を理解することがなくてもフレームワークの動作をカスタマイズできるようにします。  
  
 **✓ DO** 幅広い開発者になじみのあるは、ステートメント入力候補の Visual Studio と統合されたために、イベントを単純なコールバックよりも優先されます。  
  
 **X AVOID** パフォーマンス重視の Api でのコールバックを使用します。  
  
 **✓ DO** 新しい`Func<...>`、 `Action<...>`、または`Expression<...>`コールバックで Api を定義するときに、カスタム デリゲートではなく型です。  
  
 `Func<...>` と `Action<...>` は汎用デリゲートを表します。 `Expression<...>` は、コンパイル後に実行時に呼び出すことができる関数定義を表しますが、シリアル化してリモートプロセスに渡すこともできます。  
  
 **✓ DO** を測定しを使用するパフォーマンスの影響について理解する`Expression<...>`、使用する代わりに`Func<...>`と`Action<...>`デリゲート。  
  
 `Expression<...>` 型は、ほとんどの場合、`Func<...>` と `Action<...>` デリゲートと論理的に等価です。 これらの主な違いは、デリゲートはローカルプロセスシナリオで使用することを意図していることです。式は、リモートのプロセスまたはコンピューターで式を評価することが有益であるケースを対象としています。  
  
 **✓ DO** するデリゲートを呼び出すことによって実行している任意のコードを理解し、セキュリティ、正確性、および互換性への影響を与える可能性です。  
  
 *©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*  
  
 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*  
  
## <a name="see-also"></a>関連項目

- [機能拡張のデザイン](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
