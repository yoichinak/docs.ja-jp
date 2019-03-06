---
title: '方法: データ オブジェクトへ複数のデータ形式を格納する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataObject class [WPF], storing multiple formats
- DataFormats class [WPF], storing multiple formats
- drag-and-drop [WPF], storing multiple formats
ms.assetid: 941ace29-29c4-4c26-b75b-ea7d06aa0d69
ms.openlocfilehash: 9e261f3f00c28a0a15343e2691048ad022f1be7c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57351074"
---
# <a name="how-to-store-multiple-data-formats-in-a-data-object"></a>方法: データ オブジェクトへ複数のデータ形式を格納する
次の例は、使用する方法を示します、<xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29>メソッドを複数の形式でデータ オブジェクトにデータを追加します。  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
  
### <a name="code"></a>コード  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_storemultipleformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_storemultipleformats)]  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.IDataObject>
- [ドラッグ アンド ドロップの概要](drag-and-drop-overview.md)
