---
title: '方法: Windows フォームでサウンドの再生をループする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sound loops
- SoundPlayer class [Windows Forms], play looping
- sounds [Windows Forms], looping
- playing sounds [Windows Forms], looping
ms.assetid: ea95dd46-10a3-46c0-8263-4b205f00df7f
ms.openlocfilehash: a74acbbbcb5646a35de54a6000a0feae30f145a5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638912"
---
# <a name="how-to-loop-a-sound-playing-on-a-windows-form"></a>方法: Windows フォームでサウンドの再生をループする
サウンドを繰り返し再生するコード例を次に示します。 `stopPlayingButton_Click` イベント ハンドラー内のコードが実行されると、現在再生されているサウンドが停止します。 サウンドが再生されていない場合は、何も起こりません。  
  
## <a name="example"></a>例  
 [!code-csharp[System.Media.SoundPlayer.PlayLooping#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.PlayLooping#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
- System アセンブリおよび System.Windows.Forms アセンブリへの参照。  
  
- ファイル名 `"c:\Windows\Media\chimes.wav"` を有効なファイル名に置き換えます。  
  
 Visual Basic または Visual C# からこの例をビルドする方法については、[コマンド ラインからのビルド](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)、または[csc.exe を使用したコマンド ラインからのビルド](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) を参照してください。 新しいプロジェクトにコードを貼り付けることによって、この例では、Visual Studio を構築することもできます。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 ファイルの操作は、適切な例外処理ブロックで囲む必要があります。  
  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
- パス名が不適切である場合。 たとえば、無効な文字が含まれている場合や、空白だけの場合などです (<xref:System.ArgumentException> クラス)。  
  
- パスが読み取り専用である場合 (<xref:System.IO.IOException> クラス)。  
  
- パス名が `Nothing` である場合 (<xref:System.ArgumentNullException> クラス)。  
  
- パス名が長すぎる場合 (<xref:System.IO.PathTooLongException> クラス)。  
  
- パスが無効である場合 (<xref:System.IO.DirectoryNotFoundException> クラス)。  
  
- パスがコロン":" のみである場合 (<xref:System.NotSupportedException> クラス)。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 ファイル名からファイルの内容を判断しないでください。 たとえば、Form1.vb というファイルは Visual Basic のソース ファイルではない可能性もあります。 アプリケーションでデータを使用する前に、入力をすべて検証してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Media.SoundPlayer.PlayLooping%2A>
- [方法: Windows フォームからサウンドを再生します。](how-to-play-a-sound-from-a-windows-form.md)
- [SoundPlayer クラスの概要](soundplayer-class-overview.md)
