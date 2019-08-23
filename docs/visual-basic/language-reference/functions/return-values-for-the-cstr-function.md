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
ms.openlocfilehash: cd525ea5a295411e509f3bc37285675d15a8c4f4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930045"
---
# <a name="return-values-for-the-cstr-function-visual-basic"></a>CStr 関数の戻り値 (Visual Basic)
次の表では、の`CStr` `expression`さまざまなデータ型について、の戻り値について説明します。  
  
|型`expression`がの場合|`CStr` 戻り値|  
|-----------------------------|--------------------|  
|[Boolean データ型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|"True" または "False" を含む文字列。|  
|[Date データ型](../../../visual-basic/language-reference/data-types/date-data-type.md)|システムの短い日付`Date`形式の値 (日付と時刻) を含む文字列。|  
|[数値のデータ型](../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)|数値を表す文字列。|  
  
## <a name="cstr-and-date"></a>CStr と日付  
 型`Date`には、常に日付と時刻の両方の情報が含まれます。 型変換の場合、Visual Basic は 1/1/0001 (1 年1月1日) を日付の*ニュートラル値*と見なし、00:00:00 (午前0時) はその時刻のニュートラル値と見なされます。 `CStr`結果の文字列にニュートラル値を含めません。 たとえば、文字列に変換`#January 1, 0001 9:30:00#`する場合、結果は "9:30:00 AM" になります。日付情報は表示されません。 ただし、日付情報は依然として元`Date`の値に存在し、など<xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>の関数を使用して回復できます。  
  
> [!NOTE]
> 関数`CStr`は、アプリケーションの現在のカルチャ設定に基づいて変換を実行します。 特定のカルチャの数値の文字列形式を取得するには、数値の`ToString(IFormatProvider)`メソッドを使用します。 たとえば、型`Double`の<xref:System.Double.ToString%2A?displayProperty=nameWithType>値をに`String`変換する場合は、を使用します。  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>
- [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Boolean データ型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [Date データ型](../../../visual-basic/language-reference/data-types/date-data-type.md)
