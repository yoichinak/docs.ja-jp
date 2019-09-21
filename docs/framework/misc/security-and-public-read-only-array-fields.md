---
title: セキュリティとパブリックの読み取り専用配列フィールド
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], public read-only array fields
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3d36009fa4fc7b9299708768fe34a75f1fde6797
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910738"
---
# <a name="security-and-public-read-only-array-fields"></a>セキュリティとパブリックの読み取り専用配列フィールド
読み取り専用のパブリック配列フィールドを変更できるため、マネージライブラリから読み取り専用パブリック配列フィールドを使用して、アプリケーションの境界動作またはセキュリティを定義しないでください。  
  
## <a name="remarks"></a>Remarks  
 一部の .NET framework クラスには、プラットフォーム固有の境界パラメーターを含む読み取り専用のパブリックフィールドが含まれています。  たとえば<xref:System.IO.Path.InvalidPathChars> 、フィールドは、ファイルパス文字列で許可されていない文字を記述する配列です。  .NET Framework 全体に同様の多くのフィールドが存在します。  
  
 のような<xref:System.IO.Path.InvalidPathChars>パブリック読み取り専用フィールドの値は、コードまたはコードのアプリケーションドメインを共有するコードによって変更できます。  アプリケーションの境界動作を定義するには、このような読み取り専用パブリック配列フィールドを使用しないでください。  そうすると、悪意のあるコードが境界の定義を変更し、予期しない方法でコードを使用できるようになります。  
  
 .NET Framework のバージョン2.0 以降では、パブリック配列フィールドを使用する代わりに、新しい配列を返すメソッドを使用する必要があります。  たとえば、 <xref:System.IO.Path.InvalidPathChars>フィールドを使用する代わりに、 <xref:System.IO.Path.GetInvalidPathChars%2A>メソッドを使用する必要があります。  
  
 .NET Framework 型では、内部的に境界の種類を定義するためにパブリックフィールドが使用されないことに注意してください。  代わりに、.NET Framework は個別のプライベートフィールドを使用します。  これらのパブリックフィールドの値を変更しても、.NET Framework 型の動作は変更されません。  
  
## <a name="see-also"></a>関連項目

- [安全なコーディングのガイドライン](../../standard/security/secure-coding-guidelines.md)
