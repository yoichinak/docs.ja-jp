---
title: オーバーロードの解決法 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- overload resolution
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedure overloading [Visual Basic], overload resolution
- signatures [Visual Basic], procedure
- overloads [Visual Basic], resolution
ms.assetid: 766115d1-4352-45fb-859f-6063e0de0ec0
ms.openlocfilehash: 4f81c7377423899c142c4270f325bbd7ed20b877
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59312242"
---
# <a name="overload-resolution-visual-basic"></a>オーバーロードの解決法 (Visual Basic)
Visual Basic コンパイラには、いくつかのオーバー ロードされたバージョンで定義されているプロシージャへの呼び出しが検出されると、コンパイラは、オーバー ロードを呼び出すを決める必要があります。 これは、次の手順を実行しています。  
  
1. **アクセシビリティ。** 呼び出し元のコードの呼び出しを防止するアクセス レベルを持つオーバー ロードを排除します。  
  
2. **パラメーターの数。** 呼び出しでは指定された数と異なる数のパラメーターが定義されているオーバー ロードを除外します。  
  
3. **パラメーターのデータ型。** コンパイラは、拡張メソッドよりインスタンス メソッドの優先を使用します。 拡大に合わせてプロシージャの呼び出しの変換のみを必要とする任意のインスタンス メソッドが見つかった場合は、すべての拡張メソッドは削除され、インスタンス メソッドの候補をコンパイラが続行されます。 このようなインスタンス メソッドが見つからない場合は、インスタンスと拡張メソッドの両方を続行します。  
  
     この手順で、オーバー ロードで定義されているパラメーターの型に呼び出し元の引数のデータ型を変換できませんオーバー ロードを除外します。  
  
4. **縮小変換をします。** 呼び出し元の引数の型から定義されたパラメーターの型への縮小変換を必要なオーバー ロードを除外します。 型チェックを切り替えるかどうかこれが true ([Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) は`On`または`Off`します。  
  
5. **最小の拡大します。** コンパイラは、ペアで残りのオーバー ロードを検討します。 各ペアに定義されているパラメーターのデータ型を比較します。 内のすべてのオーバー ロードのいずれかの型は、他の対応する型に拡大変換する場合、コンパイラは後者を除外します。 これは、最小限の拡大が必要なオーバー ロードを保持します。  
  
6. **1 つの候補。** オーバー ロードを 1 つだけまでのペアがそのまま残り、オーバー ロードし、そのオーバー ロードの呼び出しを解決することを検討して続行します。 コンパイラは、オーバー ロードを 1 つの候補を減らすことができない、エラーが生成されます。  
  
 次の図は、一連の呼び出しのオーバー ロードされたバージョンを決定するプロセスを示します。  
  
 ![オーバー ロードの解決プロセスのフロー ダイアグラム](./media/overload-resolution/determine-overloaded-version.gif "オーバー ロードされたバージョンを解決します。")    
  
 次の例では、このオーバー ロード解決プロセスを示します。  
  
 [!code-vb[VbVbcnProcedures#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#62)]  
  
 [!code-vb[VbVbcnProcedures#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#63)]  
  
 ため、最初の呼び出しで、コンパイラが最初のオーバー ロードを排除最初の引数の型 (`Short`) と対応するパラメーターの型へ縮小変換 (`Byte`)。 次に除去 3 番目のオーバー ロードは、2 番目のオーバー ロードに各引数を入力 (`Short`と`Single`) 3 番目のオーバー ロードでは、対応する型に拡大変換されます (`Integer`と`Single`)。 2 番目のオーバー ロードが必要な拡大が少ないので、コンパイラは、呼び出しの使用します。  
  
 2 番目の呼び出しでは、コンパイラは縮小に基づいてオーバー ロードのいずれかを取り除くことはできません。 以下の引数の型の拡大と 2 番目のオーバー ロードを呼び出すことができますので、同じ理由で最初の呼び出しのように、3 番目のオーバー ロードを除外します。 ただし、コンパイラは、最初と 2 番目のオーバー ロードの解決できません。 それぞれが、それ以外の対応する型を拡張する 1 つの定義されているパラメーターの型 (`Byte`に`Short`が`Single`に`Double`)。 そのため、コンパイラは、オーバー ロードの解決エラーを生成します。  
  
## <a name="overloaded-optional-and-paramarray-arguments"></a>省略可能なオーバー ロードと ParamArray 引数  
 最後のパラメーターを宣言する点を除いて、プロシージャの 2 つのオーバー ロードが同じシグネチャを持つ場合[(省略可能)](../../../../visual-basic/language-reference/modifiers/optional.md)で 1 つと[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)コンパイラとしてそのプロシージャの呼び出しを解決して、その他次に示します。  
  
|場合は、呼び出しとして最後の引数が指定されています|コンパイラは最後の引数として宣言するオーバー ロードの呼び出しを解決します。|  
|---|---|  
|値 (引数を省略) ではありません。|`Optional`|  
|1 つの値|`Optional`|  
|コンマ区切りの一覧で、2 つ以上の値|`ParamArray`|  
|(空の配列を含む) 任意の長さの配列|`ParamArray`|  
  
## <a name="see-also"></a>関連項目

- [省略可能なパラメーター](./optional-parameters.md)
- [パラメーター配列](./parameter-arrays.md)
- [プロシージャのオーバーロード](./procedure-overloading.md)
- [プロシージャのトラブルシューティング](./troubleshooting-procedures.md)
- [方法: 複数のバージョンのプロシージャを定義します。](./how-to-define-multiple-versions-of-a-procedure.md)
- [方法: オーバー ロードされたプロシージャを呼び出す](./how-to-call-an-overloaded-procedure.md)
- [方法: 省略可能なパラメーターを受け取るプロシージャをオーバー ロードします。](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [方法: 不特定数のパラメーターを受け取るプロシージャをオーバー ロードします。](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [プロシージャのオーバーロードに関する注意事項](./considerations-in-overloading-procedures.md)
- [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [拡張メソッド](./extension-methods.md)
