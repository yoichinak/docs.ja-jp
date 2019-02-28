---
title: プロシージャのオーバーロードに関する注意事項 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- signatures [Visual Basic], ParamArray arguments
- ParamArray keyword [Visual Basic], parameter arrays
- ParamArray keyword [Visual Basic], arguments and signatures
- function overloading [Visual Basic], implicit overloads for ParamArray
- ParamArray keyword [Visual Basic], signatures
- Visual Basic code, procedures
- arguments [Visual Basic], parameter arrays
- procedures [Visual Basic], overloading
- parameters [Visual Basic], lists
- function overloading [Visual Basic], typeless programming
- typeless programming
- function overloading [Visual Basic], restrictions
- arguments [Visual Basic], optional
- optional arguments [Visual Basic], overloading
- signatures [Visual Basic], procedure
- parameter lists [Visual Basic]
- parameter arrays [Visual Basic], overloading arguments
- Visual Basic code, parameter lists
- procedure overloading [Visual Basic], considerations
- Option Explicit statement [Visual Basic]
- restrictions [Visual Basic], overloading procedures
- procedures [Visual Basic], parameter lists
ms.assetid: a2001248-10d0-42c5-b0ce-eeedc987319f
ms.openlocfilehash: 8dfee8a8678fb00fcded4b7da57c3b200ef64d69
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979537"
---
# <a name="considerations-in-overloading-procedures-visual-basic"></a>プロシージャのオーバーロードに関する注意事項 (Visual Basic)
異なるを使用する必要がありますプロシージャをオーバー ロードするときに*署名*各オーバー ロードされたバージョン。 通常、つまり、各バージョンは、別のパラメーター リストを指定する必要があります。 詳細については、「別の署名」を参照してください[プロシージャのオーバー ロード](./procedure-overloading.md)します。  
  
 オーバー ロードすることができます、`Function`プロシージャを`Sub`プロシージャ、およびその逆の場合は、異なるシグネチャを持つ、提供されています。 2 つのオーバー ロードできませんのみが異なります戻り値を持つ 1 つと、もう一方はありません。  
  
 同様に、プロシージャをオーバー ロードするプロパティがオーバー ロードでき、同じ制限があります。 ただし、プロシージャをオーバー ロードすることはできません、プロパティ、またはその逆です。  
  
## <a name="alternatives-to-overloaded-versions"></a>オーバー ロードされたバージョンの代替手段  
 引数のかどうかはオプションや、その数が可変際などにオーバー ロードされたバージョンは、選択肢場合がありますがあります。  
  
 省略可能な引数が必ずしもすべての言語でサポートされていませんし、パラメーター配列は Visual Basic に制限されます。 ことに注意してください。 複数の異なる言語のいずれかで記述されたコードから呼び出される可能性のあるプロシージャを作成する場合は、バージョン プラン最大限の柔軟性をオーバー ロード。  
  
### <a name="overloads-and-optional-arguments"></a>省略可能な引数とオーバー ロード  
 呼び出し元のコードの指定または 1 つまたは複数の引数を省略できます必要に応じて、複数のオーバー ロードされたバージョンを定義または省略可能なパラメーターを使用できます。  
  
#### <a name="when-to-use-overloaded-versions"></a>オーバー ロードされたバージョンを使用する場合  
 次の場合に、一連のオーバー ロードされたバージョンを定義することもできます。  
  
-   プロシージャ コード内のロジックは、呼び出し元のコードが、省略可能な引数を提供するかどうかどうかによって大きく異なります。  
  
-   プロシージャのコードは、呼び出し元のコードには、省略可能な引数が提供されているかどうかを確実にテストできません。 これは、場合など、既定値の値を可能性のある候補がない場合、呼び出し元コードでしたを期待できませんを指定します。  
  
#### <a name="when-to-use-optional-parameters"></a>省略可能なパラメーターを使用する場合  
 次の場合に 1 つまたは複数の省略可能なパラメーターをお勧めします。  
  
-   呼び出し元のコードは省略可能な引数を指定していない場合にのみ必要な操作では、既定値にパラメーターを設定します。 このような場合は、プロシージャのコードは複雑になる小さい場合は 1 つまたは複数の 1 つのバージョンを定義する`Optional`パラメーター。  
  
 詳細については、次を参照してください。[省略可能なパラメーター](./optional-parameters.md)します。  
  
### <a name="overloads-and-paramarrays"></a>Paramarray とオーバー ロード  
 呼び出し元のコードは、可変個の引数を渡すことのできる場合は、複数のオーバー ロードされたバージョンを定義またはパラメーター配列を使用できます。  
  
#### <a name="when-to-use-overloaded-versions"></a>オーバー ロードされたバージョンを使用する場合  
 次の場合に、一連のオーバー ロードされたバージョンを定義することもできます。  
  
-   呼び出し元コードことはありませんを渡している複数の値の数が少ないパラメーター配列にわかります。  
  
-   プロシージャ コード内のロジックは、呼び出し元のコードに渡す値の数によって大きく異なります。  
  
-   呼び出し元のコードでは、異なるデータ型の値を渡すことができます。  
  
#### <a name="when-to-use-a-parameter-array"></a>パラメーター配列を使用する場合  
 充実した、`ParamArray`パラメーターは、次の場合。  
  
-   呼び出し元のコードは、パラメーター配列に渡すことができます数の値を予測できないし、数が多い可能性があります。  
  
-   プロシージャのロジックは、呼び出し元のコードを渡すと、すべての値に対して基本的に同じ操作を実行するすべての値を反復処理に適しています。  
  
 詳細については、次を参照してください。[パラメーター配列](./parameter-arrays.md)します。  
  
## <a name="implicit-overloads-for-optional-parameters"></a>省略可能なパラメーターの暗黙のオーバー ロード  
 使用するプロシージャを[(省略可能)](../../../../visual-basic/language-reference/modifiers/optional.md)パラメータは、1 つは省略可能なパラメーター、これがない 1 つの 2 つのオーバー ロードされたプロシージャに相当します。 これらのいずれかに対応するパラメーター リストで、このようなプロシージャをオーバー ロードすることはできません。 次の宣言では、これについて説明します。  
  
 [!code-vb[VbVbcnProcedures#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#58)]  
  
 [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
 [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
 省略可能なパラメーターを 1 つ以上のプロシージャ、前の例と同様のロジックによって、暗黙のオーバー ロードのセットがあります。  
  
## <a name="implicit-overloads-for-a-paramarray-parameter"></a>ParamArray パラメーターの暗黙のオーバー ロード  
 コンパイラは、使用するプロシージャを[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)無限でどのような呼び出し元のコードに渡すパラメーター配列では、次のように異なる他のオーバー ロードが存在するパラメーター。  
  
-   1 つのオーバー ロードの呼び出し元のコードでは引数に指定されていない場合、 `ParamArray`  
  
-   1 つのオーバー ロードの 1 次元配列を呼び出し元のコードが提供するときに、`ParamArray`要素の型  
  
-   すべての正の整数のいずれかのオーバー ロードの呼び出し元のコードは、それぞれの引数の数を指定すると、`ParamArray`要素の型  
  
 次の宣言では、これらの暗黙的なオーバー ロードを示しています。  
  
 [!code-vb[VbVbcnProcedures#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#68)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 パラメーター配列の 1 次元配列を受け取るパラメーター リストで、このようなプロシージャをオーバー ロードすることはできません。 ただし、他の暗黙的なオーバー ロードのシグネチャを使用することができます。 次の宣言では、これについて説明します。  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
## <a name="typeless-programming-as-an-alternative-to-overloading"></a>代わりにオーバー ロードを省略したプログラミング  
 パラメーターに異なるデータ型を渡すには、呼び出し元のコードを許可する場合を省略したプログラミングは、別のアプローチです。 型チェックをスイッチを設定する`Off`いずれかで、 [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)または[/optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md)コンパイラ オプション。 パラメーターのデータ型を宣言する必要はありません。 ただし、このアプローチでは、オーバー ロードと比較して次の欠点があります。  
  
-   省略したプログラミングでは、それほど効率的での実行コードを生成します。  
  
-   プロシージャは、渡されると予想されるすべてのデータ型をテストする必要があります。  
  
-   呼び出し元のコードが、プロシージャがサポートされていないデータ型を渡すかどうか、コンパイラでエラーが生成されません。  
  
## <a name="see-also"></a>関連項目
- [プロシージャ](./index.md)
- [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)
- [プロシージャのトラブルシューティング](./troubleshooting-procedures.md)
- [方法: 複数のバージョンのプロシージャを定義します。](./how-to-define-multiple-versions-of-a-procedure.md)
- [方法: オーバー ロードされたプロシージャを呼び出す](./how-to-call-an-overloaded-procedure.md)
- [方法: 省略可能なパラメーターを受け取るプロシージャをオーバー ロードします。](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [方法: 不特定数のパラメーターを受け取るプロシージャをオーバー ロードします。](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [オーバーロードの解決](./overload-resolution.md)
- [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)
