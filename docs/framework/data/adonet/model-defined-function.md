---
title: モデル定義関数
ms.date: 03/30/2017
ms.assetid: 8bb2edc8-e8e7-44c2-adc7-f44e11bda4f0
ms.openlocfilehash: 05a44e86a118b649490cde849c8ca2c2bb0d2f15
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934522"
---
# <a name="model-defined-function"></a>モデル定義関数
*モデル定義関数*は、概念モデルで定義されている関数です。 モデル定義関数の本体は[Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)で表現されます。これにより、関数は、データソースでサポートされているルールまたは言語とは別に表現できます。  
  
 モデル定義関数の定義には、次の情報が含まれます。  
  
- 関数名。 (必須)  
  
- 戻り値の型。 (オプション)  
  
    > [!NOTE]
    > 戻り値の型が指定されていない場合、戻り値は void になります。  
  
- パラメーター情報。 (オプション)  
  
- 関数の本体を定義する[Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)式。  
  
 モデル定義関数では、出力パラメーターがサポートされません。 この制約は、モデル定義関数を構成できるようにするためにあります。  
  
## <a name="example"></a>例  
 下のダイアグラムは、`Book`、`Publisher`、および `Author` という 3 つのエンティティ型の概念モデルを示しています。  
  
 ![公開日を含むモデルを示すスクリーンショット。](./media/model-defined-function/model-published-date-three-entity-types.gif)  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)は、概念スキーマ定義言語 ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) と呼ばれるドメイン固有言語 (DSL) を使用して概念モデルを定義します。 次の CSDL は、`Book` (上のダイアグラムの) の出版以降の年数を返す概念モデルの関数を定義しています。  
  
 [!code-xml[EDM_Example_Model#ModelDefinedFunction](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#modeldefinedfunction)]  
  
## <a name="see-also"></a>関連項目

- [Entity Data Model キーの概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)
- [Entity Data Model:プリミティブデータ型](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)
