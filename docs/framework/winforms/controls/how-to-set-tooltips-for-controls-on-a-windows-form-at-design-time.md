---
title: '方法: デザイン時に Windows フォームのコントロールにツールヒントを設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], for controls
- examples [Windows Forms], tooltips
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
ms.openlocfilehash: 0d6725fc1a00826870e6400bffce63a1788e802c
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211683"
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a>方法: デザイン時に Windows フォーム上のコントロールのツールヒントを設定します。

設定することができます、<xref:System.Windows.Forms.ToolTip>コードまたは Visual Studio での Windows フォーム デザイナーでの文字列。 詳細については、<xref:System.Windows.Forms.ToolTip>コンポーネントを参照してください[ToolTip コンポーネントの概要](tooltip-component-overview-windows-forms.md)します。

## <a name="set-a-tooltip-programmatically"></a>ツールヒントをプログラムで設定します。

1. ツールヒントを表示するコントロールを追加します。

2. 使用して、<xref:System.Windows.Forms.ToolTip.SetToolTip%2A>のメソッド、<xref:System.Windows.Forms.ToolTip>コンポーネント。

    ```vb
    ' In this example, Button1 is the control to display the ToolTip.
    ToolTip1.SetToolTip(Button1, "Save changes")
    ```

    ```csharp
    // In this example, button1 is the control to display the ToolTip.
    toolTip1.SetToolTip(button1, "Save changes");
    ```

    ```cpp
    // In this example, button1 is the control to display the ToolTip.
    toolTip1->SetToolTip(button1, "Save changes");
    ```

## <a name="set-a-tooltip-in-the-designer"></a>デザイナーでツールヒントを設定します。

1. Visual Studio で、追加、<xref:System.Windows.Forms.ToolTip>コンポーネントをフォームにします。

2. ツールヒントを表示または、フォームに追加されるコントロールを選択します。

3. **プロパティ**ウィンドウで、設定、 **ToolTip1 のツールヒント**テキストの適切な文字列値。

### <a name="to-remove-a-tooltip-programmatically"></a>ツールヒントをプログラムで削除するには

1. 使用して、<xref:System.Windows.Forms.ToolTip.SetToolTip%2A>のメソッド、<xref:System.Windows.Forms.ToolTip>コンポーネント。

    ```vb
    ' In this example, Button1 is the control displaying the ToolTip.
    ToolTip1.SetToolTip(Button1, Nothing)
    ```

    ```csharp
    // In this example, button1 is the control displaying the ToolTip.
    toolTip1.SetToolTip(button1, null);
    ```

    ```cpp
    // In this example, button1 is the control displaying the ToolTip.
    toolTip1->SetToolTip(button1, NULL);
    ```

## <a name="remove-a-tooltip-in-the-designer"></a>デザイナーでツールヒントを削除します。

1. Visual Studio で、ツールヒントを表示するコントロールを選択します。

2. **プロパティ**ウィンドウ内のテキストを削除、 **ToolTip1 のツールヒント**します。

## <a name="see-also"></a>関連項目

- [ToolTip コンポーネントの概要](tooltip-component-overview-windows-forms.md)
- [方法: Windows フォームの ToolTip コンポーネントの遅延時間を変更します。](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
- [ToolTip コンポーネント](tooltip-component-windows-forms.md)
