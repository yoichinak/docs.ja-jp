---
title: 概念モデル正規関数と SQL Server 関数とのマッピング
ms.date: 03/30/2017
ms.assetid: 1a2631bc-a426-4c0a-ba8d-26d9c80d39e2
ms.openlocfilehash: f997fbf39f3dee07cc0d58a39fca779f55236606
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251675"
---
# <a name="conceptual-model-canonical-to-sql-server-functions-mapping"></a>概念モデル正規関数と SQL Server 関数とのマッピング
このトピックでは、概念モデル正規関数を対応する SQL Server 関数にマップする方法について説明します。  
  
## <a name="date-and-time-functions"></a>日付と時刻の関数  
 日付と時刻の関数のマッピングを次の表に示します。  
  
|正規関数|SQL Server 関数|  
|-------------------------|--------------------------|  
|[AddDays (式)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(day, number, date)`|  
|[AddHours(expression)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(hour, number, date)`|  
|[AddMicroseconds(expression)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(microsecond, number, date)`|  
|[AddMilliseconds(expression)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(millisecond, number, date)`|  
|[AddMinutes (式)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(minute, number, date)`|  
|[AddMonths(expression)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(month, number, date)`|  
|[AddNanoseconds 秒 (式)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(nanosecond, number, date)`|  
|[AddSeconds (式)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(second, number, date)`|  
|[AddYears(expression)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(year, number, date)`|  
|[CreateDateTime (year、month、day、hour、minute、second)](./language-reference/date-and-time-canonical-functions.md)|SQL Server 2000 と SQL Server 2005 の場合、書式指定された `datetime` 値がサーバー上に作成されます。 SQL Server 2008 以上の場合、`datetime2` 値がサーバー上に作成されます。|  
|[CreateDateTimeOffset (year、month、day、hour、minute、second、tzoffset)](./language-reference/date-and-time-canonical-functions.md)|書式指定された `datetimeoffset` 値がサーバー上に作成されます。<br /><br /> SQL Server 2000 と SQL Server 2005 ではサポートされません。|  
|[CreateTime (hour, minute, second)](./language-reference/date-and-time-canonical-functions.md)|書式指定された `time` 値がサーバー上に作成されます。<br /><br /> SQL Server 2000 と SQL Server 2005 ではサポートされません。|  
|[CurrentDateTime()](./language-reference/date-and-time-canonical-functions.md)|`SysDateTime()` (SQL Server 2008)。<br /><br /> `GetDate()` (SQL Server 2000 および SQL Server 2005)。|  
|[CurrentDateTimeOffset()](./language-reference/date-and-time-canonical-functions.md)|`SysDateTimeOffset()` (SQL Server 2008)。<br /><br /> SQL Server 2000 と SQL Server 2005 ではサポートされません。|  
|[CurrentUtcDateTime()](./language-reference/date-and-time-canonical-functions.md)|`SysUtcDateTime()` (SQL Server 2008)。 `GetUtcDate()` (SQL Server 2000 および SQL Server 2005)。|  
|[DayOfYear(expression)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(dayofyear, expression)`|  
|[Day(expression)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(day, expression)`|  
|[保存日数 (startExpression、endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(day, startdate, enddate)`|  
|[残存時間 (startExpression、endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(hour, startdate, enddate)`|  
|[Diffgram (startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(microsecond, startdate, enddate)`|  
|[Diffgram (startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(millisecond, startdate, enddate)`|  
|[Diffgram (startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(minute, startdate, enddate)`|  
|[Diffgram (startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(nanosecond, startdate, enddate)`|  
|[Diffgram (startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(second, startdate, enddate)`|  
|[Diffgram (startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(year, startdate, enddate)`|  
|[GetTotalOffsetMinutes (DateTimeOffset)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(tzoffset, expression)`|  
|[Hour (式)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(hour, expression)`|  
|[Millisecond(expression)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(millisecond, expression)`|  
|[Minute (式)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(minute, expression)`|  
|[Month (式)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(month, expression)`|  
|[2番目 (式)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(second, expression)`|  
|[Truncate (式)](./language-reference/date-and-time-canonical-functions.md)|SQL Server 2000 および SQL Server 2005 の場合、切り捨て`datetime`られた形式の値がサーバー上に作成されます。 SQL Server 2008 以降のバージョンでは、切り捨て`datetime2`ら`datetimeoffset`れた値または値がサーバー上に作成されます。|  
|[Year (式)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(YEAR, expression)`|  
  
## <a name="aggregate-functions"></a>集計関数  
 集計関数のマッピングを次の表に示します。  
  
|正規関数|SQL Server 関数|  
|-------------------------|--------------------------|  
|[Avg (式)](./language-reference/aggregate-canonical-functions.md)|`AVG(expression)`|  
|[BigCount(expression)](./language-reference/aggregate-canonical-functions.md)|`BIGCOUNT(expression)`|  
|[Count (式)](./language-reference/aggregate-canonical-functions.md)|`COUNT(expression)`|  
|[Min (式)](./language-reference/aggregate-canonical-functions.md)|`MIN(expression)`|  
|[Max (式)](./language-reference/aggregate-canonical-functions.md)|`MAX(expression)`|  
|[StDev(expression)](./language-reference/aggregate-canonical-functions.md)|`STDEV(expression)`|  
|[StDevP (式)](./language-reference/aggregate-canonical-functions.md)|`STDEVP(expression)`|  
|[Sum(expression)](./language-reference/aggregate-canonical-functions.md)|`SUM(expression)`|  
|[Var(expression)](./language-reference/aggregate-canonical-functions.md)|`VAR(expression)`|  
|[VarP(expression)](./language-reference/aggregate-canonical-functions.md)|`VARP(expression)`|  
  
## <a name="math-functions"></a>数学関数  
 数学関数のマッピングを次の表に示します。  
  
|正規関数|SQL Server 関数|  
|-------------------------|--------------------------|  
|[Abs(value)](./language-reference/math-canonical-functions.md)|`ABS(value)`|  
|[切り上げ (値)](./language-reference/math-canonical-functions.md)|`CEILING(value)`|  
|[Floor(value)](./language-reference/math-canonical-functions.md)|`FLOOR(value)`|  
|[Power(value)](./language-reference/math-canonical-functions.md)|`POWER(value, exponent)`|  
|[Round (値)](./language-reference/math-canonical-functions.md)|`ROUND(value, digits, 0)`|  
|[切捨て](./language-reference/math-canonical-functions.md)|`ROUND(value , digits, 1)`|  
  
## <a name="string-functions"></a>文字列関数  
 文字列関数のマッピングを次の表に示します。  
  
|正規関数|SQL Server 関数|  
|-------------------------|--------------------------|  
|[Contains (string, target)](./language-reference/string-canonical-functions.md)|`CHARINDEX(target, string)`|  
|[Concat (string1, string2)](./language-reference/string-canonical-functions.md)|string1 + string2|  
|[EndsWith(string, target)](./language-reference/string-canonical-functions.md)|`CHARINDEX(REVERSE(target), REVERSE(string)) = 1`<br /><br /> **メモ**が`CHARINDEX`固定長文字列`false`の列`string` に`target`格納され、定数である場合、関数はを返します。 この場合、末尾の埋め込み空白も含めて文字列全体が検索されます。 この問題を回避するには、データを固定長文字列の長さに合わせて切り詰めてから、文字列を `EndsWith` 関数に渡します。たとえば、`EndsWith(TRIM(string), target)` のように指定します。|  
|[IndexOf (target, string2)](./language-reference/string-canonical-functions.md)|`CHARINDEX(target, string2)`|  
|[Left (string1, length)](./language-reference/string-canonical-functions.md)|`LEFT(string1, length)`|  
|[長さ (文字列)](./language-reference/string-canonical-functions.md)|`LEN(string)`|  
|[LTrim(string)](./language-reference/string-canonical-functions.md)|`LTRIM(string)`|  
|[Right (string1, length)](./language-reference/string-canonical-functions.md)|`RIGHT (string1, length)`|  
|[Trim(string)](./language-reference/string-canonical-functions.md)|`LTRIM(RTRIM(string))`|  
|[Replace (string1, string2, string3)](./language-reference/string-canonical-functions.md)|`REPLACE(string1, string2, string3)`|  
|[Reverse (文字列)](./language-reference/string-canonical-functions.md)|`REVERSE (string)`|  
|[RTrim(string)](./language-reference/string-canonical-functions.md)|`RTRIM(string)`|  
|[StartsWith(string, target)](./language-reference/string-canonical-functions.md)|`CHARINDEX(target, string)`|  
|[Substring (文字列,、開始,、長さ)](./language-reference/string-canonical-functions.md)|`SUBSTRING(string, start, length)`|  
|[ToLower(string)](./language-reference/string-canonical-functions.md)|`LOWER(string)`|  
|[ToUpper(string)](./language-reference/string-canonical-functions.md)|`UPPER(string)`|  
  
## <a name="bitwise-functions"></a>ビット単位の関数  
 ビット単位の関数のマッピングを次の表に示します。  
  
|正規関数|SQL Server 関数|  
|-------------------------|--------------------------|  
|[BitWiseAnd (value1, value2)](./language-reference/bitwise-canonical-functions.md)|value1 & value2|  
|[BitWiseNot (値)](./language-reference/bitwise-canonical-functions.md)|~value|  
|[BitWiseOr (value1, value2)](./language-reference/bitwise-canonical-functions.md)|value1 &#124; value2|  
|[BitWiseXor (value1, value2)](./language-reference/bitwise-canonical-functions.md)|value1 ^ value2|
