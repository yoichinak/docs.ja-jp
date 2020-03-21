---
title: '方法: ファイルを開くダイアログ コンポーネントを使用してファイルを開く'
ms.date: 02/11/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], opening files
- OpenFile method [Windows Forms], OpenFileDialog component
- files [Windows Forms], opening with OpenFileDialog component
ms.assetid: 9d88367a-cc21-4ffd-be74-89fd63767d35
ms.openlocfilehash: ca69de19ab1b9ae387002898145fe99e35a7b6b9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182128"
---
# <a name="how-to-open-files-with-the-openfiledialog"></a>方法 : ファイルを開くダイアログ ボックスでファイルを開く

この<xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType>コンポーネントは、ファイルの参照と選択を行うための Windows ダイアログ ボックスを開きます。 選択したファイルを開いて読み取るために、メソッド<xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType>を使用するか、クラスのインスタンスを<xref:System.IO.StreamReader?displayProperty=nameWithType>作成します。 次の例は、両方の方法を示しています。

.NET Framework では、プロパティを取得<xref:System.Windows.Forms.FileDialog.FileName%2A>または設定するには、クラスによって付与される<xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType>特権レベルが必要です。 この例では、<xref:System.Security.Permissions.FileIOPermission>アクセス許可チェックを実行し、部分信頼コンテキストで実行すると、特権が不十分なために例外をスローできます。 詳細については、「コード[アクセス セキュリティの基本](../../misc/code-access-security-basics.md)」を参照してください。

これらの例は、C# または Visual Basic のコマンド ラインから .NET Framework アプリとしてビルドして実行できます。 詳細については、「 [csc.exe を使用したコマンド ラインビルド](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)」または「[コマンド ラインからのビルド](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)」を参照してください。

NET Core 3.0 以降では、.NET Core Windows フォーム*\<フォルダー名>.csproj*プロジェクト ファイルを持つフォルダーから Windows .NET Core アプリとしてサンプルをビルドして実行することもできます。

## <a name="example-read-a-file-as-a-stream-with-streamreader"></a>例: ストリームリーダーを使用してファイルをストリームとして読み取る  
  
次の例では、Windows<xref:System.Windows.Forms.Button>フォーム コントロール<xref:System.Windows.Forms.Control.Click>のイベント ハンドラーを<xref:System.Windows.Forms.OpenFileDialog>使用して<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>、メソッドを使用して を開きます。 ユーザーがファイルを選択して **[OK] を**選択すると、クラス<xref:System.IO.StreamReader>のインスタンスがファイルを読み取り、フォームのテキスト ボックスに内容を表示します。 ファイル ストリームからの読み取りの詳細<xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType>については<xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType>、 および を参照してください。  

 [!code-csharp[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/vb/Form1.vb)]  

## <a name="example-open-a-file-from-a-filtered-selection-with-openfile"></a>例: OpenFile を使用して、フィルター選択されたファイルを開く

次の例では、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Click>イベント ハンドラーを使用して<xref:System.Windows.Forms.OpenFileDialog>、テキスト ファイルのみを表示するフィルターを使用して を開きます。 ユーザーがテキスト ファイルを選択し、[ **OK**]<xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A>を選択すると、このメソッドを使用してメモ帳でファイルを開きます。

 [!code-csharp[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/vb/Form1.vb)]  

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.OpenFileDialog>
- [コンポーネントを開きます。](openfiledialog-component-windows-forms.md)
