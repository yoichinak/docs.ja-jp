---
title: VbStrConv.Wide と VbStrConv.Narrow を組み合わせることはできません
ms.date: 07/20/2015
f1_keywords:
- vbrArgument_IllegalWideNarrow
ms.assetid: a53b4e6a-36b1-4e36-b2c5-8196313ec599
ms.openlocfilehash: 917fcdfcb34778074db6a19c04e12c3cf8de90dc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59307926"
---
# <a name="vbstrconvwide-and-vbstrconvnarrow-cannot-be-combined"></a>VbStrConv.Wide と VbStrConv.Narrow を組み合わせることはできません
アプリケーションが `VbStrConv` 列挙型メンバー `Wide` と `Narrow`を結合しようとしていますが、これらは相互に排他的です。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. `VbStrConv.Wide` または `VbStrConv.Narrow`のいずれかを削除します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Globalization>

- [.NET Framework ベースの国際対応アプリケーションの概要](/visualstudio/ide/introduction-to-international-applications-based-on-the-dotnet-framework)
