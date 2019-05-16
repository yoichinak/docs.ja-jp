---
title: NotifyIcon コンポーネントの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- NotifyIcon
helpviewer_keywords:
- NotifyIcon component [Windows Forms], about NotifyIcon component
- system tray icons [Windows Forms], about system tray icons
- system tray icons [Windows Forms], using in Windows Forms
ms.assetid: 5b9189fa-d4ae-41a6-9b97-eb1f44bb1a69
ms.openlocfilehash: def109799ddfb25b6f56a4f18d52bb19f62842f5
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645706"
---
# <a name="notifyicon-component-overview-windows-forms"></a>NotifyIcon コンポーネントの概要 (Windows フォーム)

Windows フォームの <xref:System.Windows.Forms.NotifyIcon> コンポーネントは、通常、バックグラウンドで動作し、ユーザー インターフェイスに長時間表示されないプロセスのアイコンを表示する場合に使用されます。 たとえば、タスク バーの状態通知領域のアイコンをクリックしてアクセス可能なウイルス対策プログラムなどです。

## <a name="key-properties-of-notifyicons"></a>NotifyIcons のキー プロパティ

各 <xref:System.Windows.Forms.NotifyIcon> コンポーネントは、ステータス領域に 1 つのアイコンを表示します。 3 つのバック グラウンド プロセスがあり、それぞれのアイコンを表示する必要がある場合は、3 つの <xref:System.Windows.Forms.NotifyIcon> コンポーネントをフォームに追加する必要があります。 <xref:System.Windows.Forms.NotifyIcon> コンポーネントのキー プロパティは、<xref:System.Windows.Forms.NotifyIcon.Icon%2A> および <xref:System.Windows.Forms.NotifyIcon.Visible%2A> です。 <xref:System.Windows.Forms.NotifyIcon.Icon%2A> プロパティは、ステータス領域に表示されるアイコンを設定します。 アイコンを表示するために、<xref:System.Windows.Forms.NotifyIcon.Visible%2A> プロパティを `true` に設定する必要があります。

## <a name="notifyicons-options"></a>NotifyIcons オプション

バルーン ヒント、ショートカット メニュー、およびツールヒントを <xref:System.Windows.Forms.NotifyIcon> に関連付けて、ユーザーを支援できます。

<xref:System.Windows.Forms.NotifyIcon.ShowBalloonTip%2A> メソッドを呼び出して、バルーンヒントを表示する期間を指定することで、<xref:System.Windows.Forms.NotifyIcon> のバルーン ヒントを表示できます。 テキスト、アイコン、およびとバルーン ヒントのタイトルを、それぞれ <xref:System.Windows.Forms.NotifyIcon.BalloonTipText%2A>、<xref:System.Windows.Forms.NotifyIcon.BalloonTipIcon%2A>、および <xref:System.Windows.Forms.NotifyIcon.BalloonTipTitle%2A> を使用して指定できます。 <xref:System.Windows.Forms.NotifyIcon> コンポーネントには、ツールヒントとショートカット メニューも関連付けることができます。 詳細については、次を参照してください。 [ToolTip コンポーネントの概要](tooltip-component-overview-windows-forms.md)と[ContextMenu コンポーネントの概要](contextmenu-component-overview-windows-forms.md)します。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.NotifyIcon>
- [NotifyIcon コンポーネント](notifyicon-component-windows-forms.md)
