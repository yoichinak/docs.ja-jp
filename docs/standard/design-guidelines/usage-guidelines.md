---
title: 使用ガイドライン
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], usage guidelines
ms.assetid: 42215ffa-a099-4a26-b14e-fb2bdb6f95b7
author: KrzysztofCwalina
ms.openlocfilehash: 761570b899a2a36391eb81dc7f42e13fff1f14ef
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778808"
---
# <a name="usage-guidelines"></a>使用ガイドライン

このセクションには、パブリックにアクセスできる Api で一般的な種類の使用に関するガイドラインが含まれています。 組み込みフレームワーク型 (シリアル化属性など) および一般的な演算子のオーバー ロードの直接の使用状況を処理します。
  
<xref:System.IDisposable?displayProperty=nameWithType>インターフェイスは、このセクションでは説明しませんが、については、 [Dispose パターン](../../../docs/standard/design-guidelines/dispose-pattern.md)セクション。

> [!NOTE]
> 組み込みの .NET Framework 型のガイドラインとその他の共通の詳細についてには、次の参照トピックを参照してください: <xref:System.DateTime?displayProperty=nameWithType>、 <xref:System.DateTimeOffset?displayProperty=nameWithType>、 <xref:System.ICloneable?displayProperty=nameWithType>、 <xref:System.IComparable%601?displayProperty=nameWithType>、 <xref:System.IEquatable%601?displayProperty=nameWithType>、 <xref:System.Nullable%601?displayProperty=nameWithType>、 <xref:System.Object?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>.

## <a name="in-this-section"></a>このセクションの内容

[配列](arrays.md)  
[属性](attributes.md)  
[コレクション](guidelines-for-collections.md)  
[シリアル化](serialization.md)  
[System.Xml の使用法](system-xml-usage.md)  
[等値演算子](equality-operators.md)  

*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*

*Pearson Education, Inc. からのアクセス許可によって了承を得て転載[Framework デザイン ガイドライン。規則、手法、および再利用可能な .NET ライブラリの第 2 版のパターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina、Brad 内容では、Microsoft Windows の開発シリーズの一部として、Addison-wesley Professional、2008 年 10 月 22日を公開します。*
  
## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
