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
ms.openlocfilehash: 14ef02a760c9d4b77fe058334baffd63fcf29cfd
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709102"
---
# <a name="protected-members"></a>プロテクト メンバー
保護されたメンバー自体が拡張機能を提供することはありませんが、より強力なサブクラス化によって、拡張性を高めることができます。 これらを使用すると、メインのパブリックインターフェイスを不必要に複雑にすることなく、高度なカスタマイズオプションを公開できます。  
  
 フレームワークデザイナーは、保護されたメンバーに注意する必要があります。これは、"protected" という名前のセキュリティが誤った意味を持つ可能性があるためです。 だれでも、封印されていないクラスをサブクラス化し、保護されたメンバーにアクセスできるので、パブリックメンバーに使用される同じ防御的なコーディング方法がすべてプロテクトメンバーに適用されます。  
  
 **✓ CONSIDER** 高度なカスタマイズのメンバーを使用して保護されています。  
  
 **✓ DO** セキュリティ、ドキュメント、および互換性分析するためにパブリックと封印されていないクラスにプロテクト メンバーを処理します。  
  
 だれでもクラスを継承し、保護されたメンバーにアクセスできます。  
  
 *©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*  
  
 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*  
  
## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
- [機能拡張のデザイン](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
