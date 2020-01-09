---
title: リソースに名前を付ける
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], localized resources
- localization, naming guidelines
- resource names
- global applications, naming guidelines
- international applications, naming guidelines
ms.assetid: 8b0e97f3-7877-44fd-bc76-e05d36d5d79c
ms.openlocfilehash: b64a3ef6e12f8ea1abf7efd9c22f2f4333dda5c8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709167"
---
# <a name="naming-resources"></a>リソースに名前を付ける
ローカライズ可能なリソースは、プロパティのように特定のオブジェクトを介して参照できるので、リソースの名前付けガイドラインはプロパティガイドラインに似ています。  
  
 **✓ DO** リソース キーで pascal 表記を使用を使用します。  
  
 **✓ DO** 短い識別子ではなくわかりやすいを提供します。  
  
 **X DO NOT** メインの CLR 言語の言語固有のキーワードを使用します。  
  
 **✓ DO** のみ英数字とアンダー スコアを使用してリソースの名前付けで使用します。  
  
 **✓ DO** 例外メッセージのリソースに対して次の命名規則を使用します。  
  
 リソース識別子は、例外の種類の名前に例外の短い識別子を加えたものにする必要があります。  
  
 `ArgumentExceptionIllegalCharacters`  
 `ArgumentExceptionInvalidName`  
 `ArgumentExceptionFileNameIsMalformed`  
  
 *©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*  
  
 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*  
  
## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
- [名前付けのガイドライン](../../../docs/standard/design-guidelines/naming-guidelines.md)
