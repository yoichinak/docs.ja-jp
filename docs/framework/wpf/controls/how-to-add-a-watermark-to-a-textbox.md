---
title: '方法: TextBox へのウォーターマークの追加'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- displaying a background image inside a text box to aid user input [WPF]
- aid usability of a TextBox using a background image [WPF]
ms.assetid: df89bdd8-a0fb-45e0-b312-dd53332d01a8
ms.openlocfilehash: 5a2b48c6f580def98a47913c4909d0c57aca0974
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57359421"
---
# <a name="how-to-add-a-watermark-to-a-textbox"></a>方法: TextBox へのウォーターマークの追加
次の例では、使いやすさを支援する方法を示しています、<xref:System.Windows.Controls.TextBox>内での説明の背景イメージを表示することによって、<xref:System.Windows.Controls.TextBox>この時点で、イメージを削除するまで、ユーザーがテキストを入力します。 さらに、背景画像は、ユーザー入力を削除する場合、再び復元します。 次の図を参照してください。  
  
 ![背景イメージを含む TextBox](./media/editing-textbox-using-background-image.png "Editing_TextBox_using_background_image")  
  
> [!NOTE]
>  背景イメージがこの例ではなく、単に操作で使用される理由、<xref:System.Windows.Controls.TextBox.Text%2A>プロパティの<xref:System.Windows.Controls.TextBox>が背景画像はデータ バインドが妨げられないようにします。  
  
## <a name="example"></a>例  
 [!code-xaml[TextBoxMiscSnippets_snip#TextBoxBackgroundExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml#textboxbackgroundexamplewholepage)]  
  
 [!code-csharp[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml.cs#textboxbackgroundcodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/textbox_with_background_image.xaml.vb#textboxbackgroundcodeexamplewholepage)]  
  
## <a name="see-also"></a>関連項目
- [TextBox の概要](textbox-overview.md)
- [RichTextBox の概要](richtextbox-overview.md)
