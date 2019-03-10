---
title: '方法: INotifyPropertyChanged インターフェイスを実装します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- INotifyPropertyChanged interface [Windows Forms], implementing
ms.assetid: eac428af-b43b-46ac-80d9-1a5f88658725
ms.openlocfilehash: 51c0b1fa535921b7b33a16f55bdc8b76d6125e72
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57704090"
---
# <a name="how-to-implement-the-inotifypropertychanged-interface"></a>方法: INotifyPropertyChanged インターフェイスを実装します。
次のコード例は、実装する方法を示します、<xref:System.ComponentModel.INotifyPropertyChanged>インターフェイス。 Windows フォーム データ バインディングで使用されているビジネス オブジェクトでこのインターフェイスを実装します。 実装された場合、インターフェイスは、ビジネス オブジェクトでプロパティの変更をバインドされたコントロールに通信します。  
  
## <a name="example"></a>例  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>関連項目
- [方法: PropertyNameChanged パターンを適用します。](how-to-apply-the-propertynamechanged-pattern.md)
- [Windows フォームでのデータ バインディング](windows-forms-data-binding.md)
- [方法: BindingSource と INotifyPropertyChanged インターフェイスを使用して変更通知を発生させる](./controls/raise-change-notifications--bindingsource.md)
- [Windows フォーム データ バインドの変更通知](change-notification-in-windows-forms-data-binding.md)
