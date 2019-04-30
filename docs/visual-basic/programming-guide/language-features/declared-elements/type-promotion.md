---
title: 型の上位変換 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- Partial keyword [Visual Basic], unexpected results with type promotion
- scope [Visual Basic], declared elements
- scope [Visual Basic], Visual Basic
- type promotion
- declared elements [Visual Basic], visibility
ms.assetid: 035eeb15-e4c5-4288-ab3c-6bd5d22f7051
ms.openlocfilehash: f7ac6bfb944da8bd50e035ba97b2b513176dc661
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973304"
---
# <a name="type-promotion-visual-basic"></a>型の上位変換 (Visual Basic)
モジュール内のプログラミング要素を宣言するときに、Visual Basic は、モジュールを含む名前空間には、そのスコープを昇格します。 これと呼ばれます*の上位変換*します。  
  
 次の例では、モジュールのスケルトン定義し、そのモジュールの 2 つのメンバーを示します。  
  
 [!code-vb[VbVbalrDeclaredElements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#1)]  
  
 内で`projModule`プログラミング、モジュール レベルで宣言された要素に昇格`projNamespace`します。 前の例では、`basicEnum`と`innerClass`昇格されますが、`numberSub`モジュール レベルで宣言されていないためは。  
  
## <a name="effect-of-type-promotion"></a>型の上位変換の効果  
 型の上位変換の効果は、修飾文字列が、モジュール名を含める必要がないことです。 次の例では、前の例では、プロシージャに 2 つの呼び出しをでいます。  
  
 [!code-vb[VbVbalrDeclaredElements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#2)]  
  
 前の例では、最初の呼び出しは、完全修飾文字列を使用します。 ただし、これは必要ありません型の上位変換のためです。 2 番目の呼び出しもアクセス モジュールのメンバーを含めずに`projModule`修飾文字列にします。  
  
## <a name="defeat-of-type-promotion"></a>型の上位変換の無効化  
 名前空間には、既にモジュール メンバーと同じ名前のメンバーが、型の上位変換は、モジュール メンバーの無効化します。 次の例では、列挙体と同じ名前空間内のモジュールのスケルトン定義を示します。  
  
 [!code-vb[VbVbalrDeclaredElements#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#3)]  
  
 Visual Basic では、前の例では、クラスに昇格できません`abc`に`thisNameSpace`名前空間レベルで同じ名前の列挙型が既に存在します。 アクセスする`abcSub`、完全修飾文字列を使用する必要があります`thisNamespace.thisModule.abc.abcSub`します。 ただし、クラス`xyz`はまだ昇格し、アクセスできる`xyzSub`短い修飾文字列`thisNamespace.xyz.xyzSub`します。  
  
### <a name="defeat-of-type-promotion-for-partial-types"></a>部分型の型の上位変換の無効化  
 クラスまたはモジュール内の構造体を使用している場合、[部分](../../../../visual-basic/language-reference/modifiers/partial.md)キーワード、型の上位変換は自動的に失敗のクラスまたは構造体、名前空間には、同じ名前のメンバーであるかどうか。 モジュールの他の要素は、型の上位変換も対象です。  
  
 **結果。** 部分定義の型の上位変換の無効化には、予期しない結果とコンパイラ エラーも可能性があります。 次の例では、モジュール内では、クラスのスケルトンの部分的な定義を示します。  
  
 [!code-vb[VbVbalrDeclaredElements#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#4)]  
  
 前の例では、開発者は、コンパイラの 2 つの部分定義をマージする`sampleClass`します。 ただし、コンパイラが部分定義内での昇格を考慮しない`sampleModule`します。 2 つの個別のクラスをコンパイルしようという名前をその結果、`sampleClass`がさまざまな認定パス。  
  
 コンパイラは、完全修飾されたパスがまったく同じ場合にのみ、部分定義をマージします。  
  
## <a name="recommendations"></a>推奨事項  
 次の推奨事項は、適切なプログラミング手法を表します。  
  
- **一意の名前。** プログラミング要素の名前付けに対するフル コントロールがある場合は常には一意の名前をすべての場所で使用します。 同じ名前では、余分な認定を必要し、によって、コードが読みにくくなります。 微妙なエラーと予期しない結果になることができますも。  
  
- **完全に修飾します。** モジュールと同じ名前空間の他の要素を使用して、最も安全なアプローチは常にすべてのプログラミング要素の完全修飾を使用するがします。 型の上位変換は、モジュール メンバーの無効化、そのメンバーを完全修飾しない場合は、誤って別のプログラミング要素にアクセスするでした。  
  
## <a name="see-also"></a>関連項目

- [Module ステートメント](../../../../visual-basic/language-reference/statements/module-statement.md)
- [Namespace ステートメント](../../../../visual-basic/language-reference/statements/namespace-statement.md)
- [Partial](../../../../visual-basic/language-reference/modifiers/partial.md)
- [Visual Basic におけるスコープ](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [方法: コントロール変数のスコープ](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)
- [宣言された要素の参照](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
