---
title: 型 'type1' の値を 'type2' に変換できません
ms.date: 07/20/2015
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
ms.openlocfilehash: c8480c6fab2bff931950ebc21d0a8affe3c41c66
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58827147"
---
# <a name="value-of-type-type1-cannot-be-converted-to-type2"></a>型 'type1' の値を 'type2' に変換できません
型 'type1' の値は、'type2' へ変換できません。 最初の要素の文字列値を取得する、'Value' プロパティを使用することができます '\<parentElement >'。  
  
 XML リテラルを特定の型を暗黙的にキャストしようとしました。 XML リテラルは、指定した型に暗黙的にキャストできません。  
  
 **エラー ID:** BC31194  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   XML リテラルの `Value` プロパティを使用して、その値を `String`として参照します。 `CType` 関数、別の型変換関数、または <xref:System.Convert> クラスを使用して、指定した型として値をキャストします。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Convert>
- [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [XML リテラル](../../../visual-basic/language-reference/xml-literals/index.md)
- [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)
