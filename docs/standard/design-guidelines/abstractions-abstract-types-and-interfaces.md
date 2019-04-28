---
title: 抽象化 (抽象型およびインターフェイス)
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- interfaces [.NET Framework], abstract
- abstract interfaces [.NET Framework]
- abstract types [.NET Framework]
- types [.NET Framework], abstract
ms.assetid: 0a632bc7-9b03-44ee-8842-c82f88672a45
author: KrzysztofCwalina
ms.openlocfilehash: fcf566c24677630fdbb1fcd0eb7628f830b3be2b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789221"
---
# <a name="abstractions-abstract-types-and-interfaces"></a>抽象化 (抽象型およびインターフェイス)
抽象化は、コントラクトを記述するコントラクトの完全な実装を提供しない型です。 抽象化は通常インターフェイスまたは抽象クラスとして実装し、適切に定義された一連のコントラクトを実装する型の必要なセマンティクスを説明するリファレンス ドキュメントが付属します。 .NET Framework で最も重要な抽象化のものが<xref:System.IO.Stream>、 <xref:System.Collections.Generic.IEnumerable%601>、および<xref:System.Object>します。  
  
 抽象化のコントラクトをサポートする具象型を実装して、フレームワーク Api がかかる (操作) でこの具象型を使用してフレームワークを拡張することができます、抽象化します。  
  
 時の試練に耐え得ることが有意義で便利な抽象化は、設計することは困難です。 メインの難しさがなくなると不要な少なく、メンバーの適切なセットを取得しています。 抽象化のメンバーが多すぎる場合は、難しいかを実装することが不可能になります。 約束の機能が少なすぎますメンバー場合は、多くの興味深いシナリオで役に立たないになります。  
  
 フレームワークで多くの抽象化には、フレームワークの使いやすさも悪影響に影響します。 多くの場合、具体的な実装と抽象化で動作している Api の大きい画像に組み込む方法を理解せず、抽象化を理解することが難しくなります。 また、抽象化とそのメンバーの名前は必ずしも抽象頻繁なものになりますわかりにくいと印象は最初の使用量のより広範なコンテキストを理解することがなく。  
  
 ただし、抽象化は、その他の拡張メカニズムは、できない多くの場合と一致する非常に強力な機能拡張を提供します。 多くのアーキテクチャ パターン、プラグインなどの中核には制御の反転 (IoC)、パイプライン、やなど。 フレームワークのテストの容易性の非常に重要なもいます。 適切な抽象化を使用すれば、単体テストするために大量の依存関係を消去できます。 要約すると、抽象化は、最新のオブジェクト指向フレームワークのいる豊富な機能を担当します。  
  
 **X DO NOT** いくつかの具体的な実装と、抽象化を使用する Api を開発してテストする場合を除き、抽象化を提供します。  
  
 **✓ DO** 抽象化を設計するときは、抽象クラスとインターフェイス間慎重に選択します。  
  
 **✓ CONSIDER** 抽象クラスの具象実装のテストの参照を提供します。 このようなテストは、その実装が正しく、コントラクトを実装するかどうかをテストするユーザーを許可する必要があります。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *Pearson Education, Inc. からのアクセス許可によって了承を得て転載[Framework デザイン ガイドライン。規則、手法、および再利用可能な .NET ライブラリの第 2 版のパターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina、Brad 内容では、Microsoft Windows の開発シリーズの一部として、Addison-wesley Professional、2008 年 10 月 22日を公開します。*  
  
## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
- [機能拡張のデザイン](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
