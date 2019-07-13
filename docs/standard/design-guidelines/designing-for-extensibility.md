---
title: 機能拡張のデザイン
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- extending class libraries
- extensibility with class libraries in .NET Framework
- class library design guidelines [.NET Framework], extensibility
- class library extensibility [.NET Framework]
ms.assetid: 1cdb8740-871a-456c-9bd9-db96ca8d79b3
author: KrzysztofCwalina
ms.openlocfilehash: 94900dee72230a1b9d099d78168acc508af62af7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026459"
---
# <a name="designing-for-extensibility"></a>機能拡張のデザイン
フレームワークの設計の 1 つの重要な側面は、フレームワークの拡張性を慎重に検討することを確認して行っています。 これは、コストとメリットに関連付けられたさまざまな機能拡張メカニズムを理解することが必要です。 この章では、拡張メカニズムを判断するのに役立ちます: サブクラス化、イベント、仮想メンバー、コールバック、および、-、framework の要件を満たす最適なことができます。  
  
 フレームワークで機能拡張を可能にする方法はたくさんあります。 コストが非常に強力なするよりも低コストの範囲です。 任意の特定の機能拡張要件の要件を満たす最低コストのかかる機能拡張メカニズムを選択してください。 重大な変更を導入することがなくすぐ実行しないことができますが、通常は、後で、複数の機能拡張を追加することは覚えておいてください。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [シールされていないクラス](../../../docs/standard/design-guidelines/unsealed-classes.md)  
 [プロテクト メンバー](../../../docs/standard/design-guidelines/protected-members.md)  
 [イベントとコールバック](../../../docs/standard/design-guidelines/events-and-callbacks.md)  
 [仮想メンバー](../../../docs/standard/design-guidelines/virtual-members.md)  
 [抽象化 (抽象型およびインターフェイス)](../../../docs/standard/design-guidelines/abstractions-abstract-types-and-interfaces.md)  
 [抽象化の実装用の基本クラス](../../../docs/standard/design-guidelines/base-classes-for-implementing-abstractions.md)  
 [シール](../../../docs/standard/design-guidelines/sealing.md)  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *Pearson Education, Inc. からのアクセス許可によって了承を得て転載[Framework デザイン ガイドライン。規則、手法、および再利用可能な .NET ライブラリの第 2 版のパターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina、Brad 内容では、Microsoft Windows の開発シリーズの一部として、Addison-wesley Professional、2008 年 10 月 22日を公開します。*  
  
## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
