---
title: インターフェイスのデザイン
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- interfaces [.NET Framework], design guidelines
- type design guidelines, interfaces
- class library design guidelines [.NET Framework], interfaces
ms.assetid: a016bd18-6710-4358-9438-9f190a295392
author: KrzysztofCwalina
ms.openlocfilehash: 1f982aa37f92b7270725574d949989ca120297d5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026368"
---
# <a name="interface-design"></a>インターフェイスのデザイン
ほとんどの Api は、クラスと構造体を使用して最適なモデル化、インターフェイスがより適切なまたは唯一のオプションの場合は。  
  
 CLR は多重継承をサポートしていません (つまり、CLR クラスから継承できません 1 つ以上の基底クラス) が、基本クラスから継承するだけでなく、1 つまたは複数のインターフェイスを実装する型。 そのため、インターフェイスは、多重継承の効果を実現するためによく使用されます。 たとえば、<xref:System.IDisposable>は参加する継承階層の独立した disposability をサポートする型を許可するインターフェイスです。  
  
 他のどの定義で、インターフェイスは、適切な状況がいくつかの値の型を含む複数の種類でサポートされる共通のインターフェイスを作成します。 値の型が以外の型から継承できません<xref:System.ValueType>、共通の基本型を提供するために、唯一のオプションは、インターフェイスを使用して、インターフェイスを実装できます。  
  
 **✓ DO** いくつかの一般的な API 値の型を含む型のセットでサポートする必要がある場合は、インターフェイスを定義します。  
  
 **✓ CONSIDER** 既に他の型を継承する型でその機能をサポートする必要がある場合は、インターフェイスを定義します。  
  
 **X AVOID** マーカー インターフェイス (メンバーを持たないインターフェイス) を使用します。  
  
 特定の特性 (マーカー) を持つものとしてマークする必要がある場合は、一般に、インターフェイスではなく、カスタム属性を使用します。  
  
 **✓ DO** インターフェイスの実装は、少なくとも 1 つの型を提供します。  
  
 インターフェイスのデザインを検証するには、この支援を行っています。 たとえば、<xref:System.Collections.Generic.List%601>の実装には、<xref:System.Collections.Generic.IList%601>インターフェイス。  
  
 **✓ DO** を定義する各インターフェイスを使用するには、少なくとも 1 つの API を提供 (パラメーターまたはプロパティとして、インターフェイス メソッドは、インターフェイスとして型指定された)。  
  
 インターフェイスのデザインを検証するには、この支援を行っています。 たとえば、<xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType>消費、<xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType>インターフェイス。  
  
 **X DO NOT** 以前に出荷されたインターフェイスにメンバーを追加します。  
  
 そうと、インターフェイスの実装ができなくなります。 バージョン管理の問題を回避するために、新しいインターフェイスを作成する必要があります。  
  
 除くこれらのガイドライン」に説明されている場合、マネージ コードの再利用可能なライブラリのデザインのインターフェイスではなく、クラスを選択してください、一般に。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *Pearson Education, Inc. からのアクセス許可によって了承を得て転載[Framework デザイン ガイドライン。規則、手法、および再利用可能な .NET ライブラリの第 2 版のパターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina、Brad 内容では、Microsoft Windows の開発シリーズの一部として、Addison-wesley Professional、2008 年 10 月 22日を公開します。*  
  
## <a name="see-also"></a>関連項目

- [型デザインのガイドライン](../../../docs/standard/design-guidelines/type.md)
- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
