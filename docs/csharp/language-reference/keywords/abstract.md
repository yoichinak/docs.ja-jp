---
title: abstract - C# リファレンス
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- abstract
- abstract_CSharpKeyword
helpviewer_keywords:
- abstract keyword [C#]
ms.assetid: b0797770-c1f3-4b4d-9441-b9122602a6bb
ms.openlocfilehash: 547ecd9ff823f61bf3995c02959235b65a4a3979
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606146"
---
# <a name="abstract-c-reference"></a>abstract (C# リファレンス)
`abstract` 修飾子は、その修飾対象の実装が不足しているか、不完全であることを示します。 クラスやメソッド、プロパティ、インデクサー、イベントと組み合わせて abstract 修飾子を使用することができます。 クラス宣言に `abstract` 修飾子を使用して、クラスは他のクラスの基底クラスとしてのみ使用することを意図し、それ自体ではインスタンス化されないことを示します。 abstract としてマークされたメンバーは、その抽象クラスから派生した非抽象クラスによって実装される必要があります。
  
## <a name="example"></a>例  
 この例で、`GetArea` の機能は、`Shape` から派生している `Square` クラスで実装する必要があります。  
  
 [!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]
  
 抽象クラスには次の特徴があります。  
  
- 抽象クラスはインスタンス化できません。  
  
- 抽象クラスには抽象メソッドとアクセサーを記述することができます。  
  
- [sealed](./sealed.md) 修飾子を使って抽象クラスを修飾することはできません。2 つの修飾子が逆の意味を持つためです。 `sealed` 修飾子を指定したクラスは継承が禁止されるのに対し、`abstract` 修飾子を指定したクラスは継承による使用が強制されます。  
  
- 抽象クラスから派生した具象クラスには、継承されたすべての抽象メソッドとアクセサーの実際の機能を実装する必要があります。  
  
 メソッドまたはプロパティに機能が実装されていないことを示すには、そのメソッドまたはプロパティの宣言で `abstract` 修飾子を使います。  
  
 抽象メソッドには次の特徴があります。  
  
- 抽象メソッドは、仮想メソッドの性質を暗に含んでいます。  
  
- 抽象メソッドの宣言は、抽象クラスでしか認められません。  
  
- 抽象メソッドの宣言には実際の機能が実装されないため、メソッドの本体はありません。つまり、メソッドの宣言は、末尾のセミコロンがあるだけで、シグネチャの後ろに中かっこ ({ }) は存在しません。 例:  
  
    ```csharp  
    public abstract void MyMethod();  
    ```  
  
     実際の機能は、メソッド (具象クラスのメンバー) に [override](./override.md) を指定して実装します。  
  
- 抽象メソッドの宣言に [static](./static.md) 修飾子や [virtual](./virtual.md) 修飾子を使うのは誤りです。  
  
 抽象プロパティは、宣言と呼び出しの構文の違いを除けば、抽象メソッドと似た働きを持ちます。  
  
- `abstract` 修飾子を静的プロパティに対して使うのは誤りです。  
  
- 継承する抽象プロパティは、派生クラス内で [override](./override.md) 修飾子を使ったプロパティ宣言を記述することでオーバーライドすることができます。  
  
 抽象クラスの詳細については、「[抽象クラスとシール クラス、およびクラス メンバー](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)」を参照してください。  
  
 すべてのインターフェイス メンバーの機能は、抽象クラスで実装する必要があります。  
  
 インターフェイスを実装する抽象クラスで、インターフェイス メソッドを抽象メソッドにマップすることもできます。 例:  
  
[!code-csharp[csrefKeywordsModifiers#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#2)]
  
## <a name="example"></a>例  
 この例の `DerivedClass` クラスは、抽象クラス `BaseClass` から派生しています。 この抽象クラスには、`AbstractMethod` という抽象メソッドのほか、`X` と `Y` の 2 つの抽象プロパティが存在します。  
  
[!code-csharp[csrefKeywordsModifiers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#3)]
  
 この例の抽象クラスを次のようなステートメントでインスタンス化しようとするとどうなるかを次に示します。  
  
```csharp
BaseClass bc = new BaseClass();   // Error  
```  
  
このように、抽象クラス 'BaseClass' のインスタンスをコンパイラが作成できないことを伝えるエラーが発生します。  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# プログラミング ガイド](../../programming-guide/index.md)
- [修飾子](./modifiers.md)
- [virtual](./virtual.md)
- [override](./override.md)
- [C# のキーワード](./index.md)
