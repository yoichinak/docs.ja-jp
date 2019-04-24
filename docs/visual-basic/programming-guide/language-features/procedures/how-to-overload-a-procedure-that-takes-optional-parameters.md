---
title: '方法: 省略可能なパラメーター (Visual Basic) を受け取るプロシージャをオーバー ロードします。'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], optional parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: 825f9d56-4cde-43fd-993a-b9171717e2eb
ms.openlocfilehash: 58c52a7d73efbd96d772dd85d6bf2c9084fb1241
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59320231"
---
# <a name="how-to-overload-a-procedure-that-takes-optional-parameters-visual-basic"></a>方法: 省略可能なパラメーター (Visual Basic) を受け取るプロシージャをオーバー ロードします。
プロシージャが 1 つまたは複数場合[(省略可能)](../../../../visual-basic/language-reference/modifiers/optional.md)パラメーターの暗黙のオーバー ロードのいずれかに一致するオーバー ロードされたバージョンを定義することはできません。 詳細については、"暗黙的なオーバー ロードの省略可能なパラメーター"を参照してください[プロシージャのオーバー ロードに関する考慮事項](./considerations-in-overloading-procedures.md)します。  
  
## <a name="one-optional-parameter"></a>1 つの省略可能なパラメーター  
  
#### <a name="to-overload-a-procedure-that-takes-one-optional-parameter"></a>1 つの省略可能なパラメーターを受け取るプロシージャをオーバー ロードするには  
  
1. 書き込みを`Sub`または`Function`宣言ステートメントをパラメーター リストで省略可能なパラメーターが含まれています。 使用しないでください、`Optional`このオーバー ロードされたバージョンのキーワード。  
  
2. 前に、`Sub`または`Function`キーワード、[オーバー ロード](../../../../visual-basic/language-reference/modifiers/overloads.md)キーワード。  
  
3. 呼び出し元のコードは省略可能な引数を指定すると実行されるプロシージャ コードを記述します。  
  
4. プロシージャの終了、`End Sub`または`End Function`に応じてステートメント。  
  
5. パラメーター リストで省略可能なパラメーターは含まれませんが、最初の宣言と同じである 2 番目の宣言ステートメントを記述します。  
  
6. 呼び出し元のコードは省略可能な引数を指定しない場合に実行するプロシージャのコードを記述します。 プロシージャの終了、`End Sub`または`End Function`に応じてステートメント。  
  
     次の例では、2 つのオーバー ロードされたプロシージャと、最後に有効と無効なオーバー ロードされたバージョンの例の等価セット オプションのパラメーターで定義されている手順を示します。  
  
     [!code-vb[VbVbcnProcedures#59](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#59)]  
  
     [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
     [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
## <a name="multiple-optional-parameters"></a>複数の省略可能なパラメーター  
 省略可能なパラメーターを 1 つ以上のプロシージャでは、通常 2 つ以上のオーバー ロードされたバージョンを必要します。 たとえば、2 つの省略可能なパラメーターがあるで呼び出し元のコードを指定したり、他とは無関係にそれぞれを省略した場合は、指定された引数の組み合わせごとに 1 つずつ、4 つのオーバー ロードされたバージョン必要があります。  
  
 省略可能なパラメーターの数が多いほど、オーバー ロードの複雑さが増加します。 指定された引数のいくつかの組み合わせが許容されない場合を除き、N の省略可能なパラメーターの必要がある 2 ^ N のオーバー ロードされたバージョン。 、プロシージャの性質によっては、ロジックをわかりやすくするために、すべてのオーバー ロードされたバージョンを定義するという余分な作業によって正当化されることがあります。  
  
#### <a name="to-overload-a-procedure-that-takes-more-than-one-optional-parameter"></a>1 つ以上の省略可能なパラメーターを受け取るプロシージャをオーバー ロードするには  
  
1. プロシージャのロジックを指定できる省略可能な引数の組み合わせを決定します。 受け入れられない組み合わせは、別の 1 つの省略可能なパラメーターが依存している場合に発生する可能性です。 たとえば、1 つのパラメーターが配偶者の名前を受け入れ、配偶者の年齢を受け取る場合は、年齢が名前を省略すると、引数の組み合わせは許されません。  
  
2. 省略可能な引数の許容可能な組み合わせごとに、書き込み、`Sub`または`Function`宣言ステートメントを対応するパラメーター リストを定義します。 使用しないでください、`Optional`キーワード。  
  
3. 各宣言の前に、`Sub`または`Function`キーワード、[オーバー ロード](../../../../visual-basic/language-reference/modifiers/overloads.md)キーワード。  
  
4. 次の各宣言には、呼び出し元のコードは、宣言のパラメーター リストに対応する引数リストを提供する場合に実行するプロシージャ コードを記述します。  
  
5. 各プロシージャの終了、`End Sub`または`End Function`に応じてステートメント。  
  
## <a name="see-also"></a>関連項目

- [プロシージャ](./index.md)
- [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)
- [省略可能なパラメーター](./optional-parameters.md)
- [パラメーター配列](./parameter-arrays.md)
- [プロシージャのオーバーロード](./procedure-overloading.md)
- [プロシージャのトラブルシューティング](./troubleshooting-procedures.md)
- [方法: 複数のバージョンのプロシージャを定義します。](./how-to-define-multiple-versions-of-a-procedure.md)
- [方法: オーバー ロードされたプロシージャを呼び出す](./how-to-call-an-overloaded-procedure.md)
- [方法: 不特定数のパラメーターを受け取るプロシージャをオーバー ロードします。](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [オーバーロードの解決](./overload-resolution.md)
