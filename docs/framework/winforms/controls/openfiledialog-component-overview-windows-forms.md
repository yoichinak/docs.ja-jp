---
title: OpenFileDialog コンポーネントの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- OpenFileDialog
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], about OpenFileDialog
- Open File dialog box [Windows Forms], displaying in Windows Forms
ms.assetid: cd717300-46b6-4f82-8207-b218fa7fa407
ms.openlocfilehash: ec275a5923d332d23205c79442fa23bc6e402e3f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59147343"
---
# <a name="openfiledialog-component-overview-windows-forms"></a>OpenFileDialog コンポーネントの概要 (Windows フォーム)
Windows フォームの <xref:System.Windows.Forms.OpenFileDialog> コンポーネントは、事前構成済みのダイアログ ボックスです。 これは同じ**ファイルを開く** ダイアログ ボックスが、Windows オペレーティング システムによって公開されています。 これは、<xref:System.Windows.Forms.CommonDialog> クラスを継承しています。  
  
## <a name="using-this-component"></a>このコンポーネントを使用します。  
 簡単な解決策として、Windows ベースのアプリケーション内でこのコンポーネントを使用して、ファイル選択ダイアログ ボックスを構成する代わりにします。 Windows の標準のダイアログ ボックスを使用して、ユーザーがすぐに慣れる基本的な機能を持つアプリケーションを作成します。 ただし、時に使用して、<xref:System.Windows.Forms.OpenFileDialog>コンポーネント、独自のファイルを開くロジックを記述する必要があります。  
  
 使用して、<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>メソッド実行時にダイアログを表示します。 ユーザーで開くファイルを複数選択を有効にすることができます、<xref:System.Windows.Forms.OpenFileDialog.Multiselect%2A>プロパティ。 また、使用することができます、<xref:System.Windows.Forms.OpenFileDialog.ShowReadOnly%2A>プロパティのかどうか、ダイアログ ボックスでは読み取り専用チェック ボックスが表示されます。 <xref:System.Windows.Forms.OpenFileDialog.ReadOnlyChecked%2A>プロパティは読み取り専用のチェック ボックスがオンになっているかどうかを示します。 最後に、<xref:System.Windows.Forms.FileDialog.Filter%2A>プロパティ設定の現在のファイル名フィルターの文字列 ダイアログ ボックスで、"ファイルの種類 ボックスに表示される選択肢を決定します。  
  
 フォームに追加されたとき、<xref:System.Windows.Forms.OpenFileDialog>コンポーネント、Windows フォーム デザイナーの下部にあるトレイに表示されます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.OpenFileDialog>
- [OpenFileDialog コンポーネント](openfiledialog-component-windows-forms.md)
