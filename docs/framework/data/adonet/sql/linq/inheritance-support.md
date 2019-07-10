---
title: 継承のサポート
ms.date: 03/30/2017
ms.assetid: 19bb2794-b4e7-402e-8307-1d1517381a08
ms.openlocfilehash: 576fa896364d603f2cdbb7b6532e3efc3cd6f674
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743077"
---
# <a name="inheritance-support"></a>継承のサポート
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] サポート*シングル テーブル マッピング*します。 これは、1 つの継承階層全体が単一のデータベース テーブルに保存されることを意味します。 テーブルには、階層構造内で使用され得るすべてのデータ列の平坦化された共用体が格納されます (2 つのテーブルを 1 つに結合し、元のテーブルのいずれかにあった行が新しいテーブルに含まれるようにした結果、1 つの共用体が形成されます)。行によって表されるインスタンスの型に適合しない列には null が設定されます。  
  
 シングル テーブル マッピング形式は、継承を表す最も単純な形式であり、多くのクエリのカテゴリで良好なパフォーマンス特性を示します。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] でこのマッピングを実装するには、継承階層のルート クラスで属性および属性プロパティを指定する必要があります。 詳細については、「[方法 :継承階層を割り当てる](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md)します。  
  
 Visual Studio を使用している開発者は、オブジェクト リレーショナル デザイナーを使用しても継承階層を割り当てます。  
  
## <a name="see-also"></a>関連項目

- [背景情報](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
