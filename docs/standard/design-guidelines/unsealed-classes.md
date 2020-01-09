---
title: シールされていないクラス
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- classes [.NET Framework], unsealed
- unsealed classes
- inheritance, classes
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
ms.openlocfilehash: 8a5f1142674f83b5ef77f9f7e7e3518afd475e7d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709011"
---
# <a name="unsealed-classes"></a>シールされていないクラス
シールされたクラスはから継承できません。また、拡張を防ぎます。 これに対し、から継承できるクラスは、シールされていないクラスと呼ばれます。  
  
 **✓ CONSIDER** 安価なを提供するのにまだ高く評価されたフレームワークを拡張機能として、仮想またはプロテクト メンバーを追加なしで封印されていないクラスを使用します。  
  
 開発者は、カスタムコンストラクター、新しいメソッド、メソッドオーバーロードなどの便利なメンバーを追加するために、シールされていないクラスから継承することがよくあります。 たとえば、`System.Messaging.MessageQueue` が封印されていないため、ユーザーは特定のキューのパスを既定とするカスタムキューを作成したり、特定のシナリオで API を簡略化するカスタムメソッドを追加したりできます。  
  
 ほとんどのプログラミング言語では、クラスは既定で封印されていません。これは、フレームワークのほとんどのクラスで既定でも推奨されます。 封印されていない型によって実現される機能拡張は、フレームワークユーザーにとって非常に歓迎されており、封印されていない型に関連するテストコストが比較的低いため、非常に安価です  
  
 *©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*  
  
 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*  
  
## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
- [機能拡張のデザイン](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [シール](../../../docs/standard/design-guidelines/sealing.md)
