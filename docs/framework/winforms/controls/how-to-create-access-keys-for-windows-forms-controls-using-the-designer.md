---
title: '方法: デザイナーを使用して Windows フォーム コントロールのアクセス キーを作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], access keys
- Button control [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- mnemonics [Windows Forms], adding to dialog box controls
- ampersand character in shortcut key
- Windows Forms controls, access keys
- examples [Windows Forms], controls
- Text property [Windows Forms], specifying access keys for controls
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
- ALT key
ms.assetid: 4c374c4c-4ca9-4a68-ac96-9dc3ab0f518a
ms.openlocfilehash: 01bed04483702ba2e62162b675aa1138bc1b0e01
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039523"
---
# <a name="how-to-create-access-keys-for-windows-forms-controls-using-the-designer"></a>方法: デザイナーを使用して Windows フォーム コントロールのアクセス キーを作成する
*アクセスキー*は、メニュー、メニュー項目、またはボタンなどのコントロールのラベルのテキスト内の下線付きの文字です。 これにより、ユーザーは ALT キーを定義済みのアクセスキーと組み合わせて押すことで、ボタンを "クリック" できます。 たとえば、ボタンがフォームを印刷するためのプロシージャを実行し、その`Text`プロパティが "print" に設定されている場合、文字 "p" の前にアンパサンド (&) を追加すると、実行時にボタンのテキストに文字 "p" が下線付きで表示されます。 ユーザーは、ALT + P キーを押して、ボタンに関連付けられているコマンドを実行できます。 フォーカスを受け取ることができないコントロールのアクセスキーを持つことはできません。

## <a name="to-create-an-access-key-for-a-control"></a>コントロールのアクセスキーを作成するには

1. **[プロパティ]** ウィンドウで、 `Text`プロパティを、アクセスキーにする文字の前にアンパサンド (&) を含む文字列に設定します。 たとえば、文字 "P" をアクセスキーとして設定するには、「 **& Print** 」と入力します。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Button>
- [方法: Windows フォームボタンのクリックに応答する](how-to-respond-to-windows-forms-button-clicks.md)
- [方法: Windows フォームコントロールによって表示されるテキストを設定する](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [各 Windows フォーム コントロールのラベル設定とショートカットの作成](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
