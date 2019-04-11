---
title: サポートされていない機能
ms.date: 03/30/2017
ms.assetid: e480cfb5-697e-42c8-bed5-9264c945c4f9
ms.openlocfilehash: 18a1a8f33a9360b4299648bcd329f4c5f2e7de88
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59097874"
---
# <a name="unsupported-functionality"></a>サポートされていない機能
LINQ to SQL では、次の SQL 機能は、既存の共通言語ランタイム (CLR) および .NET Framework の構成要素の変換からは公開できません。  
  
-   `STDDEV`  
  
-   `LIKE`  
  
     `LIKE` は直接変換によってサポートされませんが、同様の機能が <xref:System.Data.Linq.SqlClient.SqlMethods> クラスにあります。 詳細については、「<xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>」を参照してください。  
  
-   `DATEDIFF`  
  
     LINQ to SQL では、`DATEDIFF` のサポートが制限されています。 同様の機能が <xref:System.Data.Linq.SqlClient.SqlMethods> クラスにあります。  
  
-   `ROUND`  
  
     LINQ to SQL では、`ROUND` のサポートが制限されています。 詳細については、次を参照してください。 [System.Math メソッド](system-math-methods.md)します。  
  
## <a name="see-also"></a>関連項目

- [データ型と関数](data-types-and-functions.md)
