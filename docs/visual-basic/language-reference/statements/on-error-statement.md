---
title: On Error ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.OnError
helpviewer_keywords:
- Visual Basic code, control flow
- Resume Next statement [Visual Basic]
- errors [Visual Basic], trapping
- error handling, On Error statement
- Next statement [Visual Basic], On Error
- control flow [Visual Basic], branching
- Error keyword [Visual Basic]
- execution [Visual Basic], conditional
- Resume statement [Visual Basic], and On Error statement
- Error statement [Visual Basic], and On Error statement
- GoTo statement [Visual Basic], and On Error statement
- branching [Visual Basic], on error
- conditional statements [Visual Basic], On Error
- On Error statement [Visual Basic], syntax
- On keyword [Visual Basic]
- run-time errors [Visual Basic], handling
- On Error statement [Visual Basic]
ms.assetid: ff947930-fb84-40cf-bd66-1ea219561d5c
ms.openlocfilehash: 0a5a5261e6b71178adce02a5635c1f91a1469f3d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61784073"
---
# <a name="on-error-statement-visual-basic"></a>On Error ステートメント (Visual Basic)
エラー処理ルーチンを有効にして、プロシージャ内のルーチンの場所を指定しますエラー処理ルーチンを無効にも使用できます。  
  
 実行時に発生するエラーは致命的なエラー処理がない: エラー メッセージが表示され、実行が停止します。  
  
 非構造化例外処理を使用するのではなく、コードで、処理、構造化例外の使用をお勧め可能であれば、および`On Error`ステートメント。 詳細については、[Try...Catch...Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)を参照してください。  
  
> [!NOTE]
>  `Error`キーワードでも使用、 [Error ステートメント](../../../visual-basic/language-reference/statements/error-statement.md)、旧バージョンとの互換性のためサポートされています。  
  
## <a name="syntax"></a>構文  
  
```  
On Error { GoTo [ line | 0 | -1 ] | Resume Next }  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`GoTo` `line`|により、エラー処理ルーチンで必要な指定した行から始まる`line`引数。 `line`引数が任意の行のラベルまたは行番号。 実行時エラーが発生した場合は、エラー ハンドラーをアクティブにする際、指定した行に分岐を制御します。 指定した行と同じ手順である必要があります、`On Error`ステートメント、または、コンパイル時エラーが発生します。|  
|`GoTo` 0|現在のプロシージャで有効になっているエラー ハンドラーを無効にし、リセット`Nothing`します。|  
|`GoTo` -1|現在のプロシージャで有効になっている例外を無効にし、リセット`Nothing`します。|  
|`Resume Next`|実行時エラーが発生したときに、エラーが発生したし、そのポイントから実行が継続のステートメントの直後のステートメントにコントロールが移動を指定します。 このフォームを使用してなく`On Error GoTo`オブジェクトにアクセスするときにします。|  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
>  非構造化例外処理を使用するのではなく、可能であれば、コード内の構造化例外処理を使用することをお勧め、`On Error`ステートメント。 詳細については、[Try...Catch...Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)を参照してください。  
  
 "Enabled"のエラー ハンドラーは、いずれかで有効になっている、`On Error`ステートメント。 「アクティブ」のエラー ハンドラーは、エラーを処理するプロセスでは有効なハンドラーです。  
  
 エラー ハンドラーがアクティブな間にエラーが発生したかどうか (エラーの発生間と`Resume`、 `Exit Sub`、 `Exit Function`、または`Exit Property`ステートメント)、現在のプロシージャのエラー ハンドラーは、エラーを処理できません。 呼び出し元のプロシージャに制御が戻ります。  
  
 呼び出し元のプロシージャに有効になっているエラー ハンドラーがある場合は、エラーを処理するためにアクティブ化します。 呼び出し元のプロシージャのエラー ハンドラーもアクティブな場合は、コントロールは、有効であっても、非アクティブなエラー ハンドラーが見つかるまで呼び出し元の前の手順を遡ってに渡します。 このようなエラー ハンドラーが見つからない場合は、エラーが、実際に発生した時点で致命的です。  
  
 エラー ハンドラーは、呼び出し元のプロシージャにコントロールを通過するたびにそのプロシージャには、現在のプロシージャになります。 指定された位置から現在のプロシージャの実行が再開されているいずれかのプロシージャのエラー ハンドラーによってエラーが処理されたら、`Resume`ステートメント。  
  
> [!NOTE]
>  エラー処理ルーチンは、`Sub`プロシージャまたは`Function`プロシージャ。 これは、行ラベルまたは行番号でマークされたコードのセクションです。  
  
## <a name="number-property"></a>Number プロパティ  
 エラー処理ルーチンで値を使用して、`Number`のプロパティ、`Err`エラーの原因を特定するオブジェクト。 ルーチンのテストまたはで関連するプロパティの値を保存する必要があります、`Err`前に、その他のエラーが発生する可能性がまたは可能性がある手順の前にエラーが呼び出されます。 プロパティの値で、`Err`オブジェクトは、最新のエラーのみを反映します。 エラー メッセージに関連付けられている`Err.Number`に含まれている`Err.Description`します。  
  
## <a name="throw-statement"></a>Throw ステートメント  
 エラーが発生しますが、`Err.Raise`メソッドのセット、`Exception`プロパティの新しく作成されたインスタンスを<xref:System.Exception>クラス。 派生した例外の種類の例外の発生をサポートするために、`Throw`言語でステートメントがサポートされています。 これがスローされる例外のインスタンスでは 1 つのパラメーターを取ります。 次の例では、これらの機能を使用して、既存の例外処理のサポートを使用する方法を示しています。  
  
 [!code-vb[VbVbalrErrorHandling#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#17)]  
  
 なお、`On Error GoTo`ステートメントは、例外クラスに関係なく、すべてのエラーをトラップします。  
  
## <a name="on-error-resume-next"></a>次に on Error Resume  
 `On Error Resume Next` 実行、実行時エラーの原因となったステートメントの直後のステートメントを続行または最新の直後に続くステートメントを使用して、プロシージャを含む外呼び出しを`On Error Resume Next`ステートメント。 このステートメントでは、実行、実行時エラーに関係なく続行をできるようにします。 プロシージャ内の別の場所に制御を転送するのではなく、エラーが発生するか、エラー処理ルーチンを配置することができます。 `On Error Resume Next`ステートメントになり、使用頻度の低い別のプロシージャが呼び出されたときに実行する必要があります、`On Error Resume Next`インライン エラーのルーチン内で処理する場合、各ステートメントがルーチンを呼び出すとします。  
  
> [!NOTE]
>  `On Error Resume Next`コンストラクトことをお勧めする`On Error GoTo`他のオブジェクトへのアクセス中にエラーを処理するときにします。 チェック`Err`オブジェクトと対話は、コードによってアクセスされたオブジェクトがあいまいさを削除します。 確認するオブジェクトのエラー コードを配置する`Err.Number`、どのオブジェクトが最初に、エラーを生成および (で指定されたオブジェクト`Err.Source`)。  
  
## <a name="on-error-goto-0"></a>Error GoTo 0  
 `On Error GoTo 0` 現在のプロシージャでのエラー処理を無効にします。 0 行目の手順には、番号 0 の行が含まれている場合でも、エラー処理コードの先頭として指定しません。 なし、`On Error GoTo 0`プロシージャが終了すると、ステートメントでは、エラー ハンドラーが自動的に無効にします。  
  
## <a name="on-error-goto--1"></a>Error GoTo-1 で  
 `On Error GoTo -1` 現在のプロシージャで例外を無効にします。 指定しません行-1、エラー処理コードの先頭としてプロシージャには、-1 を番号の行が含まれている場合でもです。 なし、`On Error GoTo -1`プロシージャが終了すると、ステートメントでは、例外が自動的に無効にします。  
  
 エラー処理コードが、エラーが発生していないときに実行しないように、配置、 `Exit Sub`、 `Exit Function`、または`Exit Property`次のフラグメントのように、エラー処理ルーチンの直前のステートメント。  
  
 [!code-vb[VbVbalrErrorHandling#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#18)]  
  
 エラー処理コードを次に示します、`Exit Sub`ステートメントの前と、`End Sub`ステートメント、プロシージャのフローから分離することです。 プロシージャでエラー処理コードをどこでも配置できます。  
  
## <a name="untrapped-errors"></a>エラーをトラップしません。  
 オブジェクトでエラーをトラップしないは、オブジェクトが実行可能ファイルとして実行されているときに、制御のアプリケーションに返されます。 開発環境内でエラーをトラップしないが、適切なオプションが設定されている場合にのみ制御するアプリケーションに返されます。 デバッグ中に設定、これらを設定する方法、およびホストがクラスを作成するかどうかをオプションにする説明については、ホスト アプリケーションのマニュアルを参照してください。  
  
 その他のオブジェクトにアクセスするオブジェクトを作成する場合戻す未処理のエラーを処理しようとする必要があります。 場合のエラー コードをマップすることはできません、`Err.Number`独自のエラーと、パスのいずれかには、オブジェクトの呼び出し元に戻します。 エラー コードを追加して、エラーを指定する必要があります、`VbObjectError`定数。 たとえば、エラー コードが 1052 の場合は、そのよう割り当てます。  
  
 [!code-vb[VbVbalrErrorHandling#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#19)]  
  
> [!CAUTION]
>  Windows ダイナミック リンク ライブラリ (Dll) への呼び出し中にシステム エラーは、例外は発生せず、Visual Basic エラー トラッピングをトラップすることはできません。 各戻り値の成功または失敗 (に従って、API の仕様を確認する必要があります DLL 関数を呼び出すときに、障害が発生した場合値を確認し、`Err`オブジェクトの`LastDLLError`プロパティ。  
  
## <a name="example"></a>例  
 この例を使用して、`On Error GoTo`ステートメント、プロシージャ内のエラー処理ルーチンの場所を指定します。 例では、0 で除算しようとするは、エラー数 6 を生成します。 エラーは、エラー処理ルーチンで処理され、コントロールは、エラーの原因となったステートメントに返されます。 `On Error GoTo 0`ステートメントがエラー トラッピングをオフにします。 次に、`On Error Resume Next`ステートメントを使用して、次のステートメントによって生成されたエラーのコンテキストが特定の認識されるようにエラーをトラップするを延期します。 なお`Err.Clear`をオフにするために使用、`Err`エラーを処理した後、オブジェクトのプロパティ。  
  
 [!code-vb[VbVbalrErrorHandling#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#20)]  
  
## <a name="requirements"></a>必要条件  
 **名前空間:**[Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **アセンブリ:** Visual Basic ランタイム ライブラリ (Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Number%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Description%2A>
- <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>
- [End ステートメント](../../../visual-basic/language-reference/statements/end-statement.md)
- [Exit ステートメント](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Resume ステートメント](../../../visual-basic/language-reference/statements/resume-statement.md)
- [エラー メッセージ](../../../visual-basic/language-reference/error-messages/index.md)
- [Try...Catch...Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
