---
title: ユーザー定義関数 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3f9e6bbd-8e5a-43e1-809f-f8a61338e522
ms.openlocfilehash: 4922e7fada676a6c26042236ccdb6315d6d455ae
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59104625"
---
# <a name="user-defined-functions-entity-sql"></a>ユーザー定義関数 (Entity SQL)
Entity SQL では、クエリ内でのユーザー定義関数の呼び出しがサポートされます。 これらのクエリを使用して関数をインラインを定義することができます (を参照してください[方法。ユーザー定義関数を呼び出す](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))) または概念モデルの一部として (を参照してください[方法。概念モデルでカスタム関数を定義](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)))。 Entity SQL コマンドを概念モデルの関数が定義されている、 [DefiningExpression](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#definingexpression-element-csdl)の要素を[関数](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#function-element-csdl)概念モデル内の要素。  
  
 Entity SQL を使用すると、関数をクエリ コマンド自体で定義することができます。 [関数](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md)演算子は、インライン関数を定義します。 複数の関数を 1 つのコマンドで定義することができます。関数の署名が一意であれば、これら複数の関数に同じ名前を付けることができます。 詳細については、「 [Function Overload Resolution](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [関数](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
