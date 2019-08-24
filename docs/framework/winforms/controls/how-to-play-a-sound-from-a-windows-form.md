---
title: '方法: Windows フォームからサウンドを再生する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- playing sounds [Windows Forms], Windows Forms
- sounds [Windows Forms], playing
- sounds
- My.Computer.Audio object [Windows Forms], playing sounds
- examples [Windows Forms], sounds
ms.assetid: 3d3350b7-1ebd-4e05-a738-48ca1160a19d
ms.openlocfilehash: 68a68f05b847877641132e540995f6b14bb6e065
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015799"
---
# <a name="how-to-play-a-sound-from-a-windows-form"></a>方法: Windows フォームからサウンドを再生する
この例では、実行時に指定されたパスでサウンドを再生します。

## <a name="example"></a>例

```vb
Sub PlaySimpleSound()
    My.Computer.Audio.Play("c:\Windows\Media\chimes.wav")
End Sub
```

```csharp
private void playSimpleSound()
{
    SoundPlayer simpleSound = new SoundPlayer(@"c:\Windows\Media\chimes.wav");
    simpleSound.Play();
}
```

## <a name="compiling-the-code"></a>コードのコンパイル
 この例で必要な要素は次のとおりです。

- ファイル名 `"c:\Windows\Media\chimes.wav"` を有効なファイル名に置き換えます。

- (C#) <xref:System.Media?displayProperty=nameWithType>名前空間への参照。

## <a name="robust-programming"></a>信頼性の高いプログラミング
 ファイルの操作は、適切な構造の例外処理ブロックで囲む必要があります。

 次の条件を満たす場合は、例外が発生する可能性があります。

- パス名が不適切である場合。 たとえば、不正な文字が含まれている場合や、空白だけの場合などがその例です (<xref:System.ArgumentException> クラス)。

- パスが読み取り専用である場合 (<xref:System.IO.IOException> クラス)。

- パス名が `null` である場合 (<xref:System.ArgumentNullException> クラス)。

- パス名が長すぎる場合 (<xref:System.IO.PathTooLongException> クラス)。

- パスが無効である場合 (<xref:System.IO.DirectoryNotFoundException> クラス)。

- パスはコロン ":" (<xref:System.NotSupportedException>クラス) にすぎません。

## <a name="net-framework-security"></a>.NET Framework セキュリティ
 ファイル名からファイルの内容を判断しないでください。 たとえば、`Form1.vb` というファイルは Visual Basic のソース ファイルではない可能性もあります。 アプリケーションでデータを使用する前に、入力をすべて検証してください。

## <a name="see-also"></a>関連項目

- <xref:System.Media.SoundPlayer>
- [方法: Windows フォーム内でサウンドを非同期的に読み込む](how-to-load-a-sound-asynchronously-within-a-windows-form.md)
