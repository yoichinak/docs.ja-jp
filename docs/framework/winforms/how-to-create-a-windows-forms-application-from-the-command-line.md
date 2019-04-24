---
title: '方法: コマンドラインから Windows フォーム アプリケーションを作成します。'
ms.date: 03/14/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, application development from command line
- Windows Forms, getting started
- Windows Forms, creating basic form
ms.assetid: 45ad3f8b-1c26-4c9f-91a9-3bb0759a47a4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce97089ec71fc910079910957e784605387f3e06
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59299872"
---
# <a name="how-to-create-a-windows-forms-application-from-the-command-line"></a>方法: コマンドラインから Windows フォーム アプリケーションを作成します。
次の手順では、コマンドラインから Windows フォーム アプリケーションを作成して実行するために完了する必要のある基本的な手順について説明します。 Visual Studio では、これらの手順に対する広範なサポートが用意されています。  参照してください[チュートリアル。WPF でのフォーム コントロールのホストを Windows](../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)します。  
  
## <a name="procedure"></a>プロシージャ  
  
#### <a name="to-create-the-form"></a>フォームを作成するには  
  
1. 空のコード ファイルに、次の import ステートメントまたは using ステートメントを入力します。  
  
     [!code-csharp[System.Windows.Forms.BasicForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BasicForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#2)]  
  
2. フォーム クラスから継承する `Form1` という名前のクラスを宣言します。  
  
     [!code-csharp[System.Windows.Forms.BasicForm#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BasicForm#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#3)]  
  
3. `Form1` の既定のコンストラクターを作成します。  
  
     後続の手順で、コンストラクターにさらにコードを追加します。  
  
     [!code-csharp[System.Windows.Forms.BasicForm#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.BasicForm#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#4)]  
  
4. `Main` メソッドをクラスに追加します。  
  
    1.  適用、 <xref:System.STAThreadAttribute> c# `Main` Windows フォーム アプリケーションを指定するメソッドは、シングル スレッド アパートメント。 (属性は必要ありません Visual basic で Windows フォーム アプリケーション開発された Visual Basic の使用をシングル スレッド アパートメント モデルを既定であるためです。)  
  
    2.  呼び出す<xref:System.Windows.Forms.Application.EnableVisualStyles%2A>アプリケーションにオペレーティング システムのスタイルを適用します。  
  
    3.  フォームのインスタンスを作成して実行します。  
  
     [!code-csharp[System.Windows.Forms.BasicForm#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.BasicForm#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#5)]  
  
#### <a name="to-compile-and-run-the-application"></a>アプリケーションをコンパイルして実行するには  
  
1. .NET Framework コマンド プロンプトで、`Form1` クラスを作成したディレクトリに移動します。  
  
2. フォームをコンパイルします。  
  
    -   C# を使用している場合は、次のように入力します。 `csc form1.cs`  
  
         `-or-`  
  
    -   Visual Basic を使用している場合は、次のように入力します。 `vbc form1.vb`  
  
3. コマンド プロンプトで次のように入力します。 `Form1.exe`  
  
## <a name="adding-a-control-and-handling-an-event"></a>コントロールの追加とイベントの処理  
 前の手順は、コンパイルして実行する基本的な Windows フォームを作成する方法を示しました。 次の手順では、コントロールを作成してフォームに追加し、コントロールのイベントを処理する方法を示します。 Windows フォームに追加することができます、コントロールの詳細については、次を参照してください。 [Windows フォーム コントロール](./controls/index.md)します。  
  
 Windows フォーム アプリケーションを作成する方法を理解するだけでなく、イベント ベースのプログラミングとユーザー入力を処理する方法を理解する必要があります。 詳細については、次を参照してください[Windows フォームでのイベント ハンドラーの作成](creating-event-handlers-in-windows-forms.md)、および[ユーザー入力の処理。](./controls/handling-user-input.md)  
  
#### <a name="to-declare-a-button-control-and-handle-its-click-event"></a>ボタン コントロールを宣言して、クリック イベントを処理するには  
  
1. `button1` という名前のボタン コントロールを宣言します。  
  
2. コンストラクターでボタンを作成し、<xref:System.Windows.Forms.Control.Size%2A>、<xref:System.Windows.Forms.Control.Location%2A>、および <xref:System.Windows.Forms.Control.Text%2A> の各プロパティを設定します。  
  
3. フォームにボタンを追加します。  
  
     次のコード例は、ボタン コントロールを宣言する方法を示します。  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.FormWithButton#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#2)]  
  
4. ボタンで <xref:System.Windows.Forms.Control.Click> イベントを処理するメソッドを作成します。  
  
5. クリック イベント ハンドラーで、メッセージ "Hello World" と共に <xref:System.Windows.Forms.MessageBox> を表示します。  
  
     次のコード例は、ボタン コントロールのクリック イベントを処理する方法を示します。  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.FormWithButton#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#3)]  
  
6. <xref:System.Windows.Forms.Control.Click> イベントを作成したメソッドに関連付けます。  
  
     次のコード例は、イベントをメソッドに関連付ける方法を示します。  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.FormWithButton#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#4)]  
  
7. 前の手順で説明したように、アプリケーションをコンパイルして実行します。  
  
## <a name="example"></a>例  
 次のコード例は、前の手順の完全な例です。  
  
 [!code-csharp[System.Windows.Forms.FormWithButton#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.FormWithButton#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
  
-   コードをコンパイルするには、アプリケーションをコンパイルして実行する方法を説明した、前述の手順に従います。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Control>
- [Windows フォームの表示形式の変更](changing-the-appearance-of-windows-forms.md)
- [Windows フォーム アプリケーションの拡張](./advanced/index.md)
- [Windows フォームについて](getting-started-with-windows-forms.md)
