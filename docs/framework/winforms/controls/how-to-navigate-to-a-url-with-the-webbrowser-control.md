---
title: '方法: WebBrowser コントロールで URL に移動する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- WebBrowser.Navigate
helpviewer_keywords:
- WebBrowser control [Windows Forms], examples
- URLs [Windows Forms], navigating to
- WebBrowser control [Windows Forms], navigating to URLs
- examples [Windows Forms], WebBrowser control
ms.assetid: b3ec38cb-f509-4d0b-bd79-9f3611259c62
ms.openlocfilehash: b6c1255fa17d91daaa73001fea04f26e73dba0ae
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015828"
---
# <a name="how-to-navigate-to-a-url-with-the-webbrowser-control"></a>方法: WebBrowser コントロールで URL に移動する
<xref:System.Windows.Forms.WebBrowser>コントロールを特定の URL に移動する方法を次のコード例に示します。

 新しいドキュメントが完全に読み込まれたことを確認する<xref:System.Windows.Forms.WebBrowser.DocumentCompleted>には、イベントを処理します。 このイベントのデモンストレーションについては[、「方法:WebBrowser コントロール](how-to-print-with-a-webbrowser-control.md)を使用して印刷します。

## <a name="example"></a>例

```vb
Me.webBrowser1.Navigate("http://www.microsoft.com")
```

```csharp
this.webBrowser1.Navigate("http://www.microsoft.com");
```

## <a name="compiling-the-code"></a>コードのコンパイル
 この例で必要な要素は次のとおりです。

- `webBrowser1` という名前の <xref:System.Windows.Forms.WebBrowser> コントロール。

- `System` アセンブリおよび `System.Windows.Forms` アセンブリへの参照。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.DocumentCompleted?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigated?displayProperty=nameWithType>
- [WebBrowser コントロール](webbrowser-control-windows-forms.md)
- [方法: WebBrowser コントロールを使用して印刷する](how-to-print-with-a-webbrowser-control.md)
