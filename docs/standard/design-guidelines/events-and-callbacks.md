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
author: KrzysztofCwalina
ms.openlocfilehash: 3609d6ac4847cb081740fd698869df4976f83f8f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61960400"
---
# <a name="events-and-callbacks"></a>イベントとコールバック
コールバックは、機能拡張ポイントがデリゲートからのユーザー コードにコールバックするためのフレームワークです。 これらのデリゲートは、メソッドのパラメーターでは、通常、フレームワークに渡されます。  
  
 イベントは、コールバックのデリゲート (イベント ハンドラー) を提供するための便利で一貫した構文をサポートする特殊なケースです。 さらに、Visual Studio のステートメント入力候補およびデザイナーは、イベント ベースの Api を使用してヘルプを提供します。 (を参照してください[イベント デザイン](../../../docs/standard/design-guidelines/event.md))。  
  
 **✓ CONSIDER** コールバックを使用して、フレームワークによって実行されるカスタム コードを提供できるようにします。  
  
 **✓ CONSIDER** イベントを使用したオブジェクト指向設計を理解することがなくてもフレームワークの動作をカスタマイズできるようにします。  
  
 **✓ DO** 幅広い開発者になじみのあるは、ステートメント入力候補の Visual Studio と統合されたために、イベントを単純なコールバックよりも優先されます。  
  
 **X AVOID** パフォーマンス重視の Api でのコールバックを使用します。  
  
 **✓ DO** 新しい`Func<...>`、 `Action<...>`、または`Expression<...>`コールバックで Api を定義するときに、カスタム デリゲートではなく型です。  
  
 `Func<...>` `Action<...>`汎用デリゲートを表します。 `Expression<...>` コンパイルと、その後もできますが、実行時に呼び出されることができます関数定義を表すシリアル化およびリモート プロセスに渡されます。  
  
 **✓ DO** を測定しを使用するパフォーマンスの影響について理解する`Expression<...>`、使用する代わりに`Func<...>`と`Action<...>`デリゲート。  
  
 `Expression<...>` ほとんどの場合と論理的に等価では型が`Func<...>`と`Action<...>`デリゲート。 主な違いは、デリゲートはローカル プロセスのシナリオで使用するものであります。式は、有益なリモート プロセスまたはマシンで式を評価することである場合を対象としています。  
  
 **✓ DO** するデリゲートを呼び出すことによって実行している任意のコードを理解し、セキュリティ、正確性、および互換性への影響を与える可能性です。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *Pearson Education, Inc. からのアクセス許可によって了承を得て転載[Framework デザイン ガイドライン。規則、手法、および再利用可能な .NET ライブラリの第 2 版のパターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina、Brad 内容では、Microsoft Windows の開発シリーズの一部として、Addison-wesley Professional、2008 年 10 月 22日を公開します。*  
  
## <a name="see-also"></a>関連項目

- [機能拡張のデザイン](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
