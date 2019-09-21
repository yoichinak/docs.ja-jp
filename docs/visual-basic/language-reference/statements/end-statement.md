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
ms.openlocfilehash: 9307cf10e6125441bd49baa0e663a5a13f234005
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944463"
---
# <a name="end-statement"></a>End ステートメント
直ちに実行を終了します。  
  
## <a name="syntax"></a>構文  
  
```  
End  
```  
  
## <a name="remarks"></a>Remarks  
 `End`ステートメントをプロシージャ内の任意の場所に配置して、アプリケーション全体の実行を強制的に停止することができます。 `End``Open`ステートメントで開かれたすべてのファイルを閉じ、すべてのアプリケーションの変数をクリアします。 オブジェクトへの参照を保持しているプログラムが他になく、そのコードも実行されていない場合、アプリケーションはすぐに終了します。  
  
> [!NOTE]
> ステートメントは、コードの実行を突然停止します。 `Dispose`また`Finalize` 、メソッド、メソッド、またはその他の Visual Basic コードを呼び出しません。 `End` 他のプログラムによって保持されているオブジェクト参照は無効になります。 ステートメントが`Try`また`Finally`は`Catch`ブロック内で見つかった場合、コントロールは対応するブロックに渡されません。 `End`  
  
 ステートメント`Stop`は実行を中断します`End`が、とは異なり、コンパイルされた実行可能 (.exe) ファイルに存在しない限り、ファイルを閉じたり変数をクリアしたりすることはありません。  
  
 は`End` 、開いている可能性のあるリソースには参加せずにアプリケーションを終了するため、使用する前に正常に終了するようにしてください。 たとえば、アプリケーションでフォームが開いている場合は、コントロールがステートメントに`End`到達する前に、フォームを閉じる必要があります。  
  
 をすぐに`End`停止する必要がある場合にのみ、を使用する必要があります。 プロシージャを終了する通常の方法 ([Return statement](../../../visual-basic/language-reference/statements/return-statement.md)ステートメントと[Exit ステートメント](../../../visual-basic/language-reference/statements/exit-statement.md)) は、プロシージャを正常に終了するだけでなく、呼び出し元のコードが正常に終了する機会を与えることもできます。 たとえば、コンソールアプリケーションは単`Return`に`Main`プロシージャから実行できます。  
  
> [!IMPORTANT]
> ステートメント`End`は、 <xref:System>名前<xref:System.Environment.Exit%2A>空間の<xref:System.Environment>クラスのメソッドを呼び出します。 <xref:System.Environment.Exit%2A>にはアクセス許可`UnmanagedCode`が必要です。 そうしないと、 <xref:System.Security.SecurityException>エラーが発生します。  
  
 その後に追加のキーワードが続くと、 [end \<キーワード > ステートメント](../../../visual-basic/language-reference/statements/end-keyword-statement.md)は、適切なプロシージャまたはブロックの定義の末尾に記述ます。 たとえば、は`End Function` `Function`プロシージャの定義を終了します。  
  
## <a name="example"></a>例  
 次の例では`End` 、ステートメントを使用して、ユーザーが要求した場合にコードの実行を終了します。  
  
 [!code-vb[VbVersHelp60Controls#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVersHelp60Controls/VB/Form1.vb#64)]  
  
## <a name="smart-device-developer-notes"></a>スマートデバイスの開発者向けメモ  
 このステートメントはサポートされていません。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Security.Permissions.SecurityPermissionFlag>
- [Stop ステートメント](../../../visual-basic/language-reference/statements/stop-statement.md)
- [End \<キーワード > ステートメント](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
