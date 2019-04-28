---
title: Visual Basic の Main プロシージャ
ms.date: 07/20/2015
f1_keywords:
- vb.Main
helpviewer_keywords:
- Main procedure
- Main method [Visual Basic]
- main function
ms.assetid: f0db283e-f283-4464-b521-b90858cc1b44
ms.openlocfilehash: 641edd2d0e0dde5f509c8fa77ccf65358fa76a31
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61920115"
---
# <a name="main-procedure-in-visual-basic"></a>Visual Basic の Main プロシージャ
すべての Visual Basic アプリケーションが呼び出されるプロシージャを含める必要があります`Main`します。 この手順では、開始ポイントし、アプリケーションの総合的な制御として機能します。 .NET Framework の呼び出し、`Main`に制御を渡す準備ができてし、アプリケーションが読み込まれたときにプロシージャ。 記述する必要がある、Windows フォーム アプリケーションを作成する場合を除き、`Main`自身で実行されるアプリケーションのプロシージャです。  
  
 `Main` 最初に実行されるコードが含まれています。 `Main`プログラムの開始時に最初に読み込まれる形式を決定、アプリケーションのコピーがシステムで既に実行されているかどうかを検索、アプリケーションの一連の変数を確立またはアプリケーションに必要なデータベースを開くことができます。  
  
## <a name="requirements-for-the-main-procedure"></a>メインのプロシージャの要件  
 (通常は拡張子 .exe) で自身で実行されるファイルを含める必要があります、`Main`プロシージャ。 (たとえば、拡張子は .dll) のライブラリとは実行されず、独自は必要ありません、`Main`プロシージャ。 作成するプロジェクトのさまざまな種類の要件は次のとおりです。  
  
- コンソール アプリケーションは、自分で実行して、少なくとも 1 つを指定する必要があります`Main`プロシージャ。 .  
  
- Windows フォーム アプリケーションが単独で実行します。 Visual Basic コンパイラが自動的に生成されますが、`Main`プロシージャなどのアプリケーションとする必要はありませんいずれかを記述します。  
  
- クラス ライブラリが不要、`Main`プロシージャ。 Windows コントロール ライブラリと Web コントロール ライブラリが含まれます。 Web アプリケーションは、クラス ライブラリとしてデプロイされます。  
  
## <a name="declaring-the-main-procedure"></a>メインのプロシージャを宣言します。  
 宣言する 4 つの方法がある、`Main`プロシージャ。 引数を受け取るものか、および値を返すことか。  
  
> [!NOTE]
>  宣言する場合`Main`クラスでは、使用する必要があります、`Shared`キーワード。 モジュールで`Main`する必要はありません`Shared`します。  
  
- 最も簡単な方法は、宣言する、`Sub`引数または値を返すプロシージャです。  
  
    ```  
    Module mainModule  
        Sub Main()  
            MsgBox("The Main procedure is starting the application.")  
            ' Insert call to appropriate starting place in your code.  
            MsgBox("The application is terminating.")  
        End Sub  
    End Module  
    ```  
  
- `Main` 返すことも、`Integer`値で、オペレーティング システムは、プログラムの終了コードとして使用します。 その他のプログラムでは、Windows ERRORLEVEL の値を調べることで、このコードをテストできます。 終了コードを返すを宣言する必要があります`Main`として、`Function`プロシージャの代わりに、`Sub`プロシージャ。  
  
    ```  
    Module mainModule  
        Function Main() As Integer  
            MsgBox("The Main procedure is starting the application.")  
            Dim returnValue As Integer = 0  
            ' Insert call to appropriate starting place in your code.  
            ' On return, assign appropriate value to returnValue.  
            ' 0 usually means successful completion.  
            MsgBox("The application is terminating with error level " &  
                 CStr(returnValue) & ".")  
            Return returnValue  
        End Function  
    End Module  
    ```  
  
- `Main` とることも、`String`引数として配列します。 配列内の各文字列には、プログラムの実行に使用したコマンドライン引数のいずれかが含まれています。 その値に応じて異なるアクションを実行できます。  
  
    ```  
    Module mainModule  
        Function Main(ByVal cmdArgs() As String) As Integer  
            MsgBox("The Main procedure is starting the application.")  
            Dim returnValue As Integer = 0  
            ' See if there are any arguments.  
            If cmdArgs.Length > 0 Then  
                For argNum As Integer = 0 To UBound(cmdArgs, 1)  
                    ' Insert code to examine cmdArgs(argNum) and take  
                    ' appropriate action based on its value.  
                Next argNum  
            End If  
            ' Insert call to appropriate starting place in your code.  
            ' On return, assign appropriate value to returnValue.  
            ' 0 usually means successful completion.  
            MsgBox("The application is terminating with error level " &  
                 CStr(returnValue) & ".")  
            Return returnValue  
        End Function  
    End Module  
    ```  
  
- 宣言できます`Main`コマンドライン引数を検証が終了コードを次のように返されません。  
  
    ```  
    Module mainModule  
        Sub Main(ByVal cmdArgs() As String)  
            MsgBox("The Main procedure is starting the application.")  
            Dim returnValue As Integer = 0  
            ' See if there are any arguments.  
            If cmdArgs.Length > 0 Then  
                For argNum As Integer = 0 To UBound(cmdArgs, 1)  
                    ' Insert code to examine cmdArgs(argNum) and take  
                    ' appropriate action based on its value.  
                Next argNum  
            End If  
            ' Insert call to appropriate starting place in your code.  
            MsgBox("The application is terminating.")  
        End Sub  
    End Module  
    ```  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>
- <xref:System.Array.Length%2A>
- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [Visual Basic プログラムの構造](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [/main](../../../visual-basic/reference/command-line-compiler/main.md)
- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)
- [Integer データ型](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [String データ型](../../../visual-basic/language-reference/data-types/string-data-type.md)
