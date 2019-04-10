---
title: LIKE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8300e6d2-875b-481e-9ef4-e1e7c12d46fa
ms.openlocfilehash: 8f210c83a8220f11a5e0a461c8b72466f00a4e37
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197712"
---
# <a name="like-entity-sql"></a>LIKE (Entity SQL)
指定された文字列 `String` が指定されたパターンと一致するかどうかを判断します。  
  
## <a name="syntax"></a>構文  
  
```  
match [NOT] LIKE pattern [ESCAPE escape]  
```  
  
## <a name="arguments"></a>引数  
 `match`  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]に評価される式を`String`します。  
  
 `pattern`  
 指定された `String` に一致するパターン。  
  
 `escape`  
 エスケープ文字。  
  
 NOT  
 LIKE の結果を否定することを指定します。  
  
## <a name="return-value"></a>戻り値  
 `true` 場合、`string`パターンに一致する、それ以外の`false`します。  
  
## <a name="remarks"></a>Remarks  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] LIKE 演算子を使用する式は、フィルター条件として等しいかどうかを使用する式と同じように評価されます。 ただし、 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] LIKE 演算子を使用する式はリテラルとワイルドカード文字の両方を含めることができます。  
  
 次の表では、パターン `string` の構文について説明します。  
  
|ワイルドカード文字|説明|例|  
|------------------------|-----------------|-------------|  
|%|0 個またはそれ以上の文字で構成される任意の `string` です。|`title like '%computer%'` 単語のすべてのタイトルを検索します`"computer"`タイトルにします。|  
|_ (アンダースコア)|任意の 1 文字です。|`firstname like '_ean'` 終わる 4 文字目名前をすべて検索`"ean`、"Dean や Sean など。|  
|[ ]|指定した範囲 ([a-f]) またはセット ([abcdef]) にある任意の 1 文字です。|`lastname like '[C-P]arsen'` 検索は、"arsen"で C と P、Carsen や Larsen などの任意の 1 文字で始まるを姓します。|  
|[^]|指定した範囲 ([^a-f]) またはセット ([^abcdef]) にない任意の 1 文字です。|`lastname like 'de[^l]%'` "de"で始まり、"l"で、次の文字を含めないでくださいするすべての姓を検索します。|  
  
> [!NOTE]
>  [!INCLUDE[esql](../../../../../../includes/esql-md.md)] の LIKE 演算子および ESCAPE 句は、`System.DateTime` または `System.Guid` 値には適用できません。  
  
 LIKE では、ASCII パターン マッチと Unicode パターン マッチがサポートされています。 すべてのパラメーターが ASCII 文字の場合は、ASCII パターン マッチが行われます。 1 つまたは複数の引数が Unicode の場合は、すべての引数が Unicode に変換され、Unicode パターン マッチが行われます。 LIKE で Unicode を使用する場合、後続する空白は意味を持ちます。しかし、Unicode 以外のデータの場合、後続する空白は意味を持ちません。 パターン文字列構文[!INCLUDE[esql](../../../../../../includes/esql-md.md)]のと同じ[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]します。  
  
 パターンは、標準の文字とワイルドカード文字を含むことができます。 パターン マッチ時に、標準の文字は `string` に指定された文字と正確に一致する必要があります。 しかし、ワイルドカード文字は文字列の任意の部分と一致することができます。 ワイルドカード文字を使用する場合、LIKE 演算子は = や != などの文字列比較演算子よりも柔軟です。  
  
> [!NOTE]
>  特定のプロバイダーを対象とする場合は、プロバイダー固有の拡張機能を使用できます。 ただし、たとえばコンストラクターの扱いは、プロバイダーによって異なる場合があります。 SqlServer では、[first-last] および [^first-last] のパターンがサポートされています。前者は先頭と末尾の間の 1 文字が完全に一致し、後者は先頭と末尾の間以外の 1 文字が完全に一致します。  
  
### <a name="escape"></a>エスケープ特殊文字  
 前のセクションの表で説明しているように、ESCAPE 句を使用することで、1 文字以上の特殊なワイルドカード文字を含む文字列を検索できます。 たとえば、複数のドキュメントのタイトルにリテラル "100%" が含まれており、そのドキュメントすべてを検索するとします。 ため、パーセント (%)文字がワイルドカード文字を使用してエスケープする必要があります、[!INCLUDE[esql](../../../../../../includes/esql-md.md)]エスケープ句検索を正常に実行します。 このフィルターの例は次のとおりです。  
  
```  
"title like '%100!%%' escape '!'"  
```  
  
 この検索式では、感嘆符文字 (!) の直後のパーセント ワイルドカード文字 (%) は、ワイルドカード文字としてではなく、リテラルとして処理されます。 以外のエスケープ文字として任意の文字を使用することができます、[!INCLUDE[esql](../../../../../../includes/esql-md.md)]ワイルドカード文字と、正方形の角かっこ (`[ ]`) 文字。 前の例では、感嘆符 (!) 文字はエスケープ文字です。  
  
## <a name="example"></a>例  
 次の 2 つ[!INCLUDE[esql](../../../../../../includes/esql-md.md)]クエリなどを使用して、特定の文字の文字列かどうかを判断する ESCAPE 演算子指定パターンに一致します。 最初のクエリを検索、`Name`文字で始まる`Down_`します。 アンダースコア (`_`) はワイルドカード文字であるため、このクエリは ESCAPE オプションを使用します。 ESCAPE オプションを指定せず、クエリでいずれかの検索は`Name`という単語で始まる値`Down`後にアンダー スコア文字以外の 1 文字。 クエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1.  」の手順に従って[方法。PrimitiveType 結果を返すクエリを実行](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)します。  
  
2.  次のクエリを引数として `ExecutePrimitiveTypeQuery` メソッドに渡します。  
  
 [!code-csharp[DP EntityServices Concepts 2#LIKE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#like)]  
  
## <a name="see-also"></a>関連項目

- [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
