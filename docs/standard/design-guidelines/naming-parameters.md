---
title: パラメーターに名前を付ける
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
ms.openlocfilehash: 0bb67056bb39b6a5f372191a1d0b0bb0dc1fe4d1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709180"
---
# <a name="naming-parameters"></a>パラメーターに名前を付ける
読みやすくするために、パラメーター名のガイドラインに従うことが重要です。これは、ビジュアルデザインツールが Intellisense とクラス参照機能を提供する場合に、ドキュメントとデザイナーにパラメーターが表示されるためです。  
  
 **✓ DO** パラメーター名の camel 表記を使用します。  
  
 **✓ DO** わかりやすいパラメーター名を使用します。  
  
 **✓ CONSIDER** パラメーターの型ではなく、パラメーターの意味に基づく名前を使用します。  
  
### <a name="naming-operator-overload-parameters"></a>演算子のオーバーロードパラメーターの名前付け  
 **✓ DO** 使用`left`と`right`のパラメーターに意味がない場合は、二項演算子のオーバー ロード パラメーター名にします。  
  
 **✓ DO** 使用`value`で単項演算子のオーバー ロード パラメーター名はパラメーターに意味がない場合。  
  
 **✓ CONSIDER** 演算子にわかりやすい名前オーバー ロードのパラメーターの場合は重要な価値が追加されます。  
  
 **X DO NOT** 使用の省略形または数値の添字演算子のオーバー ロードのパラメーターの名前。  
  
 *©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*  
  
 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*  
  
## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
- [名前付けのガイドライン](../../../docs/standard/design-guidelines/naming-guidelines.md)
