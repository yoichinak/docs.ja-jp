---
title: '方法: ファイル ダイアログ ボックスにカスタム プレースを追加します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Custom Place to dialog box
- adding Custom Place to dialog box
- CustomPlaces collection
ms.assetid: 63f6469b-59cd-40f6-9e61-8b5831856780
ms.openlocfilehash: d9c1373a16f7d62c2933e01e513478fc6c9866d2
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57721880"
---
# <a name="how-to-add-a-custom-place-to-a-file-dialog-box"></a>方法: ファイル ダイアログ ボックスにカスタム プレースを追加します。
[!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] の既定の 開く] ダイアログ ボックスと 保存] ダイアログ ボックスには、左側に **[お気に入りリンク]** というタイトルの領域があります。 この領域にはカスタム プレイスという名称が付いています。 <xref:System.Windows.Forms.OpenFileDialog>と<xref:System.Windows.Forms.SaveFileDialog>クラスを使用すると、フォルダーを追加する、<xref:System.Windows.Forms.FileDialog.CustomPlaces%2A>コレクション。  
  
> [!NOTE]
>  カスタムの場所に表示するために、<xref:System.Windows.Forms.OpenFileDialog>または<xref:System.Windows.Forms.SaveFileDialog>、<xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A>にプロパティを設定する必要があります`true`(既定)。  
  
### <a name="to-add-a-custom-place-to-a-file-dialog-box"></a>ファイル ダイアログ ボックスにカスタム プレイスを追加するには  
  
-   パスを既知のフォルダー GUID を使用して、追加、または<xref:System.Windows.Forms.FileDialogCustomPlace>オブジェクトを<xref:System.Windows.Forms.FileDialog.CustomPlaces%2A>ダイアログ ボックスのコレクション。  
  
     次のコード例は、パスを追加する方法を示しています。  
  
    ```vb  
    OpenFileDialog1.CustomPlaces.Add("C:\MyCustomPlace")  
    ```  
  
    ```csharp  
    openFileDialog1.CustomPlaces.Add("C:\\MyCustomPlace");  
    ```  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.FileDialog>
- <xref:System.Windows.Forms.FileDialogCustomPlacesCollection.Add%2A?displayProperty=nameWithType>
- [ファイル ダイアログ ボックスのカスタム プレイス用既知のフォルダー GUID](known-folder-guids-for-file-dialog-custom-places.md)
