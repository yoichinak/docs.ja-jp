---
title: 定数は、class、structure、または array 型ではなく、組み込み型または列挙型でなければなりません。
ms.date: 07/20/2015
f1_keywords:
- vbc30424
- bc30424
helpviewer_keywords:
- BC30424
ms.assetid: 2d402c2f-27ad-428b-b699-d45cd62f7196
ms.openlocfilehash: 88bbab2005b464ee97d647f2b4b9be6ff81e2d82
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61649843"
---
# <a name="constants-must-be-of-an-intrinsic-or-enumerated-type-not-a-class-structure-type-parameter-or-array-type"></a>定数は、class、structure、または array 型ではなく、組み込み型または列挙型でなければなりません。
クラス、構造体、または配列型、またはそれを含むジェネリック型で定義された型パラメーターと定数を宣言しようとしました。  
  
 組み込み型の定数があります (`Boolean`、 `Byte`、 `Date`、 `Decimal`、 `Double`、 `Integer`、 `Long`、 `Object`、 `SByte`、 `Short`、 `Single`、 `String`、 `UInteger`、 `ULong`、または`UShort`)、または`Enum`型が整数型のいずれかに基づきます。  
  
 **エラー ID:** BC30424  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. 組み込み関数として定数を宣言または`Enum`型。  
  
2. 定数にはまた、特殊な値など`True`、 `False`、または`Nothing`します。 コンパイラでは、これらの定義済み値の適切な組み込み型と見なします。  
  
## <a name="see-also"></a>関連項目

- [定数と列挙体](../../../visual-basic/language-reference/constants-and-enumerations.md)
- [データの種類](../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [データの種類](../../../visual-basic/language-reference/data-types/index.md)
