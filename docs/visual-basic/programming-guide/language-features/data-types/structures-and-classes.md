---
title: 構造体とクラス (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], vs. structures
- structures [Visual Basic]
- classes [Visual Basic]
- structures [Visual Basic], compared to classes
- structures [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: a221e74a-ffcf-4bdc-a0f6-a088a9bf26cc
ms.openlocfilehash: 3635729705520518d4c950f8a79da7d1249285bf
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58841616"
---
# <a name="structures-and-classes-visual-basic"></a>構造体とクラス (Visual Basic)
Visual Basic では、構造体と 2 つのエンティティに同じ機能のほとんどがサポートされる結果と共に、クラスの構文は統一します。 ただし、構造体とクラスの重要な違いもします。  
  
 クラスが参照型になるというメリットがある、参照を渡すことは、そのすべてのデータと構造体変数を渡すより効率的です。 その一方で、構造体では、グローバルなヒープ メモリの割り当ては必要ありません。  
  
 構造体から継承することはできません、ため、構造体を拡張する必要のないオブジェクトに対してのみ使用してください。 構造体を使用して、作成するオブジェクトは、s インスタンスのサイズし、構造体とクラスのパフォーマンス特性を考慮します。  
  
## <a name="similarities"></a>類似点  
 構造体とクラスは、次の点で似ています。  
  
-   両方とも*コンテナー*型、メンバーとして他の種類が含まれていることを意味します。  
  
-   両方があるメンバーで、コンス トラクター、メソッド、プロパティ、フィールド、定数、列挙型、イベント、およびイベント ハンドラーを含めることができます。 ただし、これらのメンバーの宣言とを混同しないでください*要素*構造体の。  
  
-   どちらのメンバーは、アクセス レベルを個別があることができます。 たとえば、1 つのメンバーを宣言できます`Public`別および`Private`します。  
  
-   インターフェイスを両方実装できます。  
  
-   両方共有することが、コンス トラクター パラメーターの有無。  
  
-   両方を公開できます、*プロパティの既定*、そのプロパティは、少なくとも 1 つのパラメーターを受け取ります。  
  
-   両方を宣言してイベントを発生させるし、デリゲートを宣言できます。  
  
## <a name="differences"></a>相違点  
 構造体とクラスは、次のとおりで異なります。  
  
-   構造体が*値の型*; クラスは、*参照型*します。 クラス型としてのデータへの参照を格納しているのではなく、構造体型の変数には、構造体のデータが含まれています。  
  
-   構造体を使用して、スタック割り当てです。クラスは、ヒープの割り当てを使用します。  
  
-   構造体のすべての要素は`Public`既定ではクラスの変数と定数は`Private`他のクラス メンバーは、既定で`Public`既定。 クラス メンバーには、この動作は、既定の Visual Basic 6.0 のシステムとの互換性を提供します。  
  
-   構造体の有効期限がありますに少なくとも 1 つの非共有変数または非共有、カスタム イベントの要素。クラスは、完全に空にすることができます。  
  
-   構造体の要素として宣言できません`Protected`; クラスのメンバーのことができます。  
  
-   構造体のプロシージャはイベントを処理できる場合にのみ、 [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) `Sub`プロシージャとのことによってのみ、 [AddHandler ステートメント](../../../../visual-basic/language-reference/statements/addhandler-statement.md); 任意のクラスのプロシージャは、いずれかのを使用して、イベントを処理できます[処理](../../../../visual-basic/language-reference/statements/handles-clause.md)キーワードまたは`AddHandler`ステートメント。 詳細については、「[イベント](../../../../visual-basic/programming-guide/language-features/events/index.md)」を参照してください。  
  
-   構造体の変数宣言は、初期化子または配列の初期サイズを指定できません。クラスの変数宣言できます。  
  
-   構造体は暗黙的に継承、<xref:System.ValueType?displayProperty=nameWithType>クラスし、その他の型から継承できませんクラスが以外のすべてのクラスまたはクラスから継承できます<xref:System.ValueType?displayProperty=nameWithType>します。  
  
-   構造体が継承可能です。クラスです。  
  
-   共通言語ランタイム (CLR) を呼び出すことはありませんので、構造体は終了ことはありませんが、<xref:System.Object.Finalize%2A>メソッド、構造体をクラスが呼び出すガベージ コレクター (GC) によって終了<xref:System.Object.Finalize%2A>アクティブな参照はありませんが検出されたときに、クラスの残りの。  
  
-   構造体にコンス トラクターが必要としません。クラスは。  
  
-   構造体を持つことができますパラメーターをとる場合にのみ、非共有コンス トラクター。パラメーターの有無は、クラスでそれらを持つことができます。  
  
 すべての構造体には、パラメーターを指定せず、暗黙の型のパブリック コンス トラクターがあります。 このコンス トラクターでは、既定値に構造体のすべてのデータ要素を初期化します。 この動作を再定義することはできません。  
  
## <a name="instances-and-variables"></a>インスタンスと変数  
 構造体は値型であるために、各構造体変数は個別の構造体インスタンスに完全にバインドされます。 クラスは参照型、およびオブジェクト変数は、異なる時刻でさまざまなクラスのインスタンスを参照できます。 このような区別では、次の方法で構造体とクラスの使用量に影響します。  
  
-   **初期化します。** 構造体変数には、構造体のパラメーターなしのコンス トラクターを使用して要素の初期化で、暗黙的に含まれています。 そのため、`Dim s As struct1`と等価`Dim s As struct1 = New struct1()`します。  
  
-   **変数の代入。** 構造体の 1 つの変数を別に代入するか、またはプロシージャの引数に構造体のインスタンスを渡すときに、変数のすべての要素の現在の値は、新しい構造にコピーされます。 別、1 つのオブジェクト変数の代入するか、またはオブジェクト変数をプロシージャに渡す参照ポインターのみがコピーされます。  
  
-   **Nothing を代入します。** 値を割り当てることができます[Nothing](../../../../visual-basic/language-reference/nothing.md)変数がインスタンスで、変数に関連する継続構造体。 メソッドを呼び出すし、可変要素が、代入によって再初期化されますが、そのデータ要素にアクセスすることができますも。  
  
     オブジェクト変数を設定した場合とは異なり、 `Nothing`、任意のクラスのインスタンスから関連付けを解除し、別のインスタンスを割り当てるまで、変数をメンバーにアクセスすることはできません。  
  
-   **複数のインスタンス。** オブジェクト変数が、異なるタイミングに、それに割り当てられている別のクラス インスタンスを持つことができ、いくつかのオブジェクト変数が同時に、同じクラスのインスタンスを参照できます。 クラス メンバーの値に加えた変更は、同じインスタンスを指す別の変数を使用してアクセスするときにそのメンバーに影響します。  
  
     ただし、構造体の要素は、独自のインスタンス内で分離されます。 他の同じインスタンスであっても、別の構造体変数にその値への変更は反映されません`Structure`宣言します。  
  
-   **等しいかどうか。** 2 つの構造の等価テストは、要素ごとのテストを実行する必要があります。 使用して 2 つのオブジェクト変数を比較することができます、<xref:System.Object.Equals%2A>メソッド。 <xref:System.Object.Equals%2A> 2 つの変数を指す同じインスタンスかどうかを示します。  
  
## <a name="see-also"></a>関連項目

- [データの種類](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [複合データ型](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [構造体](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [トラブルシューティング (データ型)](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [構造体とその他のプログラミング要素](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [クラスとオブジェクト](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
