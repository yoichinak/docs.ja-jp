---
title: C# のキーワード
ms.date: 03/07/2017
f1_keywords:
- cs.keywords
helpviewer_keywords:
- keywords [C#]
- C# language, keywords
- Visual C#, keywords
- '@ keyword'
ms.assetid: e929b0f2-4b92-4d37-8060-23d323b098ad
ms.openlocfilehash: 19126eb8bb78643ca1b91a0ddf537033d19cc698
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833232"
---
# <a name="c-keywords"></a>C# のキーワード

キーワードは、コンパイラで特別な意味を持つ、事前に定義されている予約済みの識別子です。 キーワードは、プレフィックスとして `@` を含めない限り、プログラムで識別子として使用できません。 たとえば、`@if` は有効な識別子ですが、`if` は違います。これは、`if` がキーワードだからです。  
  
 このトピックの最初の表では、C# プログラムの予約済み識別子であるキーワードの一覧を示します。 2 番目の表では、C# のコンテキスト キーワードの一覧を示します。 コンテキスト キーワードは、プログラムの限定されたコンテキストでのみ特別な意味を持つもので、そのコンテキストの外部では識別子として使用することができます。 一般に、C# 言語に新しいキーワードが追加されると、それらはコンテキスト キーワードとして追加されます。これは、以前のバージョンで記述されたプログラムの破損を防ぐためです。  
  
|||||  
|---|---|---|---|  
|[abstract](abstract.md)|[as](as.md)|[base](base.md)|[bool](bool.md)|  
|[break](break.md)|[byte](byte.md)|[case](switch.md)|[catch](try-catch.md)|  
|[char](char.md)|[checked](checked.md)|[class](class.md)|[const](const.md)|  
|[continue](continue.md)|[decimal](decimal.md)|[default](default.md)|[delegate](delegate.md)|  
|[do](do.md)|[double](double.md)|[else](if-else.md)|[enum](enum.md)|  
|[event](event.md)|[explicit](explicit.md)|[extern](extern.md)|[false](false-literal.md)|  
|[finally](try-finally.md)|[fixed](fixed-statement.md)|[float](float.md)|[for](for.md)|  
|[foreach](foreach-in.md)|[goto](goto.md)|[if](if-else.md)|[implicit](implicit.md)|  
|[in](in.md)|[int](int.md)|[interface](interface.md)|[internal](internal.md)|
|[is](is.md)|[lock](lock-statement.md)|[long](long.md)|[namespace](namespace.md)|
|[new](new.md)|[null](null.md)|[object](object.md)|[operator](operator.md)|
|[out](out.md)|[override](override.md)|[params](params.md)|[private](private.md)|
|[protected](protected.md)|[public](public.md)|[readonly](readonly.md)|[ref](ref.md)|
|[return](return.md)|[sbyte](sbyte.md)|[sealed](sealed.md)|[short](short.md)||
[sizeof](sizeof.md)|[stackalloc](../operators/stackalloc.md)|[static](static.md)|[string](string.md)|
|[struct](struct.md)|[switch](switch.md)|[this](this.md)|[throw](throw.md)|
|[true](true-literal.md)|[try](try-catch.md)|[typeof](typeof.md)|[uint](uint.md)|
|[ulong](ulong.md)|[unchecked](unchecked.md)|[unsafe](unsafe.md)|[ushort](ushort.md)|
|[using](using.md)|[using static](using-static.md)|[virtual](virtual.md)|[void](void.md)|
|[volatile](volatile.md)|[while](while.md)|

## <a name="contextual-keywords"></a>コンテキスト キーワード

 コンテキスト キーワードを使用して、コード内で特定の意味を付与することができます。ただし C# ではコンテキスト キーワードは予約語ではありません。 `partial` や `where` など、2 つ以上のコンテキストで特別な意味を持つコンテキスト キーワードもあります。  
  
||||  
|---|---|---|  
|[add](add.md)|[alias](extern-alias.md)|[ascending](ascending.md)|
|[async](async.md)|[await](await.md)|[by](by.md)|
|[descending](descending.md)|[dynamic](dynamic.md)|[equals](equals.md)|
|[from](from-clause.md)|[get](get.md)|[global](global.md)|
|[group](group-clause.md)|[into](into.md)|[join](join-clause.md)|
|[let](let-clause.md)|[nameof](nameof.md)|[on](on.md)|
|[orderby](orderby-clause.md)|[partial (型)](partial-type.md)|[partial (メソッド)](partial-method.md)|
|[remove](remove.md)|[select](select-clause.md)|[set](set.md)|
|[value](value.md)|[var](var.md)|[when (フィルター条件)](when.md)|
|[where (ジェネリック型制約)](where-generic-type-constraint.md)|[where (クエリ句)](where-clause.md)|[yield](yield.md)|
  
## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
