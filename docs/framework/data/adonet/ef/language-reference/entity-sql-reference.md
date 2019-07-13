---
title: Entity SQL リファレンス
ms.date: 03/30/2017
ms.assetid: 61ce7ee1-ffe2-477d-8a9f-835b0a11d900
ms.openlocfilehash: 9b666b83674cb2374409e321a2b715e9910bdd0e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034269"
---
# <a name="entity-sql-reference"></a>Entity SQL リファレンス

このセクションには、Entity SQL リファレンスの記事が含まれています。 この記事をまとめたものです、カテゴリ別の Entity SQL 演算子をグループ化します。

## <a name="arithmetic-operators"></a>算術演算子

算術演算子は、数値データ型が 1 つ以上含まれる 2 つの式の間で、数学的な操作を実行します。 次の表では、Entity SQL の算術演算子を示します。

|演算子|用途|
|--------------|---------|
|[+ (加算)](add.md)|加算。|
|[/ (除算)](divide-entity-sql.md)|除算。|
|[% (剰余)](modulo-entity-sql.md)|除算の剰余|
|[* (乗算)](multiply-entity-sql.md)|乗算。|
|[- (負符号)](negative-entity-sql.md)|否定|
|[- (減算)](subtract-entity-sql.md)|減算。|

## <a name="canonical-functions"></a>正規関数

正規関数とは、すべてのデータ プロバイダーがサポートし、あらゆるクエリ テクノロジで使用できる関数です。 次の表では、正規の関数を示します。

|関数|型|
|--------------|----------|
|[集計 Entity SQL 正規関数](aggregate-canonical-functions.md)|集計 Entity SQL 正規関数をについて説明します。|
|[数値演算正規関数](math-canonical-functions.md)|数値演算の Entity SQL 正規関数をについて説明します。|
|[文字列正規関数](string-canonical-functions.md)|文字列の Entity SQL 正規関数をについて説明します。|
|[日付と時刻の正規関数](date-and-time-canonical-functions.md)|日付と時刻の Entity SQL 正規関数をについて説明します。|
|[ビット単位の正規関数](bitwise-canonical-functions.md)|ビットごとの Entity SQL 正規関数をについて説明します。|
|[その他の正規関数](other-canonical-functions.md)|ビット単位、日付/時刻、文字列、数学、または集計に分類されない関数について説明します。|

## <a name="comparison-operators"></a>比較演算子

比較演算子は、`Byte`、`Int16`、`Int32`、`Int64`、`Double`、`Single`、`Decimal`、`String`、`DateTime`、`Date`、`Time`、`DateTimeOffset` のデータ型に対して定義されます。 比較演算子が適用される前に、オペランドに対して暗黙の型の昇格が行われます。 比較演算子は常にブール値を取得します。 1 つ以上のオペランドが `null` である場合、結果は `null` になります。

等価演算子および非等価演算子は、`Boolean` 型など、ID を持つオブジェクト型に対して定義されます。 ID を含む非プリミティブ オブジェクトは、同じ ID を共有している場合に等価と見なされます。 次の表では、Entity SQL の比較演算子を示します。

|演算子|説明|
|--------------|-----------------|
|[= (等しい)](equals-entity-sql.md)|2 つの式の等価性を比較します。|
|[> (より大きい)](greater-than-entity-sql.md)|2 つの式を比較して、左の式の値が右の式の値よりも大きいかどうかを判別します。|
|[>= (以上)](greater-than-or-equal-to-entity-sql.md)|2 つの式を比較して、左の式の値が右の式の値以上であるかどうかを判別します。|
|[\[いない\]NULL](isnull-entity-sql.md)|クエリ式が NULL かどうかを調べます。|
|[< (より小さい)](less-than-entity-sql.md)|2 つの式を比較して、左の式の値が右の式の値よりも小さいかどうかを判別します。|
|[<= (以下)](less-than-or-equal-to-entity-sql.md)|2 つの式を比較して、左の式の値が右の式の値以下であるかどうかを判別します。|
|[\[いない\]BETWEEN](between-entity-sql.md)|式の結果が指定の範囲内の値になるかどうかを判断します。|
|[\!= (等しくない)](not-equal-to-entity-sql.md)|左の式が右の式と等しくないかどうかを判断する 2 つの式を比較します。|
|[\[いない\]など](like-entity-sql.md)|指定された文字列が指定されたパターンと一致するかどうかを判断します。|

## <a name="logical-and-case-expression-operators"></a>論理と case 式演算子

論理演算子は、条件の真偽をテストします。 CASE 式は、一連のブール式を評価して結果を判定します。 次の表では、論理と CASE 式演算子を示します。

|演算子|説明|
|--------------|-----------------|
|[& & (論理 AND)](and-entity-sql.md)|論理 AND。|
|[\! (論理 NOT)](not-entity-sql.md)|論理 NOT。|
|[&#124;&#124;(論理 OR)](or-entity-sql.md)|論理 OR。|
|[CASE](case-entity-sql.md)|一連のブール式を評価して結果を決定します。|
|[THEN](then-entity-sql.md)|結果、[とき](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387119(v=vs.100))句を true に評価された場合。|

## <a name="query-operators"></a>クエリ演算子

クエリ演算子は、エンティティ データを返すクエリ式を定義するために使用されます。 次の表では、クエリ演算子を示します。

|演算子|用途|
|--------------|---------|
|[FROM](from-entity-sql.md)|使用されているコレクションを示す[選択](select-entity-sql.md)ステートメント。|
|[GROUP BY](group-by-entity-sql.md)|クエリによって返さをオブジェクトにグループを指定します ([選択](select-entity-sql.md)) 式を配置するのには。|
|[GroupPartition](grouppartition-entity-sql.md)|引数値のコレクションを返します。この値は、集計の関係先であるグループ パーティションから投影されたものです。|
|[HAVING](having-entity-sql.md)|グループまたは集計の検索条件を指定します。|
|[LIMIT](limit-entity-sql.md)|使用される、 [ORDER BY](order-by-entity-sql.md)句物理ページングを実行します。|
|[ORDER BY](order-by-entity-sql.md)|返されるオブジェクトで使用される並べ替え順序を指定します、[選択](select-entity-sql.md)ステートメント。|
|[SELECT](select-entity-sql.md)|クエリによって返される投影の要素を指定します。|
|[SKIP](skip-entity-sql.md)|使用される、 [ORDER BY](order-by-entity-sql.md)句物理ページングを実行します。|
|[TOP](top-entity-sql.md)|クエリ結果の先頭から指定した行セットだけを返すよう指定します。|
|[WHERE](where-entity-sql.md)|クエリによって返されるデータを条件に基づいてフィルター処理します。|

## <a name="reference-operators"></a>リファレンス演算子

リファレンスは、特定のエンティティ セットにある特定のエンティティへの論理ポインター (外部キー) です。 Entity SQL では、構築、分解、および参照間を移動するには、次の演算子がサポートされています。

|演算子|用途|
|--------------|---------|
|[CREATEREF](createref-entity-sql.md)|エンティティ セット内のエンティティへの参照を作成します。|
|[DEREF](deref-entity-sql.md)|参照値を逆参照し、その逆参照の結果を生成します。|
|[KEY](key-entity-sql.md)|参照またはエンティティ式のキーを抽出します。|
|[NAVIGATE](navigate-entity-sql.md)|リレーションシップ内のエンティティ型間を移動するために使用します。|
|[REF](ref-entity-sql.md)|エンティティ インスタンスへの参照を返します。|

## <a name="set-operators"></a>集合演算子

Entity SQL では、さまざまな強力な集合演算を提供します。 これには、set 演算子 UNION、INTERSECT、EXCEPT などの TRANSACT-SQL 演算子に似ていますが含まれます、および EXISTS です。 Entity SQL では、重複排除 (SET)、メンバーシップの判定 (IN)、および結合 (JOIN) 演算子もサポートします。 次の表では、Entity SQL の集合演算子を示します。

|演算子|用途|
|--------------|---------|
|[ANYELEMENT](anyelement-entity-sql.md)|複数値のコレクションから要素を抽出します。|
|[EXCEPT](except-entity-sql.md)|EXCEPT オペランドの右側に、クエリ式からも返されない、EXCEPT オペランドの左に、クエリ式から個別の値のコレクションを返します。|
|[\[いない\]EXISTS](exists-entity-sql.md)|コレクションが空かどうかを調べます。|
|[FLATTEN](flatten-entity-sql.md)|コレクションのコレクションをフラット化して単一のコレクションに変換します。|
|[\[いない\]IN](in-entity-sql.md)|コレクション内に一致する値があるかどうかを調べます。|
|[INTERSECT](intersect-entity-sql.md)|INTERSECT オペランドの左右両方のクエリ式によって返される個別の値のコレクションを返します。|
|[OVERLAPS](overlaps-entity-sql.md)|2 つのコレクションに共通の要素が存在するかどうかを調べます。|
|[SET](set-entity-sql.md)|重複する要素をすべて除外した新しいコレクションを生成することによって、オブジェクトのコレクションを 1 つの集合に変換するために使用されます。|
|[UNION](union-entity-sql.md)|複数のクエリの結果を 1 つのコレクションに結合します。|

## <a name="type-operators"></a>型演算子

Entity SQL では、式 (値) を構築、照会、および操作の種類を許可する操作を提供します。 次の表では、型の操作に使用される演算子を示します。

|演算子|用途|
|--------------|---------|
|[CAST](cast-entity-sql.md)|あるデータ型の式を別のデータ型に変換します。|
|[COLLECTION](collection-entity-sql.md)|使用される、[関数](function-entity-sql.md)宣言エンティティ型または複合型のコレクションを操作します。|
|[\[いない\]の](isof-entity-sql.md)|式の型が指定の型であるか、またはそのサブタイプであるかを判断します。|
|[OFTYPE](oftype-entity-sql.md)|クエリ式を使用して、指定された型のオブジェクトのコレクションを返します。|
|[名前付きの型コンストラクター](named-type-constructor-entity-sql.md)|エンティティ型または複合型のインスタンスの作成に使用されます。|
|[MULTISET](multiset-entity-sql.md)|値のリストからマルチセットのインスタンスを作成します。|
|[ROW](row-entity-sql.md)|1 つまたは複数の値から構造的に型付けされた匿名レコードを構築します。|
|[TREAT](treat-entity-sql.md)|特定の基本データ型のオブジェクトを指定の派生型のオブジェクトとして処理します。|

## <a name="other-operators"></a>その他の演算子

次の表では、その他の Entity SQL 演算子を示します。

|演算子|用途|
|--------------|---------|
|[+ (文字列連結)](string-concatenation-entity-sql.md)|Entity SQL で文字列を連結するために使用します。|
|[。(メンバー アクセス)](member-access-entity-sql.md)|構造型概念モデル型のインスタンスのプロパティ値またはフィールド値にアクセスするために使用されます。|
|[-- (コメント)](comment-entity-sql.md)|Entity SQL のコメントが含まれます。|
|[FUNCTION](function-entity-sql.md)|Entity SQL クエリで実行できるインライン関数を定義します。|

## <a name="see-also"></a>関連項目

- [Entity SQL 言語](entity-sql-language.md)
