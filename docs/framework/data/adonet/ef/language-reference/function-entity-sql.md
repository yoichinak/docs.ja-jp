---
title: FUNCTION (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 0bb88992-37ed-4991-ace5-55be612a2c4d
ms.openlocfilehash: efab5f1abbc5e0c22e404c37dc80dd5aafa09ce1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879607"
---
# <a name="function-entity-sql"></a>FUNCTION (Entity SQL)
Entity SQL クエリ コマンドのスコープに関数を定義します。  
  
## <a name="syntax"></a>構文  
  
```  
FUNCTION function-name  
( [ { parameter_name <type_definition>   
        [ ,...n ]  
  ]  
) AS ( function_expression )   
  
<type_definition>::=  
    { data_type | COLLECTION ( <type_definition> )   
                | REF ( data_type )   
                | ROW ( row_expression )   
        }   
```  
  
## <a name="arguments"></a>引数  
 `function-name`  
 関数名。  
  
 `parameter-name`  
 関数のパラメーター名。  
  
 `function_expression`  
 関数である有効な Entity SQL 式。 関数内のコマンドは、関数に渡される `parameter_name` パラメーターに基づいて実行されます。  
  
 `data_type`  
 サポートされる型の名前。  
  
 COLLECTION ( <type_definition`>` )  
 サポートされる型、行、または参照のコレクションを返す式。  
  
 REF **(**`data_type`**)**  
 エンティティ型への参照を返す式。  
  
 ROW **(**`row_expression`**)**  
 1 つまたは複数の値から構造的に型指定された匿名レコードを返す式。 詳細については、「 [ROW](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md)」を参照してください。  
  
## <a name="remarks"></a>Remarks  
 関数のシグネチャが異なっていれば、名前が同じ複数の関数をインラインで宣言することは可能です。 詳細については、「 [Function Overload Resolution](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md)」を参照してください。  
  
 関数がインラインである場合、Entity SQL コマンドに呼び出せるのは、そのコマンド内で定義された後のみです。 ただし、インライン関数を別のインライン関数内で呼び出す場合には、呼び出される関数が定義される前でも後でもかまいません。 次の例では、関数 B が定義される前に、関数 A が関数 B を呼び出しています。  
  
 `Function A() as ('A calls B. ' + B())`  
  
 `Function B() as ('B was called.')`  
  
 `A()`  
  
 詳細については、「[方法 :ユーザー定義関数を呼び出す](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))します。  
  
 関数をモデル自体で宣言することもできます。 モデルで宣言された関数は、コマンドでインラインで宣言された関数と同じように実行されます。 詳細については、次を参照してください。[ユーザー定義関数](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md)します。  
  
## <a name="example"></a>例  
 次の Entity SQL コマンドは、関数 `Products` を定義します。この関数は、整数値を受け取って、返された製品をフィルター処理します。  
  
 [!code-csharp[DP EntityServices Concepts 2#FUNCTION1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#function1)]  
  
## <a name="example"></a>例  
 次の Entity SQL コマンドは、関数 `StringReturnsCollection` を定義します。この関数は、文字列のコレクションを受け取って、返された連絡先をフィルター処理します。  
  
 [!code-csharp[DP EntityServices Concepts 2#FUNCTION2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#function2)]  
  
## <a name="see-also"></a>関連項目

- [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Entity SQL 言語](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
