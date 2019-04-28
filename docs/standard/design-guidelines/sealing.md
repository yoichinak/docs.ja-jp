---
title: シール
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- limiting extensibility
- classes [.NET Framework], sealing
- preventing customization
- sealed classes
ms.assetid: cc42267f-bb7a-427a-845e-df97408528d4
author: KrzysztofCwalina
ms.openlocfilehash: c8aeb5ce3d93755f30bf68732592a08d7af54957
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61762063"
---
# <a name="sealing"></a>シール
オブジェクト指向フレームワークの機能の 1 つは、開発者が拡張およびフレームワークの設計者によって予期しない方法でそれらをカスタマイズできます。 これは、両方の電源および拡張可能なデザインの危険性。 フレームワークを設計するときは、そのため、慎重に拡張機能の設計が必要なときに危険な場合は、機能拡張を制限して、非常に重要です。  
  
 機能拡張を防ぐ強力なメカニズムをシールします。 クラスまたは個々 のメンバーをシールすることができます。 クラスをシールすると、ユーザーがクラスから継承することはできません。 メンバーをシールすると、ユーザーが特定のメンバーをオーバーライドできなくなります。  
  
 **X DO NOT** これを行うには相応の理由をしなくてもクラスをシールします。  
  
 機能拡張シナリオを考えることはできませんので、クラスをシールすることは正当な理由ではありません。 フレームワークのユーザーの利便性のためのメンバーの追加など、さまざまな明確な理由のクラスから継承したいです。 参照してください[封印されていないクラス](../../../docs/standard/design-guidelines/unsealed-classes.md)明確な理由の例については、ユーザーが型から継承するようにします。  
  
 クラスをシールする理由を以下に示します。  
  
- クラスは、静的クラスです。 参照してください[静的クラスのデザイン](../../../docs/standard/design-guidelines/static-class.md)します。  
  
- クラスは、継承されたプロテクト メンバーのセキュリティに重要なシークレットを格納します。  
  
- クラスは、多くの仮想メンバーを継承し、それらを個別にシールのコストは封印されていないクラスを離れることのメリットを上回ります。 します。  
  
- クラスは、非常に高速なランタイム参照が必要な属性です。 Sealed 属性では、封印されていないものよりもわずかに高いパフォーマンス レベルがあります。 参照してください[属性](../../../docs/standard/design-guidelines/attributes.md)します。  
  
 **X DO NOT** sealed 型でプロテクト メンバーまたは仮想メンバーを宣言します。  
  
 定義上、sealed 型から継承できません。 つまり、sealed 型でプロテクト メンバーを呼び出すことはできません、および、sealed 型での仮想メソッドをオーバーライドすることはできません。  
  
 **✓ CONSIDER** をオーバーライドするメンバーをシールします。  
  
 仮想メンバーの概要に起因する問題 (で説明した[仮想メンバー](../../../docs/standard/design-guidelines/virtual-members.md)) やや劣る度にも同様に、上書きを適用します。 オーバーライドをシール、継承階層の時点からこれらの問題から保護します。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *Pearson Education, Inc. からのアクセス許可によって了承を得て転載[Framework デザイン ガイドライン。規則、手法、および再利用可能な .NET ライブラリの第 2 版のパターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina、Brad 内容では、Microsoft Windows の開発シリーズの一部として、Addison-wesley Professional、2008 年 10 月 22日を公開します。*  
  
## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
- [機能拡張のデザイン](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [シールされていないクラス](../../../docs/standard/design-guidelines/unsealed-classes.md)
