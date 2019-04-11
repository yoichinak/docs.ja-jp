---
title: コンストラクター (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 41fa7bde-8d20-4a3f-a3d2-fb791e128010
ms.openlocfilehash: 53aa7fcc82a476c8b8bd87b059e08bee6741c0d9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073781"
---
# <a name="constructing-types-entity-sql"></a>コンストラクター (Entity SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 次の 3 つの種類のコンス トラクターを提供します。 行コンス トラクター、名前付きの型のコンス トラクター、およびコレクション コンス トラクター。  
  
## <a name="row-constructors"></a>行コンストラクター  
 1 つまたは複数の値から構造的に型付けされた匿名レコードを構築するには、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] の行コンストラクターを使用します。 行コンストラクターの結果の型は、行の構築に使用された値の型に対応するフィールド型を持つ行型です。 たとえば、次の式は型の値を構築します`Record(a int, b string, c int)`:。  
  
 `ROW(1 AS a, "abc" AS b, a + 34 AS c)`  
  
 行コンストラクターで式の別名が指定されていなければ、Entity Framework は別名の生成を試みます。 詳細については、「別名規則」セクションを参照してください。[識別子](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)します。  
  
 次の規則は、行コンストラクターで別名を定義する式に適用されます。  
  
-   行コンストラクターの式で同じコンストラクターの他の別名を参照することはできません。  
  
-   同じ行コンストラクター内の 2 つの式に同じ別名を指定することはできません。  
  
 行コンス トラクターの詳細については、次を参照してください。[行](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md)します。  
  
## <a name="collection-constructors"></a>コレクション コンストラクター  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] のコレクション コンストラクターを使用して、値のリストからマルチセットのインスタンスを作成します。 コンストラクターのすべての値は、相互に互換性のある型 `T` でなければなりません。また、コンストラクターは `Multiset<T>` 型のコレクションを生成します。 たとえば、次の式は整数のコレクションを作成します。  
  
 `Multiset(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
 要素の型が確認できないため、空のマルチセット コンストラクターは使用できません。 次の式は無効です。  
  
 `multiset() {}`  
  
 詳細については、次を参照してください。 [MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md)します。  
  
## <a name="named-type-constructors-namedtype-initializers"></a>名前付きの型コンストラクター (NamedType 初期化子)  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 型コンス トラクター (初期化子) の複合型の名前付きインスタンスを作成し、エンティティ型を使用できます。 たとえば、次の式は `Person` 型のインスタンスを作成します。  
  
 `Person("abc", 12)`  
  
 次の式は、複合型のインスタンスを作成する式です。  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 次の式は、入れ子になった複合型のインスタンスを作成する式です。  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 次の式は、入れ子になった複合型を持つエンティティのインスタンスを作成する式です。  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 次の例は、複合型のプロパティを null に初期化する方法を示しています。 `MyModel.ZipCode(‘98118’, null)`  
  
 コンストラクターに対する引数は、型の属性の宣言と同じ順序であると見なされます。  
  
 詳細については、次を参照してください。[という名前の型コンス トラクター](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md)します。  
  
## <a name="see-also"></a>関連項目

- [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Entity SQL の概要](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [型システム](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md)
