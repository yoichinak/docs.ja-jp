---
title: CStr 関数の戻り値 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- times [Visual Basic], CStr Function return values
- type conversion [Visual Basic]
- dates [Visual Basic], CStr Function return values
- CStr function
- strings [Visual Basic], return value
- Date data type [Visual Basic], converting
- dates [Visual Basic]
- String data type [Visual Basic], converting
ms.assetid: 3aa744e7-1419-45d5-85e3-e5abc2953673
ms.openlocfilehash: 3653194c7e48533e664ac7513ca7f4f48d1c69f7
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819516"
---
# <a name="return-values-for-the-cstr-function-visual-basic"></a>CStr 関数の戻り値 (Visual Basic)
次の表は、戻り値の`CStr`のさまざまなデータ型の`expression`します。  
  
|場合`expression`型|`CStr` 戻り値|  
|-----------------------------|--------------------|  
|[Boolean データ型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|"True"を含む文字列または"False"。|  
|[Date データ型](../../../visual-basic/language-reference/data-types/date-data-type.md)|含んでいる文字列を`Date`システムの短い日付形式で値 (日付と時刻)。|  
|[数値のデータ型](../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)|数値を表す文字列。|  
  
## <a name="cstr-and-date"></a>CStr と日付  
 `Date`型には常に日付と時刻の両方の情報が含まれています。 型変換のために、Visual Basic であると見なす 1/1/0001 (年 1 月 1日年 1 月)、*ニュートラル値*を時間のニュートラル値の日付、および 00時 00分: 00 (午前 0 時)。 `CStr` 結果の文字列には基準値は含まれません。 たとえば、変換する`#January 1, 0001 9:30:00#`結果は"9時 30分: 00 AM"を文字列には、日付情報は表示されません。 ただし、日付情報は、元に引き続き存在`Date`値し、などの関数で回復できる<xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>します。  
  
> [!NOTE]
>  `CStr`関数は、アプリケーションの現在のカルチャ設定に基づいて変換を実行します。 特定のカルチャの数値の文字列形式を取得するには、数値を使用`ToString(IFormatProvider)`メソッド。 たとえば、使用して<xref:System.Double.ToString%2A?displayProperty=nameWithType>型の値を変換するときに`Double`を`String`します。  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>
- [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Boolean データ型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [Date データ型](../../../visual-basic/language-reference/data-types/date-data-type.md)
