---
title: 構造体の使用 - C# プログラミング ガイド
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- structs [C#], using
ms.assetid: cea4a459-9eb9-442b-8d08-490e0797ba38
ms.openlocfilehash: 0e0ba1602468d1bcc38985c78e1af5e4d2a5912c
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586086"
---
# <a name="using-structs-c-programming-guide"></a>構造体の使用 (C# プログラミング ガイド)
`struct` 型は、 `Point`、 `Rectangle`、 `Color`などの軽量のオブジェクトを表すのに適しています。 点を表すには [自動実装プロパティ](../../../csharp/language-reference/keywords/class.md) がある [クラス](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)を使用するのと同じくらい便利ですが、シナリオによっては [構造体](../../../csharp/language-reference/keywords/struct.md) を使用する方がより効率的です。 たとえば、1,000 個の `Point` オブジェクトから成る配列を宣言する場合は、各オブジェクトの参照用に追加のメモリを割り当てます。この場合、構造体であれば処理上の負荷を抑えることができます。 .NET Framework には <xref:System.Drawing.Point> という名前のオブジェクトが含まれているため、この例の構造体には代わりに "Coords" という名前が付けられています。  
  
 [!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]  
  
 構造体に既定の (パラメーターなしの) コンストラクターを定義するとエラーになります。 また、構造体の本体のインスタンス フィールドを初期化した場合もエラーになります。 外部アクセス可能な構造体メンバーを初期化するには、パラメーター化されたコンストラクター、暗黙的なパラメーターなしのコンストラクター、[オブジェクト初期化子](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)を使用するか、構造体を宣言した後で個別にメンバーにアクセスする必要があります。 プライベートかそれ以外の理由でアクセスできないメンバーの場合、コンストラクターを独占的に使用する必要があります。
  
 [new](../../../csharp/language-reference/keywords/new.md) 演算子を使用して struct オブジェクトを作成すると、[コンストラクター シグネチャ](../../../csharp/programming-guide/classes-and-structs/constructors.md#constructor-syntax)に基づき、オブジェクトが作成されて適切なコンストラクターが呼び出されます。 クラスとは異なり、構造体は `new` 演算子を使用せずにインスタンス化できます。 このような場合、コンストラクターの呼び出しが行われないため、割り当てがより効率的になります。 ただし、各フィールドは未割り当てのままになり、すべてのフィールドが初期化されるまではオブジェクトを使用できません。 たとえば、プロパティから値を取得または設定することができません。
 
 既定の、パラメーターのないコンストラクターを利用して構造体オブジェクトを初期化する場合、その[既定値](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md)に基づいてすべてのメンバーが割り当てられます。
  
 構造体のパラメーターを使用してコンストラクターを記述するとき、すべてのメンバーを明示的に初期化する必要があります。それをしない場合、1 つまたは複数のメンバーが未割り当てのままとなり、構造体を使用できず、コンパイラ エラー CS0171 が出ます。  
  
 クラスには継承がありますが、構造体には継承がありません。 構造体は、他の構造体やクラスから継承できず、基本クラスになることはできません。 ただし、構造体は、基本クラス <xref:System.Object>から継承します。 構造体は、クラスの場合とまったく同じ方法でインターフェイスを実装できます。  
  
 `struct`キーワードを使用してクラスを宣言することはできません。 C# では、クラスと構造体は、意味が異なります。 構造体は値型ですが、クラスは参照型です。 詳細については、「 [Value Types (値型)](../../../csharp/language-reference/keywords/value-types.md)」を参照してください。  
  
 参照型の機能が必要な場合以外は、小さいクラスを構造体として宣言した方が、システムによってより効率的に処理される可能性があります。  
  
## <a name="example-1"></a>例 1  
  
### <a name="description"></a>説明  
 既定のコンストラクターとパラメーター化されたコンストラクターの両方を使用した `struct` の初期化の例を次に示します。  
  
### <a name="code"></a>コード  
 [!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]  
  
 [!code-csharp[csProgGuideObjects#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#2)]  
  
## <a name="example-2"></a>例 2  
  
### <a name="description"></a>説明  
 構造体に固有の機能を次の例に示します。 この例では、`new` 演算子を使用せずに Coords オブジェクトを作成しています。 `struct` を `class`という単語に置き換えた場合、プログラムはコンパイルされません。  
  
### <a name="code"></a>コード  
 [!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]  
  
 [!code-csharp[csProgGuideObjects#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#3)]  
  
## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)
- [クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md)
- [構造体](../../../csharp/programming-guide/classes-and-structs/structs.md)
