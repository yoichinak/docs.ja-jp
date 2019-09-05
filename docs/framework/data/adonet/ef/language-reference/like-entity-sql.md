---
title: LIKE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8300e6d2-875b-481e-9ef4-e1e7c12d46fa
ms.openlocfilehash: fbe27f6e25c9d69f092a060fa2c3fbf0abc93318
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250511"
---
# <a name="like-entity-sql"></a>LIKE (Entity SQL)
指定された文字列 `String` が指定されたパターンと一致するかどうかを判断します。  
  
## <a name="syntax"></a>構文  
  
```  
match [NOT] LIKE pattern [ESCAPE escape]  
```  
  
## <a name="arguments"></a>引数  
 `match`  
 に評価される[!INCLUDE[esql](../../../../../../includes/esql-md.md)]式。 `String`  
  
 `pattern`  
 指定された `String` に一致するパターン。  
  
 `escape`  
 エスケープ文字。  
  
 NOT  
 LIKE の結果を否定することを指定します。  
  
## <a name="return-value"></a>戻り値  
 `true` がパターンに一致する場合は `string`、一致しない場合は `false`。  
  
## <a name="remarks"></a>Remarks  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]LIKE 演算子を使用する式は、フィルター条件として等価性を使用する式とほとんど同じように評価されます。 ただし、 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] LIKE 演算子を使用する式には、リテラルとワイルドカード文字の両方を含めることができます。  
  
 次の表では、パターン `string` の構文について説明します。  
  
|ワイルドカード文字|説明|例|  
|------------------------|-----------------|-------------|  
|%|0 個またはそれ以上の文字で構成される任意の `string` です。|`title like '%computer%'`タイトル内の任意の場所`"computer"`にある単語を含むすべてのタイトルを検索します。|  
|_ (アンダースコア)|任意の 1 文字です。|`firstname like '_ean'`で終わる`"ean`4 文字のすべての名を検索します。 "のように、" のようにします。|  
|[ ]|指定した範囲 ([a-f]) またはセット ([abcdef]) にある任意の 1 文字です。|`lastname like '[C-P]arsen'`"arsen" で終わる姓を検索し、C から P までの任意の1文字で始まります (Carsen やなど)。|  
|[^]|指定した範囲 ([^a-f]) またはセット ([^abcdef]) にない任意の 1 文字です。|`lastname like 'de[^l]%'`"de" で始まり、次の文字として "l" を含まない姓をすべて検索します。|  
  
> [!NOTE]
> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] の LIKE 演算子および ESCAPE 句は、`System.DateTime` または `System.Guid` 値には適用できません。  
  
 LIKE では、ASCII パターン マッチと Unicode パターン マッチがサポートされています。 すべてのパラメーターが ASCII 文字の場合は、ASCII パターン マッチが行われます。 1 つまたは複数の引数が Unicode の場合は、すべての引数が Unicode に変換され、Unicode パターン マッチが行われます。 LIKE で Unicode を使用する場合、後続する空白は意味を持ちます。しかし、Unicode 以外のデータの場合、後続する空白は意味を持ちません。 の[!INCLUDE[esql](../../../../../../includes/esql-md.md)]パターン文字列構文は、transact-sql のパターンと同じです。  
  
 パターンは、標準の文字とワイルドカード文字を含むことができます。 パターン マッチ時に、標準の文字は `string` に指定された文字と正確に一致する必要があります。 しかし、ワイルドカード文字は文字列の任意の部分と一致することができます。 ワイルドカード文字を使用する場合、LIKE 演算子は = や != などの文字列比較演算子よりも柔軟です。  
  
> [!NOTE]
> 特定のプロバイダーを対象とする場合は、プロバイダー固有の拡張機能を使用できます。 ただし、たとえばコンストラクターの扱いは、プロバイダーによって異なる場合があります。 SqlServer では、[first-last] および [^first-last] のパターンがサポートされています。前者は先頭と末尾の間の 1 文字が完全に一致し、後者は先頭と末尾の間以外の 1 文字が完全に一致します。  
  
### <a name="escape"></a>Esc キー  
 前のセクションの表で説明しているように、ESCAPE 句を使用することで、1 文字以上の特殊なワイルドカード文字を含む文字列を検索できます。 たとえば、複数のドキュメントのタイトルにリテラル "100%" が含まれており、そのドキュメントすべてを検索するとします。 パーセント (%)文字はワイルドカード文字です。検索を正常に実行[!INCLUDE[esql](../../../../../../includes/esql-md.md)]するには、escape 句を使用してエスケープする必要があります。 このフィルターの例は次のとおりです。  
  
```  
"title like '%100!%%' escape '!'"  
```  
  
 この検索式では、感嘆符文字 (!) の直後のパーセント ワイルドカード文字 (%) は、ワイルドカード文字としてではなく、リテラルとして処理されます。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]ワイルドカード文字と角かっこ (`[ ]`) 文字を除き、任意の文字をエスケープ文字として使用できます。 前の例では、感嘆符 (!) 文字はエスケープ文字です。  
  
## <a name="example"></a>例  
 次の 2 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]つのクエリでは、LIKE 演算子と ESCAPE 演算子を使用して、特定の文字列が指定したパターンに一致するかどうかを判断します。 最初のクエリでは、 `Name`文字`Down_`で始まるが検索されます。 アンダースコア (`_`) はワイルドカード文字であるため、このクエリは ESCAPE オプションを使用します。 ESCAPE オプションを指定しない場合、クエリでは、 `Name`単語`Down`の後にアンダースコア文字以外の任意の1文字が続く値が検索されます。 クエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1. [「方法:PrimitiveType の結果](../how-to-execute-a-query-that-returns-primitivetype-results.md)を返すクエリを実行します。  
  
2. 次のクエリを引数として `ExecutePrimitiveTypeQuery` メソッドに渡します。  
  
 [!code-csharp[DP EntityServices Concepts 2#LIKE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#like)]  
  
## <a name="see-also"></a>関連項目

- [Entity SQL リファレンス](entity-sql-reference.md)
