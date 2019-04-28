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
author: KrzysztofCwalina
ms.openlocfilehash: 44627aafd9ec779625413a0862412a8f6c408109
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756885"
---
# <a name="naming-resources"></a>リソースに名前を付ける
場合のプロパティと同様、特定のオブジェクトを使用してローカライズ可能なリソースを参照できる、ので、リソースの名前付けのガイドラインは、プロパティのガイドラインに似ています。  
  
 **✓ DO** リソース キーで pascal 表記を使用を使用します。  
  
 **✓ DO** 短い識別子ではなくわかりやすいを提供します。  
  
 **X DO NOT** メインの CLR 言語の言語固有のキーワードを使用します。  
  
 **✓ DO** のみ英数字とアンダー スコアを使用してリソースの名前付けで使用します。  
  
 **✓ DO** 例外メッセージのリソースに対して次の命名規則を使用します。  
  
 リソース識別子は、例外の種類名と例外の短い識別子にする必要があります。  
  
 `ArgumentExceptionIllegalCharacters`  
 `ArgumentExceptionInvalidName`  
 `ArgumentExceptionFileNameIsMalformed`  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *Pearson Education, Inc. からのアクセス許可によって了承を得て転載[Framework デザイン ガイドライン。規則、手法、および再利用可能な .NET ライブラリの第 2 版のパターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina、Brad 内容では、Microsoft Windows の開発シリーズの一部として、Addison-wesley Professional、2008 年 10 月 22日を公開します。*  
  
## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
- [名前付けのガイドライン](../../../docs/standard/design-guidelines/naming-guidelines.md)
