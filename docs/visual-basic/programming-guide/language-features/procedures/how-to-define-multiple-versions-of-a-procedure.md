---
title: '方法: 複数のバージョン (Visual Basic)、プロシージャの定義します。'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- procedure overloading [Visual Basic], multiple versions
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
ms.openlocfilehash: fc7a8e18394b904f0c22a80f71dee091d4f786ab
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61863832"
---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a>方法: 複数のバージョン (Visual Basic)、プロシージャの定義します。
プロシージャを定義するには、複数のバージョンで*オーバー ロード*バージョンごとに同じ名前が別のパラメーター リストを使用しています。 オーバー ロードの目的では、名前で区別せずに密接に関連するいくつかのバージョンのプロシージャを定義します。  
  
 詳細については、プロシージャのオーバーロード (Visual Basic)[に関するページを参照してください。  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a>プロシージャの複数のバージョンを定義するには  
  
1. 書き込みを`Sub`または`Function`を定義する手順の各バージョンの宣言ステートメントです。 すべての宣言で同じプロシージャ名を使用します。  
  
2. 前に、`Sub`または`Function`各宣言キーワード、[オーバー ロード](../../../../visual-basic/language-reference/modifiers/overloads.md)キーワード。 必要に応じて省略できます`Overloads`宣言のいずれかに含める場合は、宣言する必要がありますに追加するすべての宣言。  
  
3. 次の各宣言ステートメントには、呼び出し元のコードがそのバージョンのパラメーター リストに一致する引数を提供する特定のケースを処理するプロシージャのコードを記述します。 必要はありませんをテストするパラメーターの呼び出し元のコードが提供されています。 Visual Basic では、プロシージャの対応するバージョンに制御を渡します。  
  
4. プロシージャの各バージョンの終了、`End Sub`または`End Function`に応じてステートメント。  
  
## <a name="example"></a>例  
 次の例では、定義、`Sub`顧客の残高に対してトランザクションをポストするプロシージャ。 使用して、`Overloads`キーワードを名前と、その他のアカウント番号での顧客を受け取ると、プロシージャの 2 つのバージョンを定義します。  
  
 [!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]  
  
 呼び出し元のコードは、いずれか、顧客 id を取得できます、`String`または`Integer`、いずれの場合も同じステートメントの呼び出しを使用します。  
  
 これらのバージョンを呼び出す方法については、`post`の手順を参照してください[方法。オーバー ロードされたプロシージャを呼び出す](./how-to-call-an-overloaded-procedure.md)します。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 プロシージャ名が同じで別のパラメーター リストを持つ、オーバー ロードされたバージョンを確認します。  
  
## <a name="see-also"></a>関連項目

- [プロシージャ](./index.md)
- [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)
- [プロシージャのトラブルシューティング](./troubleshooting-procedures.md)
- [方法: 省略可能なパラメーターを受け取るプロシージャをオーバー ロードします。](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [方法: 不特定数のパラメーターを受け取るプロシージャをオーバー ロードします。](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [プロシージャのオーバーロードに関する注意事項](./considerations-in-overloading-procedures.md)
- [オーバーロードの解決](./overload-resolution.md)
