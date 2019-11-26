---
title: '方法 : 16 進文字列を数値に変換する'
ms.date: 01/31/2018
helpviewer_keywords:
- numbers [Visual Basic], hexadecimals
- hexadecimals [Visual Basic], decimals
- examples [Visual Basic], string conversion
- decimals [Visual Basic], hexadecimals
- string conversion [Visual Basic], hexadecimal to numbers
ms.assetid: 76675807-eadb-4c08-bd50-e6c6ff4b8ced
ms.openlocfilehash: f0a97a0c212a64bfa4db4606ee526b666f07877a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347172"
---
# <a name="how-to-convert-hexadecimal-strings-to-numbers-visual-basic"></a>方法: 16 進文字列を数値に変換する (Visual Basic)

This example converts a hexadecimal string to an integer using the <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> method.

## <a name="to-convert-a-hexadecimal-string-to-a-number"></a>To convert a hexadecimal string to a number

- Use the <xref:System.Convert.ToInt32(System.String,System.Int32)> method to convert the number expressed in base-16 to an integer.

  The first argument of the <xref:System.Convert.ToInt32(System.String,System.Int32)> method is the string to convert. The second argument describes what base the number is expressed in; hexadecimal is base 16.

  [!code-vb[VbVbalrStrings#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#62)]

- Note that the hexadecimal string has the following restrictions:

  - It cannot include the `&h` prefix.
  - It cannot include the `_` digit separator.

  If the prefix or a digit separator is present, the call to the <xref:System.Convert.ToInt32(System.String,System.Int32)> method throws a <xref:System.FormatException>.

## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.Conversion.Hex%2A>
- <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>
