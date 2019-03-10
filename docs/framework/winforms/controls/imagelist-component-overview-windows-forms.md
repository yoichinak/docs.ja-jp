---
title: ImageList コンポーネントの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- ImageList
helpviewer_keywords:
- collection controls [Windows Forms], images
- icon list control
- ImageList component [Windows Forms], about ImageList component
ms.assetid: 7e25d89b-5633-40c1-afc3-82e0e301ffa2
ms.openlocfilehash: 9869e647613ccf009954a5d65445947fbced40e7
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57709845"
---
# <a name="imagelist-component-overview-windows-forms"></a>ImageList コンポーネントの概要 (Windows フォーム)

Windows フォーム <xref:System.Windows.Forms.ImageList> コンポーネントは、コントロールで表示するイメージの保存に使用します。 イメージ リストでは、一貫性のある 1 つのイメージのカタログのコードを記述することができます。 たとえば、ボタンの <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> プロパティまたは <xref:System.Windows.Forms.ButtonBase.ImageKey%2A> プロパティを変更するだけで、<xref:System.Windows.Forms.Button> コントロールによって表示されるイメージを回転できます。 同じイメージのリストを複数のコントロールに関連付けることもできます。 たとえば、<xref:System.Windows.Forms.ListView> コントロールと <xref:System.Windows.Forms.TreeView> コントロールの両方を使用して同じファイルのリストを表示する場合、イメージのリストでファイルのアイコンを変更すると、新しいアイコンが両方のビューに表示されます。

## <a name="using-imagelist-with-controls"></a>コントロールでの ImageList の使用

`ImageList` プロパティを持つコントロール (<xref:System.Windows.Forms.ListView> コントロールの場合は <xref:System.Windows.Forms.ListView.SmallImageList%2A> プロパティと <xref:System.Windows.Forms.ListView.LargeImageList%2A> プロパティ) でイメージ リストを使用することができます。 イメージ リストに関連付けることができるコントロールは、<xref:System.Windows.Forms.ListView>、<xref:System.Windows.Forms.TreeView>、<xref:System.Windows.Forms.ToolBar>、<xref:System.Windows.Forms.TabControl>、<xref:System.Windows.Forms.Button>、<xref:System.Windows.Forms.CheckBox>、<xref:System.Windows.Forms.RadioButton>、および <xref:System.Windows.Forms.Label> の各コントロールです。 イメージ リストをコントロールに関連付けるには、コントロールの `ImageList` プロパティを <xref:System.Windows.Forms.ImageList> コンポーネントの名前に設定します。

## <a name="key-properties"></a>キー プロパティ

<xref:System.Windows.Forms.ImageList> コンポーネントのキー プロパティは <xref:System.Windows.Forms.ImageList.Images%2A> で、関連付けられたコントロールで使用される画像が含まれています。 各イメージは、そのインデックス値、またはそのキーを使用してアクセスできます。 <xref:System.Windows.Forms.ImageList.ColorDepth%2A> プロパティは、イメージをレンダリングする際の色の数を決定します。 イメージはすべて同じサイズで表示され、<xref:System.Windows.Forms.ImageList.ImageSize%2A> プロパティによって設定されます。 大きなイメージはサイズが合うように縮小されます。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.ImageList>
- [方法: 追加または削除のイメージを Windows フォームの ImageList コンポーネント](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)