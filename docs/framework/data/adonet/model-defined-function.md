---
title: モデル定義関数
ms.date: 03/30/2017
ms.assetid: 8bb2edc8-e8e7-44c2-adc7-f44e11bda4f0
ms.openlocfilehash: 77152e8f37b009cbc3e72f053ead867914768d3d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59226639"
---
# <a name="model-defined-function"></a>モデル定義関数
A*モデル定義関数*は概念モデルで定義されている関数です。 モデル定義関数の本体がで表される[Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)ルールとは無関係に表現する関数に対応できる、または、データ ソースの言語がサポートされています。  
  
 モデル定義関数の定義には、次の情報が含まれます。  
  
-   関数名。 (必須)  
  
-   戻り値の型。 (オプション)。  
  
    > [!NOTE]
    >  戻り値の型が指定されていない場合、戻り値は void になります。  
  
-   パラメーター情報。 (オプション)。  
  
-   [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)関数の本体を定義する式。  
  
 モデル定義関数では、出力パラメーターがサポートされません。 この制約は、モデル定義関数を構成できるようにするためにあります。  
  
## <a name="example"></a>例  
 下のダイアグラムは、`Book`、`Publisher`、および `Author` という 3 つのエンティティ型の概念モデルを示しています。  
  
 ![発行日付きモデルを示すスクリーン ショット。](./media/model-defined-function/model-published-date-three-entity-types.gif)  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)概念スキーマ定義言語と呼ばれるドメイン固有言語 (DSL) を使用して ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 概念モデルを定義します。 次の CSDL は、`Book` (上のダイアグラムの) の出版以降の年数を返す概念モデルの関数を定義しています。  
  
 [!code-xml[EDM_Example_Model#ModelDefinedFunction](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#modeldefinedfunction)]  
  
## <a name="see-also"></a>関連項目

- [Entity Data Model キーの概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [エンティティ データ モデル](../../../../docs/framework/data/adonet/entity-data-model.md)
- [Entity Data Model:プリミティブ データ型](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)
