---
title: FolderBrowserDialog コンポーネントの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- FolderBrowserDialog
helpviewer_keywords:
- FolderBrowserDialog component [Windows Forms], about FolderBrowserDialog
- directories [Windows Forms], enabling browsing in applications
- folders [Windows Forms], enabling browsing in applications
ms.assetid: 796b622c-3ba9-4356-93bb-e217fc52f2c7
ms.openlocfilehash: cd89980ccad7e6c73094c1fb462d93cee8094959
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65210406"
---
# <a name="folderbrowserdialog-component-overview-windows-forms"></a>FolderBrowserDialog コンポーネントの概要 (Windows フォーム)

Windows フォーム<xref:System.Windows.Forms.FolderBrowserDialog>コンポーネントは参照およびフォルダーの選択に使用するモーダル ダイアログ ボックス。 内から新しいフォルダーを作成することも、<xref:System.Windows.Forms.FolderBrowserDialog>コンポーネント。

> [!NOTE]
> 使用して、フォルダーではなくファイルを選択する、 [OpenFileDialog](openfiledialog-component-windows-forms.md)コンポーネント。

<xref:System.Windows.Forms.FolderBrowserDialog>を使用して実行時にコンポーネントが表示されます、<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>メソッド。 設定、<xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A>プロパティを最上位のフォルダーと、ダイアログ ボックスのツリー ビュー内に表示されるすべてのサブフォルダーを確認します。 ダイアログ ボックスが表示されると、使用できます、<xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A>プロパティが選択されているフォルダーのパスを取得します。

フォームに追加されたとき、<xref:System.Windows.Forms.FolderBrowserDialog>コンポーネントは、Visual Studio での Windows フォーム デザイナーの下部にあるトレイに表示されます。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.FolderBrowserDialog>
- [方法: Windows フォーム FolderBrowserDialog コンポーネントを含むフォルダーを選択します。](how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component.md)
- [FolderBrowserDialog コンポーネント](folderbrowserdialog-component-windows-forms.md)
