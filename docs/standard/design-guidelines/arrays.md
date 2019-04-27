---
title: 配列
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
author: KrzysztofCwalina
ms.openlocfilehash: dd30cdee0440553a9f955f0b3f4ee420e938b9ea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61864118"
---
# <a name="arrays"></a>配列
**✓ DO** パブリック Api で配列にコレクションの使用を優先します。 [コレクション](../../../docs/standard/design-guidelines/guidelines-for-collections.md)セクション コレクションと配列の間で選択する方法について詳しく説明します。  
  
 **X DO NOT** 読み取り専用配列フィールドを使用します。 フィールド自体は読み取り専用と、変更できない配列内の要素を変更することができます。  
  
 **✓ CONSIDER** 多次元配列ではなくジャグ配列を使用します。  
  
 ジャグ配列は、要素も配列を含む配列です。 配列の要素を構成するには、多次元配列と比較データ (スパース マトリックスなど) のいくつかのセットに対して無駄な小さい領域に、さまざまなサイズを指定できます。 さらに、いくつかのシナリオで実行時パフォーマンスの向上を発生する可能性がありますので、CLR は、ジャグ配列のインデックス操作を最適化します。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *Pearson Education, Inc. からのアクセス許可によって了承を得て転載[Framework デザイン ガイドライン。規則、手法、および再利用可能な .NET ライブラリの第 2 版のパターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina、Brad 内容では、Microsoft Windows の開発シリーズの一部として、Addison-wesley Professional、2008 年 10 月 22日を公開します。*  
  
## <a name="see-also"></a>関連項目

- <xref:System.Array>
- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
- [使用方法のガイドライン](../../../docs/standard/design-guidelines/usage-guidelines.md)
