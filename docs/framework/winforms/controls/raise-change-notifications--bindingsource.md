---
title: '方法: BindingSource と INotifyPropertyChanged の各インターフェイスを使用して変更通知を発生させる'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- change notifications [Windows Forms], raising
- BindingSource component [Windows Forms], and IPropertyChange
- data sources [Windows Forms], detecting changes
- examples [Windows Forms], BindingSource component
- change notifications
- INotifyPropertyChanged interface [Windows Forms], using with BindingSource
- BindingSource component [Windows Forms], examples
ms.assetid: 7fa2cf51-c09f-4375-adf0-e36c5617f099
ms.openlocfilehash: 6a622e64076d2ed2a073dc0f0e55204d1767cfd7
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591821"
---
# <a name="how-to-raise-change-notifications-using-a-bindingsource-and-the-inotifypropertychanged-interface"></a>方法: BindingSource と INotifyPropertyChanged の各インターフェイスを使用して変更通知を発生させる
データ ソースに含まれる型が <xref:System.ComponentModel.INotifyPropertyChanged> インターフェイスを実装し、プロパティ値が変更されると <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> イベントを発生させる場合に、<xref:System.Windows.Forms.BindingSource> コンポーネントがデータ ソースの変更を自動的に検出します。 これは、データ ソースの値が変わると、<xref:System.Windows.Forms.BindingSource> にバインドされるコントロールが自動的に更新されるため便利です。  
  
> [!NOTE]
>  データ ソースが <xref:System.ComponentModel.INotifyPropertyChanged> を実装し、非同期操作を実行している場合は、バック グラウンド スレッド上のデータ ソースを変更しないようにします。 代わりに、バック グラウンド スレッド上のデータを読み取り、UI スレッドでリストにデータをマージする必要があります。  
  
## <a name="example"></a>例  
 次のコード例は、<xref:System.ComponentModel.INotifyPropertyChanged> インターフェイスの簡単な実装を示します。 <xref:System.Windows.Forms.BindingSource> が <xref:System.ComponentModel.INotifyPropertyChanged> 型の一覧にバインドされるときに、<xref:System.Windows.Forms.BindingSource> がバインドされたコントロールにデータ ソースの変更を自動的に渡す方法も示します。  
  
 `CallerMemberName` 属性を使用する場合、`NotifyPropertyChanged` メソッドの呼び出しが、文字列引数としてプロパティ名を指定する必要はありません。 詳細については、次を参照してください。[呼び出し元情報 (C#)](../../../csharp/programming-guide/concepts/caller-information.md)または[呼び出し元情報 (Visual Basic)](../../../visual-basic/programming-guide/concepts/caller-information.md)します。  
  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
- System、System.Data、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ComponentModel.INotifyPropertyChanged>
- [BindingSource コンポーネント](bindingsource-component.md)
- [方法: BindingSource ResetItem メソッドを使用して変更通知を発生させる](how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)
