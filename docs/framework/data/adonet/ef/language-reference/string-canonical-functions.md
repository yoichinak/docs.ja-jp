---
title: 文字列正規関数
ms.date: 03/30/2017
ms.assetid: 5e2cbebd-5df3-47c7-b0e2-49a17ab22bfb
ms.openlocfilehash: 9013b8bd8505442666dd0688eaf2586959a61b70
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249090"
---
# <a name="string-canonical-functions"></a>文字列正規関数
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] には、文字列正規関数が含まれています。  
  
## <a name="remarks"></a>Remarks  
 次の表に、文字列 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 正規関数を示します。  
  
|関数|説明|  
|--------------|-----------------|  
|`Concat(string1, string2)`|`string2` に追加された `string1` を含む文字列を返します。<br /><br /> **引数**<br /><br /> `string1`:を追加する対象`string2`の文字列。<br /><br /> `string2`:に`string1`追加される文字列。<br /><br /> **戻り値**<br /><br /> `String`。 戻り値の文字列の長さが許容される最大長よりも長い場合は、エラーが発生します。<br /><br /> **例**<br /><br /> `-- The following example returns abcxyz.`<br /><br /> `Concat('abc', 'xyz')`|  
|`Contains(string, target)`|`true` が `target` に含まれる場合は、`string` を返します。<br /><br /> **引数**<br /><br /> `string`:検索される文字列。<br /><br /> `target`:検索対象の文字列。<br /><br /> **戻り値**<br /><br /> `true` が `target` に含まれる場合は `string`。それ以外の場合は `false`。<br /><br /> **例**<br /><br /> `-- The following example returns true.`<br /><br /> `Contains('abc', 'bc')`|  
|`EndsWith(string, target)`|`true` が `target` で終わる場合は、`string` を返します。<br /><br /> **引数**<br /><br /> `string`:検索される文字列。<br /><br /> `target`:の`string`末尾で検索する対象の文字列。<br /><br /> **戻り値**<br /><br /> `True` が `string` で終わる場合は `target`。それ以外の場合は `false`。<br /><br /> **例**<br /><br /> `-- The following example returns true.`<br /><br /> `EndsWith('abc', 'bc')` **注:** SQL Server データプロバイダーを使用している場合、文字列が`false`固定長文字列の`target`列に格納され、定数である場合、この関数はを返します。 この場合、末尾の埋め込み空白も含めて文字列全体が検索されます。 この問題を回避するには、データを固定長文字列の長さに合わせて切り詰めます。たとえば、`EndsWith(TRIM(string), target)` のように指定します。|  
|`IndexOf(target, string)`|`target` 内における `string` の位置を返します。見つからない場合は 0 を返します。 `string` の先頭を示す場合は 1 を返します。 インデックスの番号は 1 から始まります。<br /><br /> **引数**<br /><br /> `target`:検索対象の文字列。<br /><br /> `string`:検索される文字列。<br /><br /> **戻り値**<br /><br /> `Int32`。<br /><br /> **例**<br /><br /> `-- The following example returns 4.`<br /><br /> `IndexOf('xyz', 'abcxyz')`|  
|`Left(string, length)`|`length` の左側から最初の `string` 文字を返します。 `string` の長さが `length` よりも短い場合は、文字列全体が返されます。<br /><br /> **引数**<br /><br /> `string`:`String`。<br /><br /> `length`:、、、または`Byte`。 `Int32` `Int16` `Int64` `length` は 0 未満には設定できません。<br /><br /> **戻り値**<br /><br /> `String`。<br /><br /> **例**<br /><br /> `-- The following example returns abc.`<br /><br /> `Left('abcxyz', 3)`|  
|`Length(string)`|文字列の長さ (`Int32`) を文字数として返します。<br /><br /> **引数**<br /><br /> `string`:`String`。<br /><br /> **戻り値**<br /><br /> `Int32`。<br /><br /> **例**<br /><br /> `-- The following example returns 6.`<br /><br /> `Legth('abcxyz')`|  
|`LTrim(string)`|先頭`string`の空白文字を含まないを返します。<br /><br /> **引数**<br /><br /> `String`。<br /><br /> **戻り値**<br /><br /> `String`。<br /><br /> **例**<br /><br /> `-- The following example returns abc.`<br /><br /> `LTrim('   abc')`|  
|`Replace(string1, string2, string3)`|すべての `string1` を `string2` で置き換えた `string3` を返します。<br /><br /> **引数**<br /><br /> `String`。<br /><br /> **戻り値**<br /><br /> `String`。<br /><br /> **例**<br /><br /> `-- The following example returns abcxyz.`<br /><br /> `Concat('abc', 'xyz')`|  
|`Reverse(string)`|文字の順序を逆にした `string` を返します。<br /><br /> **引数**<br /><br /> `String`。<br /><br /> **戻り値**<br /><br /> `String`。<br /><br /> **例**<br /><br /> `-- The following example returns dcba.`<br /><br /> `Reverse('abcd')`|  
|`Right(string, length)`|から最後`length`の文字を返します。`string` `string` の長さが `length` よりも短い場合は、文字列全体が返されます。<br /><br /> **引数**<br /><br /> `string`:`String`。<br /><br /> `length`:、、、または`Byte`。 `Int32` `Int16` `Int64` `length` は 0 未満には設定できません。<br /><br /> **戻り値**<br /><br /> `String`。<br /><br /> **例**<br /><br /> `-- The following example returns xyz.`<br /><br /> `Right('abcxyz', 3)`|  
|`RTrim(string)`|末尾`string`の空白文字を含まないを返します。<br /><br /> **引数**<br /><br /> `String`。<br /><br /> **戻り値**<br /><br /> `String`。|  
|`Substring(string, start, length)`|`start` 位置から長さが `length` 文字の部分文字列を返します。 開始が 1 の場合は、文字列の最初の文字を示します。 インデックスの番号は 1 から始まります。<br /><br /> **引数**<br /><br /> `string`:`String`。<br /><br /> `start`:`Int16`、 、`Int32`および`Byte`。 `Int64` `start` は 1 未満には設定できません。<br /><br /> `length`:`Int16`、 、`Int32`および`Byte`。 `Int64` `length` は 0 未満には設定できません。<br /><br /> **戻り値**<br /><br /> `String`。<br /><br /> **例**<br /><br /> `-- The following example returns xyz.`<br /><br /> `Substring('abcxyz', 4, 3)`|  
|`StartsWith(string, target)`|`true` が `string` で始まる場合は、`target` を返します。<br /><br /> **引数**<br /><br /> `string`:検索される文字列。<br /><br /> `target`:の`string`先頭で検索するターゲット文字列。<br /><br /> **戻り値**<br /><br /> `True` が `string` で始まる場合は `target`。それ以外の場合は `false`。<br /><br /> **例**<br /><br /> `-- The following example returns true.`<br /><br /> `StartsWith('abc', 'ab')`|  
|`ToLower(string)`|大文字が小文字に変換された `string` を返します。<br /><br /> **引数**<br /><br /> `String`。<br /><br /> **戻り値**<br /><br /> `String`。<br /><br /> **例**<br /><br /> `-- The following example returns abc.`<br /><br /> `ToLower('ABC')`|  
|`ToUpper(string)`|小文字が大文字に変換された `string` を返します。<br /><br /> **引数**<br /><br /> `String`。<br /><br /> **戻り値**<br /><br /> `String`。<br /><br /> **例**<br /><br /> `-- The following example returns ABC.`<br /><br /> `ToUpper('abc')`|  
|`Trim(string)`|先頭`string`と末尾の空白文字を除いたを返します。<br /><br /> **引数**<br /><br /> `String`。<br /><br /> **戻り値**<br /><br /> `String`。<br /><br /> **例**<br /><br /> `-- The following example returns abc.`<br /><br /> `Trim('      abc   ')`|  
  
 `null` が入力された場合、これらの関数は `null` を返します。  
  
 同等の機能は、Microsoft SQL クライアント マネージド プロバイダーでも利用できます。 詳細については、「 [SqlClient for Entity Framework Functions](../sqlclient-for-ef-functions.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [正規関数](canonical-functions.md)
