---
title: typeof - C# リファレンス
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- typeof
- typeof_CSharpKeyword
helpviewer_keywords:
- typeof keyword [C#]
ms.assetid: 0c08d880-515e-46bb-8cd2-48b8dd62c08d
ms.openlocfilehash: 7962a3d0a5885e64701cb9d9a4d689cd982b9830
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422554"
---
# <a name="typeof-c-reference"></a>typeof (C# リファレンス)

型の <xref:System.Type?displayProperty=nameWithType> オブジェクトを取得するために使用されます。 `typeof` 式は次の形式になります。

```csharp
System.Type type = typeof(int);
```

## <a name="remarks"></a>コメント

式の実行時の型を取得する場合は、次の例のように、.NET Framework のメソッド <xref:System.Object.GetType%2A> を使用できます。

```csharp
int i = 0;
System.Type type = i.GetType();
```

`typeof` 演算子はオーバーロードできません。

`typeof` 演算子は、オープン ジェネリック型に対しても使用できます。 複数の型パラメーターを持つ型には、適切な数のコンマを指定する必要があります。 たとえば、<xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWIthType> には 2 つの型引数があるため、1 つのコンマを使用します。

```csharp
Type t = typeof(System.Collection.Generic.Dictionary<,>);
```

次の例は、メソッドの戻り値の型がジェネリック <xref:System.Collections.Generic.IEnumerable%601> であるかどうかを確認する方法を示しています。 <xref:System.Type.GetInterface%2A?displayProperty=nameWithType> では、戻り値の型が <xref:System.Collections.Generic.IEnumerable%601> でない場合、`null` ジェネリック型が返されます。

[!code-csharp[typeof_3.cs](~/samples/snippets/csharp/keywords/typeof/typeof_3.cs)]

## <a name="example"></a>例

[!code-csharp[csrefKeywordsOperator#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#12)] 

## <a name="example"></a>例

このサンプルでは、<xref:System.Object.GetType%2A> メソッドを使用して、数値計算結果の格納に使用される型を確認しています。 これは、結果の数のストレージ要件によって変わります。

[!code-csharp[csrefKeywordsOperator#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#13)]

## <a name="c-language-specification"></a>C# 言語仕様

詳細については、「[C# 言語仕様](../language-specification/index.md)」の [typeof 演算子](~/_csharplang/spec/expressions.md#the-typeof-operator)に関するセクションを参照してください。 言語仕様は、C# の構文と使用法に関する信頼性のある情報源です。

## <a name="see-also"></a>関連項目

- <xref:System.Type?displayProperty=nameWithType>
- [C# リファレンス](../../../csharp/language-reference/index.md)
- [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)
- [C# のキーワード](../../../csharp/language-reference/keywords/index.md)
- [is](../../../csharp/language-reference/keywords/is.md)
