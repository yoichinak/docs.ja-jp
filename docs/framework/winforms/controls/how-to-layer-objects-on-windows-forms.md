---
title: '方法 : Windows フォーム上のオブジェクトをレイヤー化する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, layering
- controls [Windows Forms], layering
- z order
- controls [Windows Forms], positioning
- z-order
ms.assetid: 1acc4281-2976-4715-86f4-bda68134baaf
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5b8f6c00e70df94ae3a82c2c195fa781f0840a53
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458354"
---
# <a name="how-to-layer-objects-on-windows-forms"></a>方法: Windows フォーム上のオブジェクトをレイヤー化する

複雑なユーザーインターフェイスを作成する場合や、マルチドキュメントインターフェイス (MDI) フォームを使用する場合は、多くの場合、コントロールと子フォームの両方をレイヤー化することで、より複雑なユーザーインターフェイス (UI) を作成できます。 グループのコンテキスト内でコントロールとウィンドウを移動して追跡するには、 *z オーダー*を操作します。 Z オーダーは、フォームの z 軸 (深度) に沿ってフォーム上のコントロールを視覚的に重ねたものです。 Z オーダーの最上部にあるウィンドウは、他のすべてのウィンドウと重なっています。 他のすべてのウィンドウは、z オーダーの下部にあるウィンドウと重なっています。

## <a name="to-layer-controls-at-design-time"></a>デザイン時にコントロールをレイヤー化するには

1. Visual Studio で、レイヤー化するコントロールを選択します。

2. **[書式]** メニューの **[順序]** をクリックし、 **[前面へ移動]** または **[背面へ]** 移動 を選択します。

## <a name="to-layer-controls-programmatically"></a>プログラムによってコントロールをレイヤー化するには

<xref:System.Windows.Forms.Control.BringToFront%2A> および <xref:System.Windows.Forms.Control.SendToBack%2A> メソッドを使用して、コントロールの z オーダーを操作します。

たとえば、<xref:System.Windows.Forms.TextBox> コントロール、`txtFirstName`が別のコントロールの下にあり、そのコントロールを上に表示する場合は、次のコードを使用します。

```vb
txtFirstName.BringToFront()
```

```csharp
txtFirstName.BringToFront();
```

```cpp
txtFirstName->BringToFront();
```

> [!NOTE]
> Windows フォームは*コントロールの含有*をサポートします。 コントロールの含有では、<xref:System.Windows.Forms.GroupBox> コントロール内の <xref:System.Windows.Forms.RadioButton> コントロールの数など、多数のコントロールを含んでいるコントロール内に配置する必要があります。 次に、それを含んでいるコントロール内のコントロールをレイヤー化できます。 グループボックスを移動すると、コントロールがその中に含まれているため、コントロールも移動します。

## <a name="see-also"></a>関連項目

- [Windows フォーム コントロール](index.md)
- [各 Windows フォーム コントロールのラベル設定とショートカットの作成](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Windows フォームで使用するコントロール](controls-to-use-on-windows-forms.md)
- [Windows フォーム コントロールの機能別一覧](windows-forms-controls-by-function.md)
