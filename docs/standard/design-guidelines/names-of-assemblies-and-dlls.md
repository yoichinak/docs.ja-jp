---
title: アセンブリと DLL の名前
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], DLLs
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
- DLLs, names
ms.assetid: e800b610-31b4-4949-9c14-cb60e9f254be
ms.openlocfilehash: eebccba0b923b04333f289a85330d190c31013ab
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709258"
---
# <a name="names-of-assemblies-and-dlls"></a>アセンブリと DLL の名前
アセンブリは、マネージコードプログラムの配置と id の単位です。 アセンブリは1つ以上のファイルにまたがることができますが、通常、アセンブリは1対1のを DLL とマップします。 したがって、このセクションでは DLL の名前付け規則についてのみ説明し、次にアセンブリの名前付け規則にマップできます。  
  
 **✓ DO** アセンブリ System.Data などの機能の大きなチャンクを提案する Dll の名前を選択します。  
  
 アセンブリ名と DLL 名は、名前空間名に対応する必要はありませんが、アセンブリに名前を付けるときは、名前空間名に従うことをお勧めします。 経験則として、アセンブリに含まれる名前空間の共通のプレフィックスに基づいて DLL の名前を指定することをお勧めします。 たとえば、`MyCompany.MyTechnology.FirstFeature` と `MyCompany.MyTechnology.SecondFeature`の2つの名前空間を持つアセンブリを `MyCompany.MyTechnology.dll`と呼び出すことができます。  
  
 **✓ CONSIDER** Dll を次のパターンに従って名前付け。  
  
 `<Company>.<Component>.dll`  
  
 ここで、`<Component>` には1つ以上のドット区切り句が含まれています。 例:  
  
 `Litware.Controls.dll`.  
  
 *©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*  
  
 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*  
  
## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
- [名前付けのガイドライン](../../../docs/standard/design-guidelines/naming-guidelines.md)
