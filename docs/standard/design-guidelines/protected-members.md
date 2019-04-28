---
title: プロテクト メンバー
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- members [.NET Framework], protected
- protected members
- classes [.NET Framework], unsealed
- classes [.NET Framework], protected members
- unsealed classes
- customizing class behavior
ms.assetid: aa0b58ee-3956-494d-ab48-471ae5db8740
author: KrzysztofCwalina
ms.openlocfilehash: 7d940f10799df2efc6c6d031781e1ef7cf777dd6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937398"
---
# <a name="protected-members"></a>プロテクト メンバー
単独で保護されたメンバーでは任意の拡張機能は提供しませんより強力なサブクラス化による拡張性を作成することができます。 これらは、メインのパブリック インターフェイスを不必要に複雑にせず、高度なカスタマイズ オプションを公開する使用できます。  
  
 フレームワークの設計者は、「保護」の名前は、セキュリティの誤った認識を与えることができますので、保護されたメンバーには注意する必要があります。 すべてのユーザーは、封印されていないクラスのサブクラスとメンバーへのアクセスが保護されていることと、防御的なコーディング手法がパブリック メンバーの使用が保護されたメンバーに適用するため、同じ。  
  
 **✓ CONSIDER** 高度なカスタマイズのメンバーを使用して保護されています。  
  
 **✓ DO** セキュリティ、ドキュメント、および互換性分析するためにパブリックと封印されていないクラスにプロテクト メンバーを処理します。  
  
 クラスから継承するすべてのユーザーし、プロテクト メンバーにアクセスできます。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *Pearson Education, Inc. からのアクセス許可によって了承を得て転載[Framework デザイン ガイドライン。規則、手法、および再利用可能な .NET ライブラリの第 2 版のパターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina、Brad 内容では、Microsoft Windows の開発シリーズの一部として、Addison-wesley Professional、2008 年 10 月 22日を公開します。*  
  
## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
- [機能拡張のデザイン](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
