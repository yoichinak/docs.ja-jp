---
title: 配列
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
ms.openlocfilehash: ac4b073d2d3291922498a0e56c7e81f7e7868c65
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709570"
---
# <a name="arrays"></a>配列
**✓ DO** パブリック Api で配列にコレクションの使用を優先します。 コレクション[セクションで](../../../docs/standard/design-guidelines/guidelines-for-collections.md)は、コレクションと配列のどちらかを選択する方法について詳しく説明します。  
  
 **X DO NOT** 読み取り専用配列フィールドを使用します。 フィールド自体は読み取り専用であり、変更することはできませんが、配列内の要素は変更できます。  
  
 **✓ CONSIDER** 多次元配列ではなくジャグ配列を使用します。  
  
 ジャグ配列は、配列でもある要素を含む配列です。 要素を構成する配列は、さまざまなサイズになることがあり、一部のデータセット (スパースマトリックスなど) では、多次元配列と比較して無駄になる領域が少なくなります。 さらに、CLR はジャグ配列に対するインデックス操作を最適化するため、一部のシナリオでは実行時のパフォーマンスが向上する可能性があります。  
  
 *©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*  
  
 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*  
  
## <a name="see-also"></a>関連項目

- <xref:System.Array>
- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
- [使用方法のガイドライン](../../../docs/standard/design-guidelines/usage-guidelines.md)
