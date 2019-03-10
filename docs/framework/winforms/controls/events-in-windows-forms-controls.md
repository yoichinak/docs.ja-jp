---
title: Windows フォーム コントロールのイベント
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], custom controls (using code)
- custom controls [Windows Forms], events overview (using code)
ms.assetid: 7e3d1379-87aa-437c-afce-c99454eff30e
ms.openlocfilehash: dfbac71335615af52de3b5862c4058981f965654
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720797"
---
# <a name="events-in-windows-forms-controls"></a>Windows フォーム コントロールのイベント
Windows フォーム コントロールを継承から 60 を超えるイベント<xref:System.Windows.Forms.Control?displayProperty=nameWithType>します。 以下の<xref:System.Windows.Forms.Control.Paint>イベント、コントロールを描画する、ウィンドウの表示などに関連するイベント、<xref:System.Windows.Forms.Control.Resize>と<xref:System.Windows.Forms.Control.Layout>イベント、および低レベルのマウスとキーボード イベント。 一部の下位イベントは合成<xref:System.Windows.Forms.Control>などのセマンティック イベントに<xref:System.Windows.Forms.Control.Click>と<xref:System.Windows.Forms.Control.DoubleClick>します。 詳細については、継承されたイベントは、次を参照してください。<xref:System.Windows.Forms.Control>します。  
  
 継承されたイベントの機能をカスタム コントロールでオーバーライドする必要がある場合、デリゲートを結び付けるのではなく、継承された `On`*EventName* メソッドをオーバーライドします。 .NET Framework でのイベント モデルに詳しくない場合は、「[コンポーネントからのイベントの生成](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120))」を参照してください。  
  
## <a name="see-also"></a>関連項目
- [OnPaint メソッドのオーバーライド](overriding-the-onpaint-method.md)
- [ユーザーの入力の処理](handling-user-input.md)
- [イベントの定義](defining-an-event-in-windows-forms-controls.md)
- [イベント](../../../standard/events/index.md)
