---
title: '方法: キーボード入力を標準コントロールに変更する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keyboard input [Windows Forms], modifying
- modifying keyboard input
- Windows Forms, modifying keyboard input
- keyboards [Windows Forms], keyboard input
ms.assetid: 626d3712-d866-4988-bcda-a2d5b36ec0ba
ms.openlocfilehash: 175296a904a6aed70147f513959fce74b3288abc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64630486"
---
# <a name="how-to-modify-keyboard-input-to-a-standard-control"></a>方法: キーボード入力を標準コントロールに変更する
Windows フォームは、キーボードの入力を使用して変更する機能を提供します。 キーの使用とは、メッセージ キューのさらに下のその他のメソッドとイベントが、キーの値を受信しないようにメソッドまたはイベント ハンドラー内のキーを処理することを表します。 キーの変更とは、メッセージ キューのさらに下のメソッドとイベント ハンドラーが、異なるキーの値を受け取るようにキーの値を変更することを表します。 このトピックでは、これらのタスクを実行する方法について説明します。  
  
### <a name="to-consume-a-key"></a>キーを使用するには  
  
- <xref:System.Windows.Forms.Control.KeyPress> イベント ハンドラーで、<xref:System.Windows.Forms.KeyPressEventArgs> クラスの <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> プロパティを `true` に設定します。  
  
     または  
  
     <xref:System.Windows.Forms.Control.KeyDown> イベント ハンドラーで、<xref:System.Windows.Forms.KeyEventArgs> クラスの <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> プロパティを `true` に設定します。  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.Control.KeyDown> イベント ハンドラーで <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> プロパティを設定すると、<xref:System.Windows.Forms.Control.KeyPress> イベントと <xref:System.Windows.Forms.Control.KeyUp> イベントが現在のキー入力から発生しないようにすることができます。 この目的には、<xref:System.Windows.Forms.KeyEventArgs.SuppressKeyPress%2A> プロパティを使用します。  
  
     次の例は、<xref:System.Windows.Forms.Control.KeyPress> イベント ハンドラーによって受信された <xref:System.Windows.Forms.KeyPressEventArgs> の <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> プロパティを検査する `switch` ステートメントの抜粋です。 このコードは、'A' と 'a' 文字のキーを使用します。  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#6)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#6)]  
  
### <a name="to-modify-a-standard-character-key"></a>標準の文字のキーを変更するには  
  
- <xref:System.Windows.Forms.Control.KeyPress> イベント ハンドラーで、<xref:System.Windows.Forms.KeyPressEventArgs> クラスの <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> プロパティを新しい文字のキーの値に設定します。  
  
     次の例は、'B' を 'A' に変更して、'b' を 'a' に変更する `switch` ステートメントの抜粋です。 <xref:System.Windows.Forms.KeyPressEventArgs> パラメーターの <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> のプロパティが `false` に設定され、新しいキーの値が、メッセージ キューの他のメソッドとイベントに反映されることに注意してください。  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#7)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#7)]  
  
### <a name="to-modify-a-noncharacter-key"></a>非文字キーを変更するには  
  
- Windows メッセージを処理する <xref:System.Windows.Forms.Control> メソッドをオーバーライドして、WM_KEYDOWN または WM_SYSKEYDOWN のメッセージを検出し、<xref:System.Windows.Forms.Message> パラメーターの <xref:System.Windows.Forms.Message.WParam%2A> プロパティを、新しい非文字キーを表す <xref:System.Windows.Forms.Keys> 値に設定します。  
  
     次のコード例は、F1 から F9 のキーを検出して、F3 キーを押したときに F1 に変更するよう、コントロールの <xref:System.Windows.Forms.Control.PreProcessMessage%2A> メソッドをオーバーライドする方法を示しています、 詳細については<xref:System.Windows.Forms.Control>キーボードのメッセージを先にオーバーライドできるメソッドを参照してください[、Windows フォーム アプリケーションにおけるユーザー入力](user-input-in-a-windows-forms-application.md)と[キーボード入力のしくみ](how-keyboard-input-works.md)します。  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#12)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#12)]  
  
## <a name="example"></a>例  
 次のコード例は、前のセクションのコード例の完全なアプリケーションです。 アプリケーションは、<xref:System.Windows.Forms.TextBox> クラスから派生したカスタム コントロールを使用して、キーボードの入力を使用して変更します。  
  
 [!code-csharp[System.Windows.Forms.KeyBoardInput#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInput#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
- System、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。  
  
 Visual Basic または Visual C# からこの例をビルドする方法については、[コマンド ラインからのビルド](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)、または[csc.exe を使用したコマンド ラインからのビルド](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) を参照してください。 新しいプロジェクトにコードを貼り付けることによって、この例では、Visual Studio を構築することもできます。  
  
## <a name="see-also"></a>関連項目

- [Windows フォーム アプリケーションにおけるキーボード入力](keyboard-input-in-a-windows-forms-application.md)
- [Windows フォーム アプリケーションにおけるユーザー入力](user-input-in-a-windows-forms-application.md)
- [キーボード入力のしくみ](how-keyboard-input-works.md)
