---
title: '方法 : Windows フォームにコントロールをロックする'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, locking
- controls [Windows Forms], locking
ms.assetid: 94efe0d2-c14e-4d14-b903-63ea9b07e290
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d157ddc8be4b5fa0057241b562e76b566e8dad99
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458345"
---
# <a name="how-to-lock-controls-to-windows-forms"></a>方法: Windows フォームにコントロールをロックする

Windows アプリケーションのユーザーインターフェイス (UI) をデザインするときに、コントロールが正しく配置されると、コントロールをロックすることができます。これにより、他のプロパティを設定するときに誤って移動したりサイズを変更したりすることはありません。

また、フォーム上のすべてのコントロールを一度にロックおよびロック解除することもできます。これは、多くのコントロールを持つフォームに便利です。または、個々のコントロールのロックを解除することもできます。 すべてのコントロールをフォーム上に配置したら、それらをすべて所定の場所にロックして、不適切な移動を防ぐことができます。

## <a name="to-lock-a-control"></a>コントロールをロックするには

Visual Studio の **[プロパティ]** ウィンドウで、 **[Locked]** プロパティを選択し、 **[true]** を選択します。 (名前をダブルクリックすると、プロパティの設定が切り替わります)。

または、コントロールを右クリックし、 **[コントロールのロック]** を選択します。

> [!NOTE]
> コントロールをロックすると、デザイン画面上の新しいサイズまたは位置にドラッグできなくなります。 ただし、コントロールのサイズや位置は、 **[プロパティ]** ウィンドウまたはコードで変更することもできます。

## <a name="to-lock-all-the-controls-on-a-form"></a>フォーム上のすべてのコントロールをロックするには

**[書式]** メニューの **[コントロールのロック]** をクリックします。

> [!NOTE]
> フォームがコントロールであるため、このコマンドはフォームのサイズもロックします。

## <a name="to-unlock-all-locked-controls-on-a-form"></a>フォーム上のロックされているすべてのコントロールのロックを解除するには

**[書式]** メニューの **[コントロールのロック]** をクリックします。

フォーム上の以前にロックされていたすべてのコントロールのロックが解除されます。

## <a name="to-unlock-locked-controls-individually"></a>ロックされたコントロールを個別にロック解除するには

**[プロパティ]** ウィンドウで、 **[Locked]** プロパティを選択し、 **[false]** を選択します。 (名前をダブルクリックすると、プロパティの設定が切り替わります)。

## <a name="see-also"></a>関連項目

- [Windows フォーム コントロール](index.md)
- [各 Windows フォーム コントロールのラベル設定とショートカットの作成](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Windows フォームで使用するコントロール](controls-to-use-on-windows-forms.md)
- [Windows フォーム コントロールの機能別一覧](windows-forms-controls-by-function.md)
