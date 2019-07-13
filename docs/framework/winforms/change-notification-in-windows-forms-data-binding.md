---
title: Windows フォーム データ バインディングの変更通知
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, data binding
- Windows Forms, adding change notification for data binding
ms.assetid: b5b10f90-0585-41d9-a377-409835262a92
ms.openlocfilehash: b4a70f96ad256b22ce0d933a633475161160e5a4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665855"
---
# <a name="change-notification-in-windows-forms-data-binding"></a>Windows フォーム データ バインディングの変更通知
Windows フォーム データ バインドの最も重要な概念の 1 つは*変更通知*します。 いることを確認、データ ソースとバインドされたコントロール常に最新のデータ、データ バインディングの変更通知を追加する必要があります。 具体的には、バインドされたコントロールがそのデータ ソースに加えられた変更の通知を受け取ることを保証して、データ ソースは、コントロールのバインド プロパティに加えられた変更の通知されます。  
  
 データ バインディングの種類に応じて、変更通知のさまざまな種類があります。  
  
- 1 つのコントロールのプロパティがオブジェクトの 1 つのインスタンスにバインドされている単純なバインディング。  
  
- 一覧内の項目のプロパティまたはコントロール プロパティにバインドされている 1 つのコントロールのプロパティを含めることができますリストベースのバインドは、オブジェクトの一覧にバインドされます。  
  
 さらに場合に、データ バインドを使用する Windows フォーム コントロールを作成するには、適用、 *PropertyName*にコントロールのバインドされたプロパティに対する変更が反映されるように、コントロールにパターンを変更しますデータ ソース。  
  
## <a name="change-notification-for-simple-binding"></a>単純なバインディングの変更通知  
 単純バインディングは、バインドされたプロパティの値が変更されたときに、ビジネス オブジェクトは変更通知を提供する必要があります。 公開することでこれを行う、 *PropertyName*Changed イベントのビジネス オブジェクトと、ビジネス オブジェクトがバインドされたコントロールに各プロパティを<xref:System.Windows.Forms.BindingSource>またはビジネス オブジェクトが実装する推奨される方法<xref:System.ComponentModel.INotifyPropertyChanged>インターフェイスと発生させ、<xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged>イベント プロパティの値が変更されたとき。 詳細については、「[方法 :INotifyPropertyChanged インターフェイスを実装](how-to-implement-the-inotifypropertychanged-interface.md)します。 実装するオブジェクトを使用する場合、<xref:System.ComponentModel.INotifyPropertyChanged>インターフェイスがありませんを使用する、<xref:System.Windows.Forms.BindingSource>オブジェクトをコントロールにバインドを使用していますが、<xref:System.Windows.Forms.BindingSource>お勧めします。  
  
## <a name="change-notification-for-list-based-binding"></a>一覧ベースのバインディングの変更通知  
 Windows フォームは、プロパティの変更 (リスト項目プロパティの値を変更) を提供するバインドされたリストとリストが変更されましたによって異なります (項目が削除または、リストに追加) 情報をコントロールにバインドします。 したがって、データ バインディングを使用するリストを実装する必要があります、 <xref:System.ComponentModel.IBindingList>、両方の種類の変更通知を提供します。 <xref:System.ComponentModel.BindingList%601>の汎用実装は、<xref:System.ComponentModel.IBindingList>と Windows フォーム データ バインディングを使用するために設計されています。 作成することができます、<xref:System.ComponentModel.BindingList%601>を実装するビジネス オブジェクトの種類を格納している<xref:System.ComponentModel.INotifyPropertyChanged>一覧は自動的に変換し、<xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged>イベント<xref:System.ComponentModel.IBindingList.ListChanged>イベント。 バインドされたリストがない場合、<xref:System.ComponentModel.IBindingList>を使用してオブジェクトの一覧を Windows フォーム コントロールにバインドする必要があります、<xref:System.Windows.Forms.BindingSource>コンポーネント。 <xref:System.Windows.Forms.BindingSource>コンポーネントは、プロパティからリストへの変換と同様、<xref:System.ComponentModel.BindingList%601>します。 詳細については、「[方法 :BindingSource と INotifyPropertyChanged インターフェイスを使用して変更通知を発生させる](./controls/raise-change-notifications--bindingsource.md)します。  
  
## <a name="change-notification-for-custom-controls"></a>カスタム コントロールの変更通知  
 最後に、コントロールにある必要がありますを公開する、 *PropertyName*Changed イベントの各プロパティのデータにバインドするように設計します。 コントロール プロパティへの変更は、バインドされたデータ ソースに反映されます。 詳細については、「[方法 :PropertyNameChanged パターンを適用します。](how-to-apply-the-propertynamechanged-pattern.md)  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.ComponentModel.INotifyPropertyChanged>
- <xref:System.ComponentModel.BindingList%601>
- [Windows フォームでのデータ バインディング](windows-forms-data-binding.md)
- [Windows フォームがサポートするデータ ソース](data-sources-supported-by-windows-forms.md)
- [データ連結と Windows フォーム](data-binding-and-windows-forms.md)
