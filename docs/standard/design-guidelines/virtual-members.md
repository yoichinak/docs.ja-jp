---
title: 仮想メンバー
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- overridable members
- virtual members
- members [.NET Framework], virtual
ms.assetid: 8ff4eb97-0364-43ec-8a02-934b5cd94d19
author: KrzysztofCwalina
ms.openlocfilehash: 4943ddcdf1bc4e3e32c8d664cbcc5c50ae3959bd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778708"
---
# <a name="virtual-members"></a>仮想メンバー
そのため、サブクラスの動作を変更する仮想メンバーをオーバーライドできます。 それらは、それらのもたらす拡張性の観点からのコールバックとよく似ていますが、実行のパフォーマンスとメモリ消費量の観点からは優れています。 また、仮想メンバー自然に感じられる特殊な既存の型 (特殊化) の種類を作成する必要のあるシナリオでします。  
  
 仮想メンバーはコールバックとイベントをよりパフォーマンスが向上しますが、非仮想メソッドよりも優れた実行しません。  
  
 仮想メンバーの主な欠点は、仮想メンバーの動作はコンパイル時にのみ変更できます。 実行時に、コールバックの動作を変更できます。  
  
 コールバック (およびそれよりコールバックの他の情報) などの仮想メンバーを設計、テスト、および仮想メンバーへの呼び出しが予期しない方法でオーバーライドでき、任意のコードを実行できるので、管理コストがかかります。 また、さらに多くの労力は通常、設計と、それらを文書化のコストが高いため、仮想メンバーのコントラクトを明確に定義する必要です。  
  
 **X DO NOT** これを行うには相応の理由があり、デザイン、テスト、および仮想メンバーを保守に関連するすべてのコストを認識している限り、メンバーを仮想にすることです。  
  
 仮想メンバーは、互換性の問題なしに作成できる変更の観点からありました。 また、これらは、非仮想メンバーよりも低速仮想メンバーへの呼び出しがインラインでないため、ほとんどの場合です。  
  
 **✓ CONSIDER** に何がどうしても必要なだけの機能拡張を制限します。  
  
 **✓ DO** 仮想メンバーのアクセシビリティは public で保護されたアクセシビリティを優先します。 パブリック メンバーが拡張機能を提供 (必要な) 場合プロテクト仮想メンバーを呼び出すことによって。  
  
 クラスのパブリック メンバーは、そのクラスの直接のコンシューマー向けの機能の適切なセットを提供する必要があります。 仮想メンバーは、サブクラスで上書きするように設計し、保護されたアクセシビリティが使用する場所のすべての仮想機能拡張ポイントをスコープする優れた方法です。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *Pearson Education, Inc. からのアクセス許可によって了承を得て転載[Framework デザイン ガイドライン。規則、手法、および再利用可能な .NET ライブラリの第 2 版のパターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina、Brad 内容では、Microsoft Windows の開発シリーズの一部として、Addison-wesley Professional、2008 年 10 月 22日を公開します。*  
  
## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
- [機能拡張のデザイン](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
