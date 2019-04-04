---
title: '方法: 不特定数のパラメーター (Visual Basic) を受け取るプロシージャをオーバー ロードします。'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], indefinite number of parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: c7042de2-2422-4039-94e8-ac298896af69
ms.openlocfilehash: bae420e88a74fbe3f7e8ad3592133fdcaf191029
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838996"
---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a>方法: 不特定数のパラメーター (Visual Basic) を受け取るプロシージャをオーバー ロードします。
プロシージャがある場合、 [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)パラメーター、パラメーター配列の 1 次元配列を取得するオーバー ロードされたバージョンを定義することはできません。 詳細については、「暗黙的なオーバー ロードを ParamArray パラメーター」を参照してください[プロシージャのオーバー ロードに関する考慮事項](./considerations-in-overloading-procedures.md)します。  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a>可変個のパラメーターを受け取るプロシージャをオーバー ロードするには  
  
1.  プロシージャは、コード ロジックのメリットを呼び出すことがから複数のバージョンのオーバー ロードされたことを確認、`ParamArray`パラメーター。 「オーバー ロードと Paramarray」を参照してください[プロシージャのオーバー ロードに関する考慮事項](./considerations-in-overloading-procedures.md)します。  
  
2.  パラメーター リストの可変部分で、プロシージャが受け取る指定された値の数を決定します。 これは、値はありませんの大文字と小文字が含まれます、1 つの 1 次元配列の大文字と小文字を含めることができます。  
  
3.  指定された値の許容数はそれぞれ、書き込み、`Sub`または`Function`宣言ステートメントを対応するパラメーター リストを定義します。 使用しないで、`Optional`または`ParamArray`このオーバー ロードされたバージョンのキーワード。  
  
4.  各宣言の前に、`Sub`または`Function`キーワード、[オーバー ロード](../../../../visual-basic/language-reference/modifiers/overloads.md)キーワード。  
  
5.  次の各宣言には、呼び出し元のコードは、宣言のパラメーター リストに対応する値を指定すると実行されるプロシージャ コードを記述します。  
  
6.  各プロシージャの終了、`End Sub`または`End Function`に応じてステートメント。  
  
## <a name="example"></a>例  
 次の例で定義されている手順を示しています、 [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)パラメーターとし、同等の一連のオーバー ロードされたプロシージャ。  
  
 [!code-vb[VbVbcnProcedures#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#69)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 パラメーター配列の 1 次元配列を受け取るパラメーター リストで、このようなプロシージャをオーバー ロードすることはできません。 ただし、他の暗黙的なオーバー ロードのシグネチャを使用することができます。 次の宣言では、これについて説明します。  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
 オーバー ロードされたバージョンのコードは呼び出し元のコードの 1 つまたは複数の値を指定するかどうかをテストする必要はありません、`ParamArray`パラメーター、そうである場合、または数。 Visual Basic では、呼び出し元の引数リストに一致するバージョンに制御を渡します。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 ため、使用するプロシージャを`ParamArray`パラメーターは、一連のオーバー ロードされたバージョンに、これらの暗黙的なオーバー ロードのいずれかに対応するパラメーター リストで、このようなプロシージャをオーバー ロードすることはできません。 詳細については、[プロシージャのオーバー ロードに関する考慮事項](./considerations-in-overloading-procedures.md)を参照してください。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 無限に増大することができる配列を処理するたびに、アプリケーションの内部の容量を超過してしまう可能性があります。 パラメーター配列を受け取る場合は、呼び出し元のコードは、渡された配列の長さをテストし、がアプリケーションには大きすぎる場合は、適切な手順を実行する必要があります。  
  
## <a name="see-also"></a>関連項目

- [プロシージャ](./index.md)
- [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)
- [省略可能なパラメーター](./optional-parameters.md)
- [パラメーター配列](./parameter-arrays.md)
- [プロシージャのオーバーロード](./procedure-overloading.md)
- [プロシージャのトラブルシューティング](./troubleshooting-procedures.md)
- [方法: 複数のバージョンのプロシージャを定義します。](./how-to-define-multiple-versions-of-a-procedure.md)
- [方法: オーバー ロードされたプロシージャを呼び出す](./how-to-call-an-overloaded-procedure.md)
- [方法: 省略可能なパラメーターを受け取るプロシージャをオーバー ロードします。](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [オーバーロードの解決](./overload-resolution.md)
