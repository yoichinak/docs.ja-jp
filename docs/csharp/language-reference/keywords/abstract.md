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
ms.openlocfilehash: 5476e99cbd1a5af2acf91ed6bf854fded3425e72
ms.sourcegitcommit: 4c10802ad003374641a2c2373b8a92e3c88babc8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2019
ms.locfileid: "65452454"
---
# <a name="abstract-c-reference"></a>abstract (C# リファレンス)
`abstract` 修飾子は、その修飾対象の実装が不足しているか、不完全であることを示します。 クラスやメソッド、プロパティ、インデクサー、イベントと組み合わせて abstract 修飾子を使用することができます。 クラス宣言に `abstract` 修飾子を使用して、クラスは他のクラスの基底クラスとしてのみ使用することを意図し、それ自体ではインスタンス化されないことを示します。 abstract としてマークされたメンバーは、その抽象クラスから派生したクラスで実装する必要があります。
  
## <a name="example"></a>例  
 この例で、`Area` の機能は、`ShapesClass` から派生している `Square` クラスで実装する必要があります。  
  
 [!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]
  
 抽象クラスには次の特徴があります。  
  
- 抽象クラスはインスタンス化できません。  
  
- 抽象クラスには抽象メソッドとアクセサーを記述することができます。  
  
- [sealed](../../../csharp/language-reference/keywords/sealed.md) 修飾子を使って抽象クラスを修飾することはできません。2 つの修飾子が逆の意味を持つためです。 `sealed` 修飾子を指定したクラスは継承が禁止されるのに対し、`abstract` 修飾子を指定したクラスは継承による使用が強制されます。  
  
- 抽象クラスから派生した具象クラスには、継承されたすべての抽象メソッドとアクセサーの実際の機能を実装する必要があります。  
  
 メソッドまたはプロパティに機能が実装されていないことを示すには、そのメソッドまたはプロパティの宣言で `abstract` 修飾子を使います。  
  
 抽象メソッドには次の特徴があります。  
  
- 抽象メソッドは、仮想メソッドの性質を暗に含んでいます。  
  
- 抽象メソッドの宣言は、抽象クラスでしか認められません。  
  
- 抽象メソッドの宣言には実際の機能が実装されないため、メソッドの本体はありません。つまり、メソッドの宣言は、末尾のセミコロンがあるだけで、シグネチャの後ろに中かっこ ({ }) は存在しません。 次に例を示します。  
  
    ```csharp  
    public abstract void MyMethod();  
    ```  
  
     実際の機能は、メソッド (具象クラスのメンバー) に [override](../../../csharp/language-reference/keywords/override.md) を指定して実装します。  
  
- 抽象メソッドの宣言に [static](../../../csharp/language-reference/keywords/static.md) 修飾子や [virtual](../../../csharp/language-reference/keywords/virtual.md) 修飾子を使うのは誤りです。  
  
 抽象プロパティは、宣言と呼び出しの構文の違いを除けば、抽象メソッドと似た働きを持ちます。  
  
- `abstract` 修飾子を静的プロパティに対して使うのは誤りです。  
  
- 継承する抽象プロパティは、派生クラス内で [override](../../../csharp/language-reference/keywords/override.md) 修飾子を使ったプロパティ宣言を記述することでオーバーライドすることができます。  
  
 抽象クラスの詳細については、「[抽象クラスとシール クラス、およびクラス メンバー](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)」を参照してください。  
  
 すべてのインターフェイス メンバーの機能は、抽象クラスで実装する必要があります。  
  
 インターフェイスを実装する抽象クラスで、インターフェイス メソッドを抽象メソッドにマップすることもできます。 次に例を示します。  
  
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

- [C# リファレンス](../../../csharp/language-reference/index.md)
- [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)
- [修飾子](../../../csharp/language-reference/keywords/modifiers.md)
- [virtual](../../../csharp/language-reference/keywords/virtual.md)
- [override](../../../csharp/language-reference/keywords/override.md)
- [C# のキーワード](../../../csharp/language-reference/keywords/index.md)
