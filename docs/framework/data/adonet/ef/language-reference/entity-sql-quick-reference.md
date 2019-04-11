---
title: Entity SQL クイック リファレンス
ms.date: 03/30/2017
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
ms.openlocfilehash: b4e3eaf8abd82b63fa2663b47f878ecfa9584897
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207072"
---
# <a name="entity-sql-quick-reference"></a>Entity SQL クイック リファレンス
このトピックでは、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] クエリのクイック リファレンスを提供します。 このトピック内のクエリは、AdventureWorks Sales model に基づいています。  
  
## <a name="literals"></a>リテラル  
  
### <a name="string"></a>String  
 Unicode と非 Unicode の文字列リテラルがあります。 Unicode 文字列の先頭 n. にはたとえば、`N'hello'`します。  
  
 非 Unicode 文字列リテラルの例を次に示します。  
  
```  
'hello'  
--same as  
"hello"  
```  
  
 Output:  
  
|[値]|  
|-----------|  
|hello|  
  
### <a name="datetime"></a>DateTime  
 DateTime リテラルでは、日付部分と時刻部分の両方が必須です。 既定値はありません。  
  
 例:  
  
```  
DATETIME '2006-12-25 01:01:00.000'   
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 Output:  
  
|[値]|  
|-----------|  
|12/25/2006 1:01:00 AM|  
  
### <a name="integer"></a>整数型  
 整数リテラルには Int32 (123) 型、UInt32 (123U) 型、Int64 (123L) 型、および UInt64 (123UL) 型があります。  
  
 例:  
  
```  
--a collection of integers  
{1, 2, 3}  
```  
  
 Output:  
  
|[値]|  
|-----------|  
|1|  
|2|  
|3|  
  
### <a name="other"></a>その他  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] でサポートされているその他のリテラルは、Guid、Binary、Float/Double、Decimal、および `null` です。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] の NULL リテラルは、概念モデルのその他すべての型と互換性があると見なされます。  
  
## <a name="type-constructors"></a>型コンストラクター  
  
### <a name="row"></a>ROW  
 [行](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md)としての匿名の構造的に型指定された (レコード) 値を作成します。 `ROW(1 AS myNumber, ‘Name’ AS myName).`  
  
 例:  
  
```  
SELECT VALUE row (product.ProductID as ProductID, product.Name   
    as ProductName) FROM AdventureWorksEntities.Product AS product  
```  
  
 Output:  
  
|ProductID|名前|  
|---------------|----------|  
|1|Adjustable Race|  
|879|All-Purpose Bike Stand|  
|712|AWC Logo Cap|  
|...|...|  
  
### <a name="multiset"></a>MULTISET  
 [MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md)など、コレクションを構築します。  
  
 `MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`  
  
 例:  
  
```  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 Output:  
  
|ProductID|名前|ProductNumber|…|  
|---------------|----------|-------------------|-------|  
|842|Touring-Panniers, Large|PA-T100|…|  
  
### <a name="object"></a>Object  
 [という名前の型コンス トラクター](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md)など、ユーザー定義の (名前付き) のオブジェクトを構築します`person("abc", 12)`します。  
  
 例:  
  
```  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,   
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,   
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail   
AS o  
```  
  
 Output:  
  
|SalesOrderDetailID|CarrierTrackingNumber|OrderQty|ProductID|...|  
|------------------------|---------------------------|--------------|---------------|---------|  
|1|4911-403C-98|1|776|...|  
|2|4911-403C-98|3|777|...|  
|...|...|...|...|...|  
  
## <a name="references"></a>参照  
  
### <a name="ref"></a>REF  
 [REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)エンティティ型のインスタンスへの参照を作成します。 たとえば、次のクエリは、Orders エンティティ セットの各 Order エンティティへの参照を返します。  
  
```  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 Output:  
  
|[値]|  
|-----------|  
|1|  
|2|  
|3|  
|...|  
  
 次の例では、プロパティ抽出演算子 (.) を使用して、エンティティのプロパティにアクセスします。 プロパティ抽出演算子を使用すると、参照は自動的に逆参照されます。  
  
 例:  
  
```  
SELECT VALUE REF(p).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 Output:  
  
|[値]|  
|-----------|  
|Adjustable Race|  
|All-Purpose Bike Stand|  
|AWC Logo Cap|  
|...|  
  
### <a name="deref"></a>DEREF  
 [DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)参照値とその結果が逆参照を生成を逆参照します。 たとえば、次のクエリは、`SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2` のように、Orders エンティティ セットの各 Order について Order エンティティを生成します。  
  
 例:  
  
```  
SELECT VALUE DEREF(REF(p)).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 Output:  
  
|[値]|  
|-----------|  
|Adjustable Race|  
|All-Purpose Bike Stand|  
|AWC Logo Cap|  
|...|  
  
### <a name="createref-and-key"></a>CREATEREF と KEY  
 [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)キーを渡す参照を作成します。 [キー](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)型参照を持つ式のキー部分を抽出します。  
  
 例:  
  
```  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))   
    FROM AdventureWorksEntities.Product as p  
```  
  
 Output:  
  
|ProductID|  
|---------------|  
|980|  
|365|  
|771|  
|...|  
  
## <a name="functions"></a>関数  
  
### <a name="canonical"></a>正規  
 名前空間を[正規関数](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)としてでは、Edm では、`Edm.Length("string")`します。 正規関数と同じ名前の関数を含んでいる別の名前空間がインポートされない限り、名前空間を指定する必要はありません。 2 つの名前空間に同じ関数が存在する場合は、完全な名前を指定する必要があります。  
  
 例:  
  
```  
SELECT Length(c. FirstName) As NameLen FROM   
    AdventureWorksEntities.Contact AS c   
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 Output:  
  
|NameLen|  
|-------------|  
|6|  
|6|  
|5|  
  
### <a name="microsoft-provider-specific"></a>Microsoft プロバイダー固有  
 [Microsoft プロバイダー固有の関数](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)では、`SqlServer`名前空間。  
  
 例:  
  
```  
SELECT SqlServer.LEN(c.EmailAddress) As EmailLen FROM   
    AdventureWorksEntities.Contact AS c WHERE   
    c.ContactID BETWEEN 10 AND 12  
```  
  
 Output:  
  
|EmailLen|  
|--------------|  
|27|  
|27|  
|26|  
  
## <a name="namespaces"></a>名前空間  
 [使用して](../../../../../../docs/framework/data/adonet/ef/language-reference/using-entity-sql.md)クエリ式で使用される名前空間を指定します。  
  
 例:  
  
```  
using SqlServer; LOWER('AA');  
```  
  
 Output:  
  
|[値]|  
|-----------|  
|aa|  
  
## <a name="paging"></a>ページング  
 ページングを宣言することで表すことができます、[スキップ](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)と[制限](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)サブ句を[ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)句。  
  
 例:  
  
```  
SELECT c.ContactID as ID, c.LastName as Name FROM   
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 Output:  
  
|ID|名前|  
|--------|----------|  
|10|Adina|  
|11|Agcaoili|  
|12|Aguilar|  
  
## <a name="grouping"></a>グループ化  
 [GROUPING BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md)クエリによって返されるオブジェクトにグループを指定します ([選択](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) 式を配置するのには。  
  
 例:  
  
```  
SELECT VALUE name FROM AdventureWorksEntities.Product as P   
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 Output:  
  
|name|  
|----------|  
|LL Mountain Seat Assembly|  
|ML Mountain Seat Assembly|  
|HL Mountain Seat Assembly|  
|...|  
  
## <a name="navigation"></a>ナビゲーション  
 リレーションシップ ナビゲーション操作を使用すると、開始側のエンティティと終了側のエンティティ間のリレーションシップをナビゲートできます。 [NAVIGATE](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md)として修飾されるリレーションシップ型では\<名前空間 >.\<リレーションシップ型の名前 >。 移動 Ref を返します\<T > 場合のカーディナリティ、終了するは 1 です。 場合のカーディナリティの終了が n、コレクション < Ref\<T >> が返されます。  
  
 例:  
  
```  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM   
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)   
    FROM AdventureWorksEntities.Address AS a  
```  
  
 Output:  
  
|AddressID|  
|---------------|  
|1|  
|2|  
|3|  
|...|  
  
## <a name="select-value-and-select"></a>SELECT VALUE AND SELECT  
  
### <a name="select-value"></a>SELECT VALUE  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 暗黙の行の構築をスキップする SELECT VALUE 句を提供します。 SELECT VALUE 句には 1 つの項目のみを指定できます。 場合、このような句を使用して、SELECT 句内の項目に row ラッパーは構築されず、および、必要な構造のコレクションの作成例:`SELECT VALUE a`します。  
  
 例:  
  
```  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product as p  
```  
  
 Output:  
  
|名前|  
|----------|  
|Adjustable Race|  
|All-Purpose Bike Stand|  
|AWC Logo Cap|  
|...|  
  
### <a name="select"></a>SELECT  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] また、任意の行を構築する行コンス トラクターを提供します。 SELECT は、投影内の 1 つまたは複数の要素、および `SELECT a, b, c` などのフィールドを持つデータ レコードの結果を取得します。  
  
 例:  
  
 SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:  
  
|名前|ProductID|  
|----------|---------------|  
|Adjustable Race|1|  
|All-Purpose Bike Stand|879|  
|AWC Logo Cap|712|  
|...|...|  
  
## <a name="case-expression"></a>CASE 式  
 [Case 式](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md)一連の結果を決定するブール式を評価します。  
  
 例:  
  
```  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 Output:  
  
|[値]|  
|-----------|  
|true|  
  
## <a name="see-also"></a>関連項目

- [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Entity SQL の概要](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
