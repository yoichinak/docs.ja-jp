---
title: '方法: OpenFileDialog コンポーネントでファイルを開く'
ms.date: 02/11/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], opening files
- OpenFile method [Windows Forms], OpenFileDialog component
- files [Windows Forms], opening with OpenFileDialog component
ms.assetid: 9d88367a-cc21-4ffd-be74-89fd63767d35
ms.openlocfilehash: 5781543a61d77ef8f0658e95759c57fdb77cfc4f
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723089"
---
# <a name="how-to-open-files-with-the-openfiledialog"></a>方法: それは、OpenFileDialog を開いているファイル 

<xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType>コンポーネントは、参照やファイルを選択する [Windows] ダイアログ ボックスを開きます。 開き、選択したファイルを読み取り、使用することができます、<xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType>メソッド、またはのインスタンスを作成、<xref:System.IO.StreamReader?displayProperty=nameWithType>クラス。 次の例では、両方の方法を示します。 

.NET framework で取得または設定する、<xref:System.Windows.Forms.FileDialog.FileName%2A>プロパティには特権レベルが付与して、<xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType>クラス。 例では、実行、<xref:System.Security.Permissions.FileIOPermission>アクセス許可を確認して、部分的に信頼されたコンテキストで実行する場合は、特権がないため例外をスローできます。 詳細については、[コード アクセス セキュリティの基礎](../../misc/code-access-security-basics.md)を参照してください。

ビルドしてから、.NET Framework アプリとしてこれらの例を実行することができます、C#または Visual Basic のコマンド ライン。 詳細については、[csc.exe を](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)または[コマンドラインからビルド](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)を参照してください。 

.NET Core 3.0 以降では、ことができますもビルドおよび実行する例では、.NET Core アプリを Windows として .NET Core の Windows フォームのあるフォルダーから *\<フォルダー名>.csproj* プロジェクト ファイル。 

## <a name="example-read-a-file-as-a-stream-with-streamreader"></a>例:StreamReader とストリームとしてファイルを読み取り  
  
次のコードの例では、Windows フォーム<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Click>を開くイベント ハンドラー、<xref:System.Windows.Forms.OpenFileDialog>で、<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>メソッド。 ユーザーがファイルを選択し、選択した後**OK**のインスタンス、<xref:System.IO.StreamReader>クラス ファイルを読み取り、フォームのテキスト ボックスにその内容を表示します。 ファイル ストリームからの読み取りの詳細については、<xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType>と<xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType>を参照してください。  

 [!code-csharp[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/vb/Form1.vb)]  

## <a name="example-open-a-file-from-a-filtered-selection-with-openfile"></a>例:選択されている OpenFile フィルター選択された項目からファイルを開く 

次の例では、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Click>を開くイベント ハンドラー、<xref:System.Windows.Forms.OpenFileDialog>はテキスト ファイルのみを表示するフィルター。 ユーザーがテキスト ファイルを選択し、選択した後**OK**、<xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A>メソッドを使用して、メモ帳でファイルを開きます。

 [!code-csharp[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/vb/Form1.vb)]  

## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.OpenFileDialog>
- [OpenFileDialog コンポーネント](openfiledialog-component-windows-forms.md)
