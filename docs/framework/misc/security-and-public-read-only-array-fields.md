---
title: セキュリティとパブリックの読み取り専用配列フィールド
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], public read-only array fields
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 19b5ad73150697c1442056642a1b11d504ecc426
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59113777"
---
# <a name="security-and-public-read-only-array-fields"></a>セキュリティとパブリックの読み取り専用配列フィールド
パブリックの読み取り専用の配列フィールドを変更できるため、境界の動作またはアプリケーションのセキュリティを定義するのに、マネージ ライブラリからパブリック読み取り専用の配列フィールドを使用しないでください。  
  
## <a name="remarks"></a>Remarks  
 .NET framework の一部のクラスには、プラットフォーム固有の境界パラメーターが含まれている読み取り専用のパブリック フィールドが含まれます。  たとえば、<xref:System.IO.Path.InvalidPathChars>フィールドは、ファイル パスの文字列で許可されていない文字を記述する配列。  .NET Framework 全体で多くの同じフィールドが存在します。  
  
 パブリックの読み取り専用フィールドの値などの<xref:System.IO.Path.InvalidPathChars>コードや、コードのアプリケーション ドメインを共有するコードで変更できます。  アプリケーションの境界の動作を定義するのに次のような読み取り専用のパブリックの配列フィールドを使用しないでください。  場合は、悪意のあるコードは、境界の定義を変更し、予期しない方法でコードを使用します。  
  
 2.0 と .NET Framework の以降のバージョンでは、パブリックの配列フィールドを使用する代わりに新しい配列を返すメソッドを使用してください。  使用する代わりに、たとえば、<xref:System.IO.Path.InvalidPathChars>フィールドを使用する必要がある、<xref:System.IO.Path.GetInvalidPathChars%2A>メソッド。  
  
 .NET Framework の型が内部での境界の種類を定義するパブリック フィールドを使用しないことに注意してください。  代わりに、.NET Framework では、別のプライベート フィールドを使用します。  これらのパブリック フィールドの値を変更しても、.NET Framework 型の動作は変わりません。  
  
## <a name="see-also"></a>関連項目

- [安全なコーディングのガイドライン](../../../docs/standard/security/secure-coding-guidelines.md)
