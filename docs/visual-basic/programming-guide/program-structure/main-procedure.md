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
ms.openlocfilehash: b6c8ec4052d834d410df7fef12e59434f5fdfb44
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039977"
---
# <a name="main-procedure-in-visual-basic"></a>Visual Basic の Main プロシージャ
すべての Visual Basic アプリケーションには、と`Main`いうプロシージャが含まれている必要があります。 この手順は、アプリケーションの開始点と全体的な制御として機能します。 .NET Framework は、アプリケーション`Main`を読み込んだときにプロシージャを呼び出し、そのプロシージャに制御を渡す準備ができています。 Windows フォームアプリケーションを作成する場合を除き、独自に実行`Main`するアプリケーション用の手順を記述する必要があります。

 `Main`最初に実行されるコードが含まれています。 で`Main`は、プログラムの開始時に最初に読み込まれるフォームを決定し、アプリケーションのコピーが既にシステムで実行されているかどうかを確認したり、アプリケーションに対して一連の変数を設定したり、アプリケーションで必要なデータベースを開いたりすることができます。

## <a name="requirements-for-the-main-procedure"></a>Main プロシージャの要件
 独自の (通常は拡張子 .exe) で実行されるファイルには、 `Main`プロシージャが含まれている必要があります。 ライブラリ (たとえば、拡張子 .dll) は独自には実行されず、プロシージャは`Main`必要ありません。 作成できるさまざまな種類のプロジェクトの要件は次のとおりです。

- コンソールアプリケーションは自身で実行されるため、少なくとも 1 `Main`つのプロシージャを指定する必要があります。

- Windows フォームアプリケーションは独自に実行されます。 ただし、このようなアプリケーションでは`Main` 、Visual Basic コンパイラによってプロシージャが自動的に生成されるため、作成する必要はありません。

- クラスライブラリには、プロシージャ`Main`は必要ありません。 これには、Windows コントロールライブラリと Web コントロールライブラリが含まれます。 Web アプリケーションはクラスライブラリとして配置されます。

## <a name="declaring-the-main-procedure"></a>Main プロシージャの宣言
 プロシージャを宣言するには、 `Main`次の4つの方法があります。 引数を受け取ることも、それ以外の値を返すこともできます。

> [!NOTE]
>  クラスでを`Main`宣言する場合は、 `Shared`キーワードを使用する必要があります。 モジュールでは、 `Main`はである必要`Shared`はありません。

- 最も簡単な方法は、引数`Sub`を取らず、値を返さないプロシージャを宣言することです。

    ```vb
    Module mainModule
        Sub Main()
            MsgBox("The Main procedure is starting the application.")
            ' Insert call to appropriate starting place in your code.
            MsgBox("The application is terminating.")
        End Sub
    End Module
    ```

- `Main`は、オペレーティングシステム`Integer`がプログラムの終了コードとして使用する値を返すこともできます。 他のプログラムでは、Windows の ERRORLEVEL 値を調べることによって、このコードをテストできます。 終了コードを返すには、 `Main` `Sub`プロシージャではなく`Function` 、プロシージャとして宣言する必要があります。

    ```vb
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

- `Main`は、引数と`String`して配列を受け取ることもできます。 配列内の各文字列には、プログラムを呼び出すために使用されるコマンドライン引数の1つが含まれています。 値に応じて、さまざまなアクションを実行できます。

    ```vb
    Module mainModule
        Function Main(ByVal cmdArgs() As String) As Integer
            MsgBox("The Main procedure is starting the application.")
            Dim returnValue As Integer = 0
            ' See if there are any arguments.
            If cmdArgs.Length > 0 Then
                For argNum As Integer = 0 To UBound(cmdArgs, 1)
                    ' Insert code to examine cmdArgs(argNum) and take
                    ' appropriate action based on its value.
                Next
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

- を宣言`Main`すると、次のように、コマンドライン引数を調べることができますが、終了コードは返されません。

    ```vb
    Module mainModule
        Sub Main(ByVal cmdArgs() As String)
            MsgBox("The Main procedure is starting the application.")
            Dim returnValue As Integer = 0
            ' See if there are any arguments.
            If cmdArgs.Length > 0 Then
                For argNum As Integer = 0 To UBound(cmdArgs, 1)
                    ' Insert code to examine cmdArgs(argNum) and take
                    ' appropriate action based on its value.
                Next
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
