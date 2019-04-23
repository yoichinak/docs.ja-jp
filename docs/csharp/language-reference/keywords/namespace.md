---
title: 名前空間キーワード - C# リファレンス
ms.custom: seoapril2019
ms.date: 07/20/2015
f1_keywords:
- namespace_CSharpKeyword
- namespace
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
ms.openlocfilehash: 4859c361b3321c1144204f63896152694f6ac5c9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59148760"
---
# <a name="namespace-c-reference"></a>namespace (C# リファレンス)

`namespace` キーワードは、関連する一連のオブジェクトを含む範囲を宣言するために使用されます。 名前空間を利用し、コード要素を整理したり、グローバルに一意の型を作成したりできます。

[!code-csharp[csrefKeywordsNamespace#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#1)]

## <a name="remarks"></a>解説

名前空間内では、以下の型を 0 個以上宣言できます。

- 別の名前空間

- [class](class.md)

- [interface](interface.md)

- [struct](struct.md)

- [enum](enum.md)

- [delegate](delegate.md)

C# ソース ファイル内に名前空間を明示的に宣言しているかどうかに関係なく、コンパイラは既定の名前空間を追加します。 この無名の名前空間はグローバル名前空間とも呼ばれますが、すべてのファイルに存在します。 グローバル名前空間内にある識別子は、名前付き名前空間で利用できます。

名前空間には暗黙的にパブリック アクセスが設定されます。この属性は変更できません。 名前空間内の要素に割り当てることができるアクセス修飾子については、「[アクセス修飾子](access-modifiers.md)」を参照してください。

名前空間は、2 つ以上の宣言で定義できます。 たとえば、次の例では、`MyCompany` 名前空間の一部として 2 つのクラスを定義しています。

[!code-csharp[csrefKeywordsNamespace#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#2)]

## <a name="example"></a>例

入れ子になった名前空間で静的なメソッドを呼び出す方法の例を次に示します。

[!code-csharp[csrefKeywordsNamespace#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#3)]

## <a name="related-resources"></a>関連資料

名前空間の使用方法の詳細については、次のトピックを参照してください。

- [名前空間](../../programming-guide/namespaces/index.md)

- [名前空間の使用](../../programming-guide/namespaces/using-namespaces.md)

- [方法: グローバル名前空間エイリアスを使用する](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)

## <a name="c-language-specification"></a>C# 言語仕様

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>関連項目

- [C# リファレンス](../../language-reference/index.md)
- [C# プログラミング ガイド](../../programming-guide/index.md)
- [C# のキーワード](index.md)
- [名前空間キーワード](namespace-keywords.md)
- [using](using-directive.md)
- [using static](using-static.md)