---
title: 構造体 - C# ガイド
description: 構造体型と、構造体を作成する方法について説明します
ms.date: 10/12/2016
ms.technology: csharp-fundamentals
ms.assetid: a7094b8c-7229-4b6f-82fc-824d0ea0ec40
ms.openlocfilehash: 39bf44dc187fbbc7aac71a1d5c5f3a4d7f446eb8
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739180"
---
# <a name="structs"></a>構造体

"*構造体*" は値の型です。 構造体が作成されると、構造体が割り当てられている変数にはその構造体の実際のデータが設定されます。 構造体が新しい変数に割り当てられると、そのデータがコピーされます。 したがって、新しい変数と元の変数には、同じデータのコピーが別個に含まれることになります。 一方のコピーに対して行われた変更は、もう一方のコピーには影響しません。

値型の変数は、その値を直接含みます。つまり、変数がどのようなコンテキストで宣言されたとしても、必ずメモリがインラインで割り当てられます。 値型の変数には、独立したヒープ割り当てやガベージ コレクションのオーバーヘッドはありません。  
  
値型には、[構造体](./language-reference/keywords/struct.md)と[列挙体](./language-reference/keywords/enum.md)の 2 つのカテゴリがあります。  
  
組み込みの数値型は構造体であり、次のようにしてアクセスできるプロパティとメソッドを持ちます。  
  
[!code-csharp[Static Method](../../samples/snippets/csharp/concepts/structs/static-method.cs)]
  
ただし、宣言とそこへの値の代入は、あたかも単純な非集約型であるかのように行うことができます。  
  
[!code-csharp[Assign Values](../../samples/snippets/csharp/concepts/structs/assign-value.cs)] 
  
値型は、"*シール*" されています。たとえば <xref:System.Int32> から値型を派生させることはできません。構造体は <xref:System.ValueType> からしか継承できないため、任意のユーザー定義型または構造体を継承する構造体を定義することはできません。 ただし、構造体は 1 つ以上のインターフェイスを実装できます。 構造体型は、インターフェイス型にキャストできます。これを行うと、"*ボックス化操作*" によって、構造体がマネージド ヒープ上の参照型オブジェクト内にラップされます。 ボックス化操作が発生するのは、入力パラメーターとして <xref:System.Object> を受け取るメソッドに値型を渡した場合です。 詳細については、「[ボックス化とボックス化解除](./programming-guide/types/boxing-and-unboxing.md )」を参照してください。  
  
独自のカスタム値型を作成するには、[struct](./language-reference/keywords/struct.md) キーワードを使用します。 通常、構造体は、次の例に示すように、少数の関連する変数のコンテナーとして使用します。  
  
[!code-csharp[Struct Keyword](../../samples/snippets/csharp/concepts/structs/struct-keyword.cs)]  
  
.NET Framework における値の型の詳細については、「[共通型システム](../standard/common-type-system.md)」を参照してください。  
    
構造体は、構文上はクラスとほとんど変わりませんが、次のようにクラスよりも制限されます。  
  
- 構造体宣言内では、`const` または `static` と宣言されているフィールド以外は初期化できません。  
  
- 構造体では、パラメーターなしのコンストラクター (パラメーターを伴わないコンストラクター) やファイナライザーを宣言できません。  
  
- 構造体は、割り当て時にコピーされます。 構造体を新しい変数に割り当てると、すべてのデータがコピーされ、新しいコピーを変更しても、元のコピーのデータは変更されません。 これは、Dictionary<string, myStruct> などの値の型のコレクションを使用する際に重要です。  
  
- 構造体は値型ですが、クラスは参照型です。  
  
- クラスとは異なり、構造体は `new` 演算子を使用せずにインスタンス化できます。  
  
- 構造体は、パラメーターのあるコンストラクターを宣言できます。  
  
- 構造体は、他の構造体やクラスから継承できず、基本クラスになることはできません。 すべての構造体が <xref:System.ValueType> を直接継承し、System.ValueType は <xref:System.Object> を継承します。  
  
- 構造体は、インターフェイスを実装できます。

## <a name="nullable-value-types"></a>null 許容値型

値型には、通常、[null](language-reference/keywords/null.md) 値を割り当てることができません。 しかし、型の後ろに `?` を付けることによって、null 値を設定できる値型を作成できます。 たとえば、`int?` は、[null](./language-reference/keywords/null.md) 値も設定できる `int` 型です。 null 許容値型は一般的な構造体型 <xref:System.Nullable%601> のインスタンスです。 null 許容値型は、数値が null または未定義の可能性があるデータベースとの間でデータを受け渡しする場合に、特に便利です。 詳細については、「[null 許容値型](language-reference/builtin-types/nullable-value-types.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [クラス](programming-guide/classes-and-structs/classes.md)
- [基本型](basic-types.md)
