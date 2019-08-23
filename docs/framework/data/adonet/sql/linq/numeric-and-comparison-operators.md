---
title: 数値演算子および比較演算子
ms.date: 03/30/2017
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
ms.openlocfilehash: ff54856a66ad5e9c0362c013f8df5f1147055cd0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915707"
---
# <a name="numeric-and-comparison-operators"></a>数値演算子および比較演算子

算術演算子と比較演算子は、次の点を除いて、共通言語ランタイム (CLR) では期待どおりに動作します。

- SQL では、浮動小数点数に対して剰余演算子がサポートされません。

- SQL ではチェックされない算術はサポートされません。

- インクリメント演算子とデクリメント演算子は、SQL に複製できない式で使用すると副作用があるため、SQL ではサポートされません。

## <a name="supported-operators"></a>サポートされる演算子

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、次の演算子をサポートしています。

- 基本算術演算子

  - `+`

  - `-` (減算)

  - `*`

  - `/`

  - Visual Basic 整数除算 (`\`)

  - `%` (Visual Basic `Mod`)

  - `<<`

  - `>>`

  - `-` (単項マイナス符号)

- 基本比較演算子

  - Visual Basic `=` および C# `==`

  - Visual Basic `<>` および C# `!=`

  - Visual Basic `Is/IsNot`

  - `<`

  - `<=`

  - `>`

  - `>=`

## <a name="see-also"></a>関連項目

- [データ型と関数](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
- [C# 演算子](../../../../../csharp/language-reference/operators/index.md)
- [演算子](../../../../../visual-basic/language-reference/operators/index.md)
