---
title: クエリ キーワード - C# リファレンス
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- query keywords [C#]
- LINQ [C#], query keywords
ms.assetid: 6c9bec16-dbd7-4a7c-a060-fe4600b2021f
ms.openlocfilehash: ed931871e8abbfd9ff421a1307fb21c3490493fb
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608457"
---
# <a name="query-keywords-c-reference"></a>クエリ キーワード (C# リファレンス)

このセクションでは、クエリ式で使用するコンテキスト キーワードについて説明します。

## <a name="in-this-section"></a>このセクションの内容

|句|説明|
|------------|-----------------|
|[from](from-clause.md)|データ ソースおよび範囲変数 (反復変数に類似) を指定します。|
|[where](where-clause.md)|論理 AND 演算子 (`&&`) と論理 OR 演算子 (<code>&#124;&#124;</code>) で区切られた 1 つ以上のブール式に基づき、ソース要素をフィルター処理します。|
|[select](select-clause.md)|クエリ実行で返されるシーケンスに含まれる要素の型と形状を指定します。|
|[グループ](group-clause.md)|指定したキー値に基づき、クエリ結果をグループ化します。|
|[into](into.md)|join 句、group 句、または select 句の結果への参照として機能する識別子を指定します。|
|[orderby](orderby-clause.md)|要素型の既定の比較子に基づき、クエリ結果を昇順または降順で並べ替えます。|
|[join](join-clause.md)|指定した 2 つの一致基準の等価比較に基づき、2 つのデータ ソースを結合します。|
|[let](let-clause.md)|範囲変数を使用して、クエリ式のサブ式の結果を格納します。|
|[in](in.md)|[join](join-clause.md) 句のコンテキスト キーワードです。|
|[on](on.md)|[join](join-clause.md) 句のコンテキスト キーワードです。|
|[equals](equals.md)|[join](join-clause.md) 句のコンテキスト キーワードです。|
|[by](by.md)|[group](group-clause.md) 句のコンテキスト キーワードです。|
|[ascending](ascending.md)|[orderby](orderby-clause.md) 句のコンテキスト キーワードです。|
|[descending](descending.md)|[orderby](orderby-clause.md) 句のコンテキスト キーワードです。|

## <a name="see-also"></a>関連項目

- [C# のキーワード](index.md)
- [統合言語クエリ (LINQ)](../../programming-guide/concepts/linq/index.md)
- [LINQ クエリ式](../../programming-guide/linq-query-expressions/index.md)
- [C# の LINQ の概要](../../programming-guide/concepts/linq/getting-started-with-linq.md)
