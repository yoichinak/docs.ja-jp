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
author: KrzysztofCwalina
ms.openlocfilehash: 1aeef9e1be6e5fe747f440a8cb7f21095cb22f49
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945497"
---
# <a name="names-of-assemblies-and-dlls"></a>アセンブリと DLL の名前
アセンブリは、展開およびマネージ コード アプリケーションの id の単位です。 アセンブリは、1 つまたは複数のファイルにまたがることができます、通常このアセンブリは DLL と 1 対 1 をマップします。 そのため、このセクションでは、のみ DLL の名前付け規則、アセンブリの名前付け規則にマップできますがについて説明します。  
  
 **✓ DO** アセンブリ System.Data などの機能の大きなチャンクを提案する Dll の名前を選択します。  
  
 アセンブリと DLL の名前が名前空間の名前に対応する必要はありませんが、アセンブリの名前を付けるときは、名前空間の名前を次に適切です。 適切な経験則では、アセンブリに含まれている名前空間の共通のプレフィックスに基づいた DLL の名前です。 たとえば、2 つの名前空間を持つアセンブリ`MyCompany.MyTechnology.FirstFeature`と`MyCompany.MyTechnology.SecondFeature`、呼び出すことができます`MyCompany.MyTechnology.dll`します。  
  
 **✓ CONSIDER** Dll を次のパターンに従って名前付け。  
  
 `<Company>.<Component>.dll`  
  
 場所`<Component>`ドットで区切られた 1 つ以上の句が含まれています。 例:  
  
 `Litware.Controls.dll`。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *Pearson Education, Inc. からのアクセス許可によって了承を得て転載[Framework デザイン ガイドライン。規則、手法、および再利用可能な .NET ライブラリの第 2 版のパターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina、Brad 内容では、Microsoft Windows の開発シリーズの一部として、Addison-wesley Professional、2008 年 10 月 22日を公開します。*  
  
## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
- [名前付けのガイドライン](../../../docs/standard/design-guidelines/naming-guidelines.md)
