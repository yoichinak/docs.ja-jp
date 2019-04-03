---
title: 引数の値渡しと参照渡し (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- ByRef keyword [Visual Basic], passing arguments by reference
- Visual Basic code, procedures
- passing arguments [Visual Basic], by value or by reference
- ByVal keyword [Visual Basic], passing arguments by value
- arguments [Visual Basic], passing by value or by reference
- argument passing [Visual Basic], by value or by reference
ms.assetid: fd8a9de6-7178-44d5-a9bf-458d4ad907c2
ms.openlocfilehash: c23ca51322f57dc13a85c3ea94e0d335dc50ca13
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58830358"
---
# <a name="passing-arguments-by-value-and-by-reference-visual-basic"></a>引数の値渡しと参照渡し (Visual Basic)
Visual basic では、プロシージャに引数を渡すことができます*値によって*または*参照によって*します。 呼ばれます、*渡し*、し、プロシージャが呼び出し元のコードで引数を基になるプログラミングの要素を変更できるかどうかを決定します。 プロシージャ宣言では、各パラメーターの引き渡し方法を決定を指定して、 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)または[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)キーワード。  
  
## <a name="distinctions"></a>違いがあります。  
 プロシージャに引数を渡すときは、相互作用をいくつかの違いに注意してください。  
  
-   基になるプログラミング要素が変更可能または変更不可能なのかどうか  
  
-   引数自体が変更可能または変更不可能なのかどうか  
  
-   値渡しまたは参照によって引数が渡されるかどうか  
  
-   引数のデータ型は、値型または参照型かどうか  
  
 詳細については、次を参照してください。[変更の間の相違点と変更できない引数](./differences-between-modifiable-and-nonmodifiable-arguments.md)と[の相違点の間の値と参照渡しによって引数を渡す](./differences-between-passing-an-argument-by-value-and-by-reference.md)します。  
  
## <a name="choice-of-passing-mechanism"></a>渡す機能の選択  
 慎重に各引数の引き渡し方法を選択する必要があります。  
  
-   **保護**します。 2 つの引数を渡す方法の選択、最も重要な条件を変更する変数を呼び出すことのリスクは。 引数を渡すことの利点は、`ByRef`プロシージャがその引数から呼び出し元コードに値を返すことができます。 引数を渡すことの利点は、`ByVal`からプロシージャによって変更されている変数を防ぐことができます。  
  
-   **パフォーマンス**します。 引き渡し方法が、コードのパフォーマンスに影響を与えることができますが、違いは通常の意味ではありません。 1 つの例外は渡された値型`ByVal`します。 この場合は、Visual Basic では、引数のデータ全体の内容をコピーします。 そのため、構造体などの大きな値型はなりますに渡すより効率的な`ByRef`します。  
  
     参照型でデータへのポインターにのみ、コピー (4 バイト、64 ビット プラットフォームでは 8 バイトである 32 ビット プラットフォームで) です。 そのため、型の引数を渡すことができます`String`または`Object`パフォーマンスを損なわずに値渡し。  
  
## <a name="determination-of-the-passing-mechanism"></a>引数渡しの方法の決定  
 プロシージャ宣言では、各パラメーターの引き渡し方法を指定します。 呼び出し元のコードがオーバーライドすることはできません、`ByVal`メカニズム。  
  
 パラメーターが宣言されている場合`ByRef`、呼び出し元のコードにするためのメカニズムを強制できます`ByVal`で引数名を呼び出しにかっこで囲みます。 詳細については、「[方法 :引数の値渡しを強制](./how-to-force-an-argument-to-be-passed-by-value.md)します。  
  
 Visual Basic では既定では、引数を値渡しです。  
  
## <a name="when-to-pass-an-argument-by-value"></a>引数を値渡しする場合  
  
-   呼び出し元に、引数の基になるコード要素が変更不可能な要素の場合は、対応するパラメーターを宣言[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)します。 変更不可能な要素の値は、コードでは変更ありません。  
  
-   基になる要素は変更できますが、その値を変更できるプロシージャしたくない場合、パラメーターを宣言`ByVal`します。 呼び出し元のコードだけでは、値渡し変更可能な要素の値を変更できます。  
  
## <a name="when-to-pass-an-argument-by-reference"></a>参照渡しで引数を渡す場合  
  
-   プロシージャの呼び出し元のコードで基になる要素を変更する必要が本当にある場合は、対応するパラメーターを宣言[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)します。  
  
-   コードの適切な実行は、呼び出し元のコード内の基になる要素を変更するプロシージャに依存している場合は、パラメーターを宣言`ByRef`します。 値を値によって渡す場合、または呼び出し元のコードをオーバーライドする場合、`ByRef`メカニズムの引数をかっこで囲んでを渡し、プロシージャの呼び出しが予期しない結果を生じる可能性があります。  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 次の例は、引数を値渡しする場合と参照渡しする場合を示しています。 プロシージャ`Calculate`両方を持つ、`ByVal`と`ByRef`パラメーター。 利率を指定された`rate`との合計金額、`debt`の新しい値を計算するが、プロシージャのタスク`debt`の元の値を利率を適用した結果である`debt`します。 `debt`は、`ByRef`パラメーターに対応する呼び出し元のコードで引数の値に、新しい合計が反映されます`debt`します。 パラメーター`rate`は、`ByVal`パラメーターのため`Calculate`その値を変更しないでください。  
  
### <a name="code"></a>コード  
 [!code-vb[VbVbcnProcedures#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class2.vb#74)]  
  
## <a name="see-also"></a>関連項目

- [プロシージャ](./index.md)
- [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)
- [方法: プロシージャに引数を渡す](./how-to-pass-arguments-to-a-procedure.md)
- [方法: プロシージャ引数の値を変更します。](./how-to-change-the-value-of-a-procedure-argument.md)
- [方法: プロシージャ引数の値が変化しません。](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [方法: 引数の値渡しを強制します。](./how-to-force-an-argument-to-be-passed-by-value.md)
- [位置と名前による引数渡し](./passing-arguments-by-position-and-by-name.md)
- [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
