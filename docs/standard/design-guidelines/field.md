---
title: "フィールドのデザイン"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- fields, design guidelines
- read-only fields
- member design guidelines, fields
ms.assetid: 7cb4b0f3-7a10-4c93-b84d-733f7134fcf8
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ccced2c9e816122d770f43056c36ab4a6d510fde
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="field-design"></a>フィールドのデザイン
カプセル化の原則が、最も重要な概念のいずれかのオブジェクト指向デザインします。 この原則は、オブジェクト内に格納されているデータはそのオブジェクトにのみアクセスできることを示します。  
  
 原則を解釈する便利な方法は、言い換えれば、その型 (名前やタイプの変更) のフィールドへの変更が、型のメンバーを以外のコードを変更せずにできるように、型を設計することができます。 この解釈は、すぐに、すべてのフィールドをプライベートでなければならないことを意味します。  
  
 この厳密な制限から定数と静的な読み取り専用のフィールドは必要であるため、このようなフィールドほぼ定義では、決してを変更するお除外します。  
  
 **X しないで**パブリックまたは保護されたインスタンス フィールドを提供します。  
  
 Public または protected ようにではなくフィールドにアクセスするため、プロパティを提供する必要があります。  
  
 **✓ しないで**は決して変化しない定数の定数フィールドを使用します。  
  
 コンパイラは、コードの呼び出しに直接 const フィールドの値を書き込みますがします。 そのため、const の値は変更不可能互換性の問題の危険を回避します。  
  
 **✓ しないで**のパブリック静的を使用して`readonly`フィールドの定義済みのオブジェクト インスタンス。  
  
 型の定義済みのインスタンスが場合、により読み取り専用で、型自体の静的フィールドをパブリックとしてと宣言します。  
  
 **X しないで**への変更可能な型のインスタンスを割り当てる`readonly`フィールドです。  
  
 変更可能な型は、インスタンスは作成後に変更することができますのインスタンスを持つ型です。 たとえば、配列、ほとんどのコレクション、およびストリームは変更可能な型が<xref:System.Int32?displayProperty=nameWithType>、 <xref:System.Uri?displayProperty=nameWithType>、および<xref:System.String?displayProperty=nameWithType>はすべて変更できません。 参照型のフィールドで読み取り専用の修飾子には、置き換えられるのフィールドに格納されているインスタンスができなくなりますが、フィールドのインスタンス データのインスタンスを変更するメンバーを呼び出すことによって変更されているを妨げることはできません。  
  
 *部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*  
  
 *ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*  
  
## <a name="see-also"></a>参照  
 [メンバーのデザインのガイドライン](../../../docs/standard/design-guidelines/member.md)  
 [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
