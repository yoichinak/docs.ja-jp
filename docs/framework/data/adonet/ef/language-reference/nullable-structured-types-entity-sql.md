---
title: NULL 値が許容される構造化型 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ae006fa9-997e-45bb-8a04-a7f62026171e
ms.openlocfilehash: 632b092e1d0d99a2a40cc3cd4b323e234de6232b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59127856"
---
# <a name="nullable-structured-types-entity-sql"></a>NULL 値が許容される構造化型 (Entity SQL)
構造化型の `null` インスタンスは、存在しないインスタンスです。 これは、すべてのプロパティの値が `null` であるインスタンスとは異なります。  
  
 このトピックでは、NULL 値が許容される構造化型について説明します。この内容には、NULL 値が許容される型、および構造化 NULL 値が許容される型の `null` インスタンスを生成するコード パターンも含まれます。  
  
## <a name="kinds-of-nullable-structured-types"></a>NULL 値が許容される構造化型の種類  
 NULL 値が許容される構造化型には、3 つの種類があります。  
  
-   行型。  
  
-   複合型。  
  
-   エンティティ型。  
  
## <a name="code-patterns-that-produce-null-instances-of-structured-types"></a>構造化型の NULL インスタンスを生成するコード パターン  
 次のシナリオは、`null` インスタンスを生成します。  
  
-   構造化型としての `null` の構造化  
  
    ```  
    TREAT (NULL AS StructuredType)  
    ```  
  
-   派生型に対する基本データ型のキャスト  
  
    ```  
    TREAT (BaseType AS DerivedType)  
    ```  
  
-   false の条件での外部結合  
  
    ```  
    Collection1 LEFT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     --または  
  
    ```  
    Collection1 RIGHT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     --または  
  
    ```  
    Collection1 FULL OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
-   `null` 参照の逆参照  
  
    ```  
    DEREF(NullRef)  
    ```  
  
-   空のコレクションからの ANYELEMENT の取得  
  
    ```  
    ANYELEMENT(EmptyCollection)  
    ```  
  
-   構造化型の `null` インスタンスのチェック  
  
    ```csharp  
    ...  
    for (int i = 0; i < reader.FieldCount; i++)  
    {  
        if (reader.IsDBNull(i))  
        {  
            Console.WriteLine("[NULL]");  
        }  
        else  
        {  
            Console.WriteLine(reader.GetValue(i).ToString());  
        }  
    }  
    ```  
  
## <a name="see-also"></a>関連項目

- [Entity SQL の概要](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
