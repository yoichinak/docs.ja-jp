---
title: フィールドのデザイン
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- fields, design guidelines
- read-only fields
- member design guidelines, fields
ms.assetid: 7cb4b0f3-7a10-4c93-b84d-733f7134fcf8
author: KrzysztofCwalina
ms.openlocfilehash: 3ab8fe279605c4795bb3a26557d0241b186b273a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026407"
---
# <a name="field-design"></a>フィールドのデザイン
カプセル化の原理は、最も重要な概念の 1 つをオブジェクト指向設計にです。 この原則は、データ オブジェクト内に格納されますが、そのオブジェクトのみがアクセスできるがあることを示しています。  
  
 原則を解釈する便利な方法は、型のメンバー以外のコードを損なうことがなくその型 (名前または種類の変更) のフィールドに変更ができるように、型を設計する必要がありますには。 この解釈は、すぐに、すべてのフィールドがプライベートでなければならないことを意味します。  
  
 定数と静的な読み取り専用フィールドは、このようなフィールドの定義によってほぼ必要はまったくありませんを変更するために、この厳密な制限から除外します。  
  
 **X DO NOT** パブリックまたは保護されたインスタンス フィールドを提供します。  
  
 Public または protected にする代わりにフィールドへのアクセスのプロパティを提供する必要があります。  
  
 **✓ DO** は決して変化しない定数の定数フィールドを使用します。  
  
 コンパイラは、const フィールドの値を直接コードを呼び出すに焼き付けます。 そのため、const 値は、決して互換性の問題のリスクを負うことがなく変更できます。  
  
 **✓ DO** のパブリック静的を使用して`readonly`フィールドの定義済みのオブジェクト インスタンス。  
  
 型の定義済みのインスタンスがある場合により読み取り専用で、型自体の静的フィールドをパブリックとしてと宣言します。  
  
 **X DO NOT** への変更可能な型のインスタンスを割り当てる`readonly`フィールドです。  
  
 変更可能な型は、インスタンス化した後で変更することができますのインスタンスの型です。 たとえば、配列、ほとんどのコレクション、およびストリームは変更可能な型が<xref:System.Int32?displayProperty=nameWithType>、 <xref:System.Uri?displayProperty=nameWithType>、および<xref:System.String?displayProperty=nameWithType>はすべて不変です。 参照型のフィールドに対する読み取り専用修飾子には、置き換えられるのフィールドに格納されているインスタンスができなくなりますが、フィールドのインスタンスのデータのインスタンスを変更するメンバーを呼び出すことによって変更を妨げることはできません。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *Pearson Education, Inc. からのアクセス許可によって了承を得て転載[Framework デザイン ガイドライン。規則、手法、および再利用可能な .NET ライブラリの第 2 版のパターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina、Brad 内容では、Microsoft Windows の開発シリーズの一部として、Addison-wesley Professional、2008 年 10 月 22日を公開します。*  
  
## <a name="see-also"></a>関連項目

- [メンバーのデザインのガイドライン](../../../docs/standard/design-guidelines/member.md)
- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
