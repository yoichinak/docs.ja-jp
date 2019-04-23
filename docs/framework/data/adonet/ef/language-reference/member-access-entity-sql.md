---
title: . (メンバー アクセス) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4733e3b2-3efa-4b96-b591-ac31350e96ad
ms.openlocfilehash: 6ebedd2b381d035d199e151f64632acf7d502ff5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59139712"
---
# <a name="-member-access-entity-sql"></a>. (メンバー アクセス) (Entity SQL)
ドット演算子 (.) は、[!INCLUDE[esql](../../../../../../includes/esql-md.md)]メンバー アクセス演算子。 メンバー アクセス演算子を使用すると、構造型概念モデル型のインスタンスのプロパティ値またはフィールド値を生成できます。  
  
## <a name="syntax"></a>構文  
  
```  
expression.identifier  
```  
  
## <a name="arguments"></a>引数  
 `expression`  
 構造型概念モデル型のインスタンス。  
  
 `identifier`  
 オブジェクト インスタンスに属するプロパティまたはフィールド。  
  
## <a name="remarks"></a>Remarks  
 ドット (.) 演算子は、複合型またはエンティティ型のプロパティの抽出と同様に、レコードからフィールドを抽出するために使用できます。 たとえば、Name 型の n が Person 型のメンバーであり、p が Person 型のインスタンスである場合、p.n は有効なメンバー アクセス式として Name 型の値を生成します。  
  
 `select p.Name.FirstName from LOB.Person as p`  
  
## <a name="see-also"></a>関連項目

- [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
