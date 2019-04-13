---
title: '方法: 特定のデータ形式でデータを取得する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drag-and-drop [WPF], retrieving data
- DataFormats class [WPF], retrieving data
- DataObject class [WPF], retrieving data
ms.assetid: a625acf3-1144-44cd-add7-456aefc3859f
ms.openlocfilehash: b3ec1b8fa873fd449956912e9e77e98b0362cb0e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080021"
---
# <a name="how-to-retrieve-data-in-a-particular-data-format"></a>方法: 特定のデータ形式でデータを取得する
次の例では、指定された形式でデータ オブジェクトからデータを取得する方法を示します。  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 次のコード例を使用して、<xref:System.Windows.DataObject.GetDataPresent%28System.String%29>を最初に指定されたデータが書式設定を確認するオーバー ロードは (ネイティブまたは自動変換を)、例を使用してデータを取得する指定の形式を使用できる場合、<xref:System.Windows.DataObject.GetData%28System.String%29>メソッド。  
  
### <a name="code"></a>コード  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 次のコード例を使用して、<xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29>オーバー ロードを最初に指定したデータ形式が使用可能なネイティブを確認する (自動変換できるデータ形式はフィルターされます) 例では、が、を使用して、データを取得する指定の形式を使用できる場合<xref:System.Windows.DataObject.GetData%28System.String%29>。メソッド。  
  
### <a name="code"></a>コード  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat_Native](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat_native)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat_Native](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat_native)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.IDataObject>
- [ドラッグ アンド ドロップの概要](drag-and-drop-overview.md)
