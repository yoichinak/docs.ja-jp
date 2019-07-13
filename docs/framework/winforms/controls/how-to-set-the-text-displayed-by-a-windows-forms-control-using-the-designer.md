---
title: '方法: Windows フォーム コントロールに表示するテキストをデザイナーで設定する'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], setting caption
- Windows Forms, setting the text displayed
ms.assetid: 9d18e0e0-f17f-4074-837d-e67ceeeaa89d
ms.openlocfilehash: 37ab3823a41cca2eeea550c90e92e90bc364c759
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/21/2019
ms.locfileid: "65960351"
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control-using-the-designer"></a>方法: Windows フォーム コントロールに表示するテキストをデザイナーで設定する

Windows フォーム コントロールは、通常、コントロールの主な機能に関連するいくつかのテキストを表示します。 たとえば、<xref:System.Windows.Forms.Button>コントロールには、通常、ボタンがクリックされたときに実行するアクションを示すキャプションが表示されます。 すべてのコントロールに対して、<xref:System.Windows.Forms.Control.Text%2A> プロパティを使用してテキストを設定または返すことができます。 <xref:System.Windows.Forms.Control.Font%2A> プロパティを使用して、フォントを変更することができます。

### <a name="to-set-the-text-and-font-with-the-designer"></a>テキストとデザイナーを使用したフォントを設定するには

1. [プロパティ] ウィンドウで次のように設定します。、<xref:System.Windows.Forms.Control.Text%2A>適切な文字列をコントロールのプロパティ。

     下線付きのショートカット キーを作成するアンパサンドが含まれています (&) は、ショートカット キーとなる文字の前にします。

2. [プロパティ] ウィンドウで、省略記号ボタンをクリックします。 (![。 Visual Studio の [プロパティ] ウィンドウで、省略記号ボタン (…)](./media/visual-studio-ellipsis-button.png)) 横に、<xref:System.Windows.Forms.Control.Font%2A>プロパティ。

     標準的なフォント ダイアログ ボックスで、フォント、フォント スタイル、サイズ、(取り消し線、下線) などの効果とスクリプトを選択します。

## <a name="see-also"></a>関連項目

- [方法: によって表示されるテキストを設定、Windows フォーム コントロール](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [フォントとテキストの使用](../advanced/using-fonts-and-text.md)
- [各 Windows フォーム コントロールのラベル設定とショートカットの作成](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
