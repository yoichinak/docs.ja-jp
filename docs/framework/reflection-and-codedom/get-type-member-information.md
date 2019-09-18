---
title: '方法: リフレクションを使用して型とメンバーの情報を取得する'
ms.date: 09/03/2019
helpviewer_keywords:
- reflection, obtaining member information
- types [.NET Framework], obtaining member information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
author: rpetrusha
ms.author: ronpet
dev_langs:
- cpp
- csharp
- vb
ms.openlocfilehash: da71845ea276267220636cfd661465ea02b2b50d
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972859"
---
# <a name="how-to-get-type-and-member-information-by-using-reflection"></a>方法: リフレクションを使用して型とメンバーの情報を取得する
<xref:System.Reflection> 名前空間には、型とそのメンバーに関する情報を取得するための多くのメソッドがあります。 この記事では、これらのメソッドの 1 つである <xref:System.Type.GetMembers%2A?displayProperty=nameWithType> を例として示します。 詳細については、「[リフレクションの概要](reflection.md)」を参照してください。
  
## <a name="example"></a>例

リフレクションを使用して型とメンバーの情報を取得する例を次に示します。

[!code-cpp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cpp)]
[!code-csharp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cs)]
[!code-vb[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.vb)]

## <a name="see-also"></a>関連項目

- [アプリケーション ドメインを使用したプログラミング](../app-domains/application-domains.md#programming-with-application-domains)
- [リフレクション](reflection.md)
- [アプリケーション ドメインを使用する](../app-domains/use.md)
