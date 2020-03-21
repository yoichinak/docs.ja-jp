---
title: Overload Resolution
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
ms.openlocfilehash: 84d52bbbfb34c2e5d67ed6a1810ab3e32fafda22
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266873"
---
# <a name="overload-resolution-visual-basic"></a>オーバーロードの解決法 (Visual Basic)
Visual Basic コンパイラが、オーバーロードされた複数のバージョンで定義されているプロシージャの呼び出しを検出した場合、コンパイラは、呼び出すオーバーロードのどれを決定する必要があります。 これは、次の手順を実行して行います。  
  
1. **アクセシビリティ。** 呼び出し元のコードが呼び出しを妨げるアクセス レベルを持つオーバーロードを排除します。  
  
2. **パラメーターの数。** 呼び出しで指定されたパラメーター数とは異なる数のパラメーターを定義するオーバーロードを排除します。  
  
3. **パラメーター データ型。** コンパイラは、拡張メソッドよりもインスタンス メソッドの優先を提供します。 プロシージャ呼び出しに一致するために拡大変換のみを必要とするインスタンス メソッドが見つかった場合、すべての拡張メソッドは削除され、コンパイラはインスタンス メソッドの候補のみを使用して続行されます。 そのようなインスタンス メソッドが見つからない場合は、インスタンス メソッドと拡張メソッドの両方を使用して続行されます。  
  
     この手順では、呼び出し元の引数のデータ型を、オーバーロードで定義されたパラメーター型に変換できないオーバーロードを排除します。  
  
4. **縮小変換。** 呼び出し元の引数型から定義済みのパラメーター型への縮小変換を必要とするオーバーロードを排除します。 これは、型チェック スイッチ ([オプション Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)ステートメント`On` `Off`) が .  
  
5. **最も広く表示されます。** コンパイラは、残りのオーバーロードをペアで考慮します。 各ペアについて、定義されたパラメータのデータ型を比較します。 オーバーロードの一方の型が、他のオーバーロードの対応する型にすべて拡大された場合、コンパイラは後者を削除します。 つまり、最小限の拡大を必要とするオーバーロードを保持します。  
  
6. **単一の候補。** 1 つのオーバーロードだけが残るまで、ペアでのオーバーロードの検討を続行し、そのオーバーロードへの呼び出しを解決します。 コンパイラがオーバーロードを 1 つの候補に減らすことができない場合は、エラーが生成されます。  
  
 次の図は、オーバーロードされたバージョンのセットのうちどれを呼び出すかを決定するプロセスを示しています。  
  
 ![オーバーロードの解決プロセスのフロー ダイアグラム](./media/overload-resolution/determine-overloaded-version.gif "オーバーロードされたバージョン間の解決")
  
 このオーバーロード解決プロセスの例を次に示します。  
  
 [!code-vb[VbVbcnProcedures#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#62)]  
  
 [!code-vb[VbVbcnProcedures#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#63)]  
  
 最初の呼び出しでは、最初の引数 ( ) の型が対応`Short`するパラメーター ( )`Byte`の型に絞り込まれるため、コンパイラは最初のオーバーロードを削除します。 次に、2 番目のオーバーロード ( と ) の`Short`各`Single`引数型が 3 番目のオーバーロード (`Integer`と`Single`) の対応する型に広がるため、3 番目のオーバーロードが削除されます。 2 番目のオーバーロードは、必要な拡大が少ないので、コンパイラは呼び出しに使用します。  
  
 2 番目の呼び出しでは、コンパイラは、狭くすることに基づいてオーバーロードを削除できません。 これは、引数型の拡大を減らして 2 番目のオーバーロードを呼び出すことができるため、最初の呼び出しと同じ理由で 3 番目のオーバーロードを排除します。 ただし、コンパイラは、最初と 2 番目のオーバーロードの間で解決できません。 各パラメーター`Byte`型には、もう一方の型 ( から ) に`Short`対応する`Single`型`Double`に拡大されるパラメータ型が定義されています。 そのため、コンパイラはオーバーロード解決エラーを生成します。  
  
## <a name="overloaded-optional-and-paramarray-arguments"></a>オーバーロードされたオプション引数と ParamArray 引数  
 プロシージャの 2 つのオーバーロードに同じシグネチャがある場合、最後のパラメーターが一方で[Optional、](../../../../visual-basic/language-reference/modifiers/optional.md)もう一方のパラメータが[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)として宣言されている以外は、コンパイラは次のようにそのプロシージャの呼び出しを解決します。  
  
|呼び出しが最後の引数を次のように指定した場合|コンパイラは、最後の引数を次のように宣言するオーバーロードへの呼び出しを解決します。|  
|---|---|  
|値なし (引数は省略)|`Optional`|  
|単一の値|`Optional`|  
|コンマ区切りリスト内の 2 つ以上の値|`ParamArray`|  
|任意の長さの配列 (空の配列を含む)|`ParamArray`|  
  
## <a name="see-also"></a>関連項目

- [オプションのパラメータ](./optional-parameters.md)
- [パラメータ配列](./parameter-arrays.md)
- [プロシージャのオーバーロード](./procedure-overloading.md)
- [プロシージャのトラブルシューティング](./troubleshooting-procedures.md)
- [方法 : プロシージャの複数のバージョンを定義する](./how-to-define-multiple-versions-of-a-procedure.md)
- [方法 : オーバーロードされたプロシージャを呼び出す](./how-to-call-an-overloaded-procedure.md)
- [方法 : 省略可能なパラメーターを受け取るプロシージャをオーバーロードする](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [方法 : 不特定数のパラメーターを受け取るプロシージャをオーバーロードする](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [プロシージャのオーバーロードに関する注意事項](./considerations-in-overloading-procedures.md)
- [オーバー ロード](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [拡張メソッド](./extension-methods.md)
