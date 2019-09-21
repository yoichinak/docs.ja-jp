---
title: '方法: よく使用する場所をファイル ダイアログ ボックスに追加する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Custom Place to dialog box
- adding Custom Place to dialog box
- CustomPlaces collection
ms.assetid: 63f6469b-59cd-40f6-9e61-8b5831856780
ms.openlocfilehash: 824c948fafd0a0995ad261389414d2d79918c8a1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916350"
---
# <a name="how-to-add-a-custom-place-to-a-file-dialog-box"></a>方法: よく使用する場所をファイル ダイアログ ボックスに追加する
[!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] の既定の 開く ダイアログ ボックスと 保存 ダイアログ ボックスには、左側に **[お気に入りリンク]** というタイトルの領域があります。 この領域にはカスタム プレイスという名称が付いています。 クラスとクラスを使用すると<xref:System.Windows.Forms.SaveFileDialog> 、フォルダーを<xref:System.Windows.Forms.FileDialog.CustomPlaces%2A>コレクションに追加できます。 <xref:System.Windows.Forms.OpenFileDialog>  
  
> [!NOTE]
> カスタムプレースを<xref:System.Windows.Forms.OpenFileDialog>またはに表示するに<xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A>は<xref:System.Windows.Forms.SaveFileDialog>、プロパティを (既定値) に`true`設定する必要があります。  
  
### <a name="to-add-a-custom-place-to-a-file-dialog-box"></a>ファイル ダイアログ ボックスにカスタム プレイスを追加するには  
  
- パスを既知のフォルダー GUID を使用して、追加、または<xref:System.Windows.Forms.FileDialogCustomPlace>オブジェクトを<xref:System.Windows.Forms.FileDialog.CustomPlaces%2A>ダイアログ ボックスのコレクション。  
  
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
