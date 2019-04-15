---
title: 関数のオーバーロードの解決方法 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 9c648054-3808-4a69-9d3e-98e6a4f9c5ca
ms.openlocfilehash: 0248fdd3f3ba6afb5c7edca740d9aad3ca74bd03
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59302518"
---
# <a name="function-overload-resolution-entity-sql"></a>関数のオーバーロードの解決方法 (Entity SQL)
このトピックでは、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 関数の解決方法について説明します。  
  
 それぞれのシグネチャが一意であれば、複数の関数を同じ名前で定義することは可能です。  
  
 その場合、式でどの関数が参照されているのかを判断するには、以下の基準を適用する必要があります。 これらの基準は順番に適用されます。 1 つの関数のみに該当する最初の基準が、どの関数に解決されるかを決定します。  
  
1. **パラメーター番号**します。 関数が、式で指定されているパラメーター数と同じ数のパラメーターを含んでいます。  
  
2. **型の完全一致**します。 関数の各引数の型が、パラメーターの型と完全に一致するか、NULL リテラルになっています。  
  
3. **サブタイプの一致**します。 関数の各引数の型が、パラメーターの型に完全に一致するか、そのサブタイプになっています。または、引数が NULL リテラルになっています。 複数の関数が、必要なサブタイプの型変換数においてのみ異なる場合は、最も少ないサブタイプの型変換数を持つ関数が、解決された関数になります。  
  
4. **サブタイプまたは型の昇格の一致**します。 関数の各引数の型が、パラメーターの型に完全に一致しているか、そのサブタイプであるか、その型に昇格できます。または、引数が NULL リテラルになっています。 ここでも、複数の関数が、サブタイプの型変換および昇格の数においてのみ異なる場合は、最も少ないサブタイプの型変換および昇格の数を持つ関数が、解決された関数になります。  
  
 これらの基準のいずれによっても 1 つの関数を選択できない場合、関数の呼び出し式はあいまいになります。  
  
 これらの規則を使用して 1 つの関数を抽出できても、引数がパラメーターに一致しない場合があります。 この場合は、エラーが発生します。  
  
 ユーザー定義関数の場合、そのユーザー定義関数に適したシグネチャとモデル定義関数が存在する場合でも、インライン クエリ関数の定義が優先されます。  
  
## <a name="see-also"></a>関連項目

- [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Entity SQL の概要](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [関数](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
