---
title: '方法: INotifyPropertyChanged インターフェイスを実装する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- INotifyPropertyChanged interface [Windows Forms], implementing
ms.assetid: eac428af-b43b-46ac-80d9-1a5f88658725
ms.openlocfilehash: cfdfb22fd854a8f630243e0f612761c71cb778d8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225600"
---
# <a name="how-to-implement-the-inotifypropertychanged-interface"></a>方法: INotifyPropertyChanged インターフェイスを実装する
次のコード例は、実装する方法を示します、<xref:System.ComponentModel.INotifyPropertyChanged>インターフェイス。 Windows フォーム データ バインディングで使用されているビジネス オブジェクトでこのインターフェイスを実装します。 実装された場合、インターフェイスは、ビジネス オブジェクトでプロパティの変更をバインドされたコントロールに通信します。  
  
## <a name="example"></a>例  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>関連項目

- [方法: PropertyNameChanged パターンを適用する](how-to-apply-the-propertynamechanged-pattern.md)
- [Windows フォームでのデータ バインディング](windows-forms-data-binding.md)
- [方法: BindingSource と INotifyPropertyChanged の各インターフェイスを使用して変更通知を発生させる](./controls/raise-change-notifications--bindingsource.md)
- [Windows フォーム データ バインディングの変更通知](change-notification-in-windows-forms-data-binding.md)
