---
title: 等値演算子
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], Equals method
- class library design guidelines [.NET Framework], equality operator
- equality operator (==) [.NET Framework]
- Equals method
- == operator (equality) [.NET Framework]
ms.assetid: bc496a91-fefb-4ce0-ab4c-61f09964119a
author: KrzysztofCwalina
ms.openlocfilehash: ef1a0aff1ac59434d9d9a6f0371bf236f637050e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61960333"
---
# <a name="equality-operators"></a>等値演算子
このセクションでは、等値演算子のオーバー ロードをについて説明しを指す`operator==`と`operator!=`として等値演算子。  
  
 **X DO NOT** 等値演算子および以外のいずれかのオーバー ロードします。  
  
 **✓ DO** いることを確認<xref:System.Object.Equals%2A?displayProperty=nameWithType>等値演算子は、同じセマンティクスと同様のパフォーマンス特性があるとします。  
  
 多くの場合、つまり`Object.Equals`等値演算子はオーバー ロード時にオーバーライドする必要があります。  
  
 **X AVOID** 等値演算子から例外をスローします。  
  
 たとえば、引数のいずれかがスローする代わりに null の場合は false を返す`NullReferenceException`します。  
  
## <a name="equality-operators-on-value-types"></a>値の型で等値演算子  
 **✓ DO** 等しいかどうかがわかりやすい場合は、値型で等値演算子をオーバー ロードします。  
  
 ほとんどのプログラミング言語での既定の実装がない`operator==`値の型。  
  
## <a name="equality-operators-on-reference-types"></a>参照型で等値演算子  
 **X AVOID** 変更可能な参照型で等値演算子のオーバー ロードします。  
  
 多くの言語では、参照型の組み込みの等値演算子があります。 組み込みの演算子は、通常は参照の等価性を実装し、値の等価性を既定の動作が変更されたときに、多くの開発者は驚かします。  
  
 この問題は、不変性をより参照の等価性と値の等価性の間の違いに注意をはるかに困難になるために、変更不可の参照型の軽減されます。  
  
 **X AVOID** 実装では、参照の等価性の場合よりもはるかに低速になる場合は、参照型で等値演算子をオーバー ロードします。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *Pearson Education, Inc. からのアクセス許可によって了承を得て転載[Framework デザイン ガイドライン。規則、手法、および再利用可能な .NET ライブラリの第 2 版のパターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina、Brad 内容では、Microsoft Windows の開発シリーズの一部として、Addison-wesley Professional、2008 年 10 月 22日を公開します。*  
  
## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
- [使用方法のガイドライン](../../../docs/standard/design-guidelines/usage-guidelines.md)
