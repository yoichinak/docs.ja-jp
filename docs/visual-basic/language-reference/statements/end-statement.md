---
title: End ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.End
- End
helpviewer_keywords:
- execution [Visual Basic], ending
- files [Visual Basic], closing
- End keyword [Visual Basic], End statements
- programs [Visual Basic], quitting
- code, exiting
- program termination
- End statement [Visual Basic]
- execution [Visual Basic], stopping
ms.assetid: 0e64467c-0f34-4aab-9ddd-43f8b9d55d90
ms.openlocfilehash: 66dba1df125a08b8ae05519a0c66edb6da15ceaa
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583412"
---
# <a name="end-statement"></a>End ステートメント
直ちに実行を終了します。  
  
## <a name="syntax"></a>構文  
  
```vb  
End  
```  
  
## <a name="remarks"></a>Remarks  
 @No__t_0 ステートメントをプロシージャ内の任意の場所に配置して、アプリケーション全体の実行を強制的に停止することができます。 `End` `Open` ステートメントで開かれたすべてのファイルを閉じ、アプリケーションのすべての変数をクリアします。 オブジェクトへの参照を保持しているプログラムが他になく、そのコードも実行されていない場合、アプリケーションはすぐに終了します。  
  
> [!NOTE]
> @No__t_0 ステートメントは、コードの実行を突然停止し、`Dispose` または `Finalize` メソッド、またはその他の Visual Basic コードを呼び出しません。 他のプログラムによって保持されているオブジェクト参照は無効になります。 @No__t_0 ステートメントが `Try` または `Catch` ブロック内で検出された場合、コントロールは対応する `Finally` ブロックに渡されません。  
  
 @No__t_0 ステートメントは実行を中断しますが、`End` とは異なり、コンパイル済みの実行可能 (.exe) ファイルに存在しない限り、ファイルは閉じられず、変数はクリアされません。  
  
 @No__t_0 は、開いている可能性のあるリソースには参加せずにアプリケーションを終了するため、使用する前に、正常に終了するようにしてください。 たとえば、アプリケーションでフォームが開いている場合は、コントロールが `End` ステートメントに到達する前に、それらを閉じる必要があります。  
  
 @No__t_0 は、すぐに停止する必要がある場合にのみ使用してください。 プロシージャを終了する通常の方法 ([Return statement](../../../visual-basic/language-reference/statements/return-statement.md)ステートメントと[Exit ステートメント](../../../visual-basic/language-reference/statements/exit-statement.md)) は、プロシージャを正常に終了するだけでなく、呼び出し元のコードが正常に終了する機会を与えることもできます。 たとえば、コンソールアプリケーションは、単純に `Main` プロシージャから `Return` できます。  
  
> [!IMPORTANT]
> @No__t_0 ステートメントは、<xref:System> 名前空間の <xref:System.Environment> クラスの <xref:System.Environment.Exit%2A> メソッドを呼び出します。 <xref:System.Environment.Exit%2A> には `UnmanagedCode` のアクセス許可が必要です。 そうしないと、<xref:System.Security.SecurityException> エラーが発生します。  
  
 その後に追加のキーワードが続く場合、 [end \<keyword > ステートメント](../../../visual-basic/language-reference/statements/end-keyword-statement.md)は、適切なプロシージャまたはブロックの定義の末尾に記述ます。 たとえば、`End Function` は `Function` プロシージャの定義を終了します。  
  
## <a name="example"></a>例  
 次の例では、`End` ステートメントを使用して、ユーザーから要求された場合にコードの実行を終了します。  
  
 [!code-vb[VbVersHelp60Controls#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVersHelp60Controls/VB/Form1.vb#64)]  
  
## <a name="smart-device-developer-notes"></a>スマートデバイスの開発者向けメモ  
 このステートメントはサポートされていません。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Security.Permissions.SecurityPermissionFlag>
- [Stop ステートメント](../../../visual-basic/language-reference/statements/stop-statement.md)
- [End \<keyword > ステートメント](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
