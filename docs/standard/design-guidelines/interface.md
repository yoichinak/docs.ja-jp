---
title: インターフェイスのデザイン
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- interfaces [.NET Framework], design guidelines
- type design guidelines, interfaces
- class library design guidelines [.NET Framework], interfaces
ms.assetid: a016bd18-6710-4358-9438-9f190a295392
ms.openlocfilehash: 06b2e0d281314f3bd6346a7dbbd8bb56928fe58b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709297"
---
# <a name="interface-design"></a>インターフェイスのデザイン
ほとんどの Api はクラスと構造体を使用してモデル化されていますが、インターフェイスがより適している場合や、唯一のオプションである場合もあります。  
  
 CLR は複数の継承をサポートしていません (つまり、CLR クラスは複数の基底クラスから継承することはできません) が、基底クラスから継承するだけでなく、1つまたは複数のインターフェイスを実装することもできます。 したがって、多くの場合、インターフェイスは、多重継承の効果を実現するために使用されます。 たとえば、<xref:System.IDisposable> は、参加する他の継承階層に依存しない disposability を型がサポートできるようにするインターフェイスです。  
  
 インターフェイスを定義する他の状況としては、いくつかの値型を含む、複数の型でサポートできる共通インターフェイスを作成することがあります。 値型は、<xref:System.ValueType>以外の型から継承することはできませんが、インターフェイスを実装することはできます。そのため、共通の基本型を指定するための唯一のオプションはインターフェイスを使用することです。  
  
 **✓ DO** いくつかの一般的な API 値の型を含む型のセットでサポートする必要がある場合は、インターフェイスを定義します。  
  
 **✓ CONSIDER** 既に他の型を継承する型でその機能をサポートする必要がある場合は、インターフェイスを定義します。  
  
 **X AVOID** マーカー インターフェイス (メンバーを持たないインターフェイス) を使用します。  
  
 クラスを特定の特性 (マーカー) としてマークする必要がある場合は、一般に、インターフェイスではなくカスタム属性を使用します。  
  
 **✓ DO** インターフェイスの実装は、少なくとも 1 つの型を提供します。  
  
 これにより、インターフェイスの設計を検証できます。 たとえば、<xref:System.Collections.Generic.List%601> は <xref:System.Collections.Generic.IList%601> インターフェイスの実装です。  
  
 **✓ DO** を定義する各インターフェイスを使用するには、少なくとも 1 つの API を提供 (パラメーターまたはプロパティとして、インターフェイス メソッドは、インターフェイスとして型指定された)。  
  
 これにより、インターフェイスの設計を検証できます。 たとえば、<xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> は <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> インターフェイスを使用します。  
  
 **X DO NOT** 以前に出荷されたインターフェイスにメンバーを追加します。  
  
 これにより、インターフェイスの実装が中断されます。 バージョン管理の問題を回避するために、新しいインターフェイスを作成する必要があります。  
  
 これらのガイドラインで説明されている状況を除き、一般に、マネージコードの再利用可能なライブラリの設計では、インターフェイスではなくクラスを選択する必要があります。  
  
 *©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*  
  
 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*  
  
## <a name="see-also"></a>関連項目

- [型デザインのガイドライン](../../../docs/standard/design-guidelines/type.md)
- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
