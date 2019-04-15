---
title: System.Convert メソッド
ms.date: 03/30/2017
ms.assetid: 3ca6c5b6-ea5d-4ab0-b675-f082135b342c
ms.openlocfilehash: 9836820f2c084a80fcc0a4856f20597716344dfd
ms.sourcegitcommit: 859b2ba0c74a1a5a4ad0d59a3c3af23450995981
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/11/2019
ms.locfileid: "59480652"
---
# <a name="systemconvert-methods"></a>System.Convert メソッド

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 次をサポートしていません<xref:System.Convert>メソッド。

- <xref:System.IFormatProvider> パラメーターを持つ形式。

- 文字配列またはバイト配列を扱うメソッド。

  - <xref:System.Convert.FromBase64CharArray%2A>

  - <xref:System.Convert.ToBase64CharArray%2A>

  - <xref:System.Convert.FromBase64String%2A>

  - <xref:System.Convert.ToBase64String%2A>

- 次のメソッド。

  - `public static <Type2> To<Type2>(<Type1> value);` where

    `Type1` `Type2`はそれぞれの`sbyte`、 `uint`、 `ulong`、または`ushort`します。

  - C#: 

    `int To<int type>(string value, int fromBase),`

    `ToString(... value, int toBase)`

  - Visual Basic: 

    `Function To(Of [Numeric])(value as String, fromBase As Integer)`

    `As [Numeric], ToString( value As …, toBase As Integer)`

  - <xref:System.Convert.IsDBNull%2A>

  - <xref:System.Convert.GetTypeCode%2A>

  - <xref:System.Convert.ChangeType%2A>

## <a name="see-also"></a>関連項目

- [データ型と関数](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
