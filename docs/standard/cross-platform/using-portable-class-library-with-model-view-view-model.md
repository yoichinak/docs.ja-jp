---
title: Model-View-View Model を利用した汎用性のあるクラス ライブラリの使用
ms.date: 07/18/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Portable Class Library [.NET Framework], and MVVM
- MVVM, and Portable Class Library
ms.assetid: 41a0b9f8-15a2-431a-bc35-e310b2953b03
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 445cf4178b90719f923b66a7778f60c1bc846766
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204976"
---
# <a name="using-portable-class-library-with-model-view-view-model"></a>Model-View-View Model を利用した汎用性のあるクラス ライブラリの使用
You can use the .NET Framework [Portable Class Library](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) to implement the Model-View-View Model (MVVM) pattern and share assemblies across multiple platforms.

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 MVVM is an application pattern that isolates the user interface from the underlying business logic. You can implement the model and view model classes in a Portable Class Library project in Visual Studio 2012, and then create views that are customized for different platforms. This approach enables you to write the data model and business logic only once, and use that code from .NET Framework, Silverlight, Windows Phone, and Windows 8.x Store apps, as shown in the following illustration.

 ![Shows the Portable Class Library with MVVM sharing assemblies across platforms.](./media/using-portable-class-library-with-model-view-view-model/mvvm-share-assemblies-across-platforms.png)

 This topic does not provide general information about the MVVM pattern. It only provides information about how to use Portable Class Library to implement MVVM. For more information about MVVM, see the [MVVM Quickstart Using the Prism Library 5.0 for WPF](https://docs.microsoft.com/previous-versions/msp-n-p/gg430857(v=pandp.40)).

## <a name="classes-that-support-mvvm"></a>Classes That Support MVVM
 When you target the .NET Framework 4.5, [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], Silverlight, or Windows Phone 7.5 for your Portable Class Library project, the following classes are available for implementing the MVVM pattern:

- <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> クラス

- <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> クラス

- <xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType> クラス

- <xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType> クラス

- <xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType> クラス

- <xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType> クラス

- <xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType> クラス

- <xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType> クラス

- <xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType> クラス

- <xref:System.Windows.Input.ICommand?displayProperty=nameWithType> クラス

- All classes in the <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType> namespace

## <a name="implementing-mvvm"></a>Implementing MVVM
 To implement MVVM, you typically create both the model and the view model in a Portable Class Library project, because a Portable Class Library project cannot reference a non-portable project. The model and view model can be in the same project or in separate projects. If you use separate projects, add a reference from the view model project to the model project.

 After you compile the model and view model projects, you reference those assemblies in the app that contains the view. If the view interacts only with the view model, you only have to reference the assembly that contains the view model.

### <a name="model"></a>モデル
 The following example shows a simplified model class that could reside in a Portable Class Library project.

 [!code-csharp[PortableClassLibraryMVVM#1](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customer.cs#1)]
 [!code-vb[PortableClassLibraryMVVM#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customer.vb#1)]

 The following example shows a simple way to populate, retrieve, and update the data in a Portable Class Library project. In a real app, you would retrieve the data from a source such as a Windows Communication Foundation (WCF) service.

 [!code-csharp[PortableClassLibraryMVVM#2](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customerrepository.cs#2)]
 [!code-vb[PortableClassLibraryMVVM#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerrepository.vb#2)]

### <a name="view-model"></a>View Model
 A base class for view models is frequently added when implementing the MVVM pattern. The following example shows a base class.

 [!code-csharp[PortableClassLibraryMVVM#3](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/viewmodelbase.cs#3)]
 [!code-vb[PortableClassLibraryMVVM#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/viewmodelbase.vb#3)]

 An implementation of the <xref:System.Windows.Input.ICommand> interface is frequently used with the MVVM pattern. <xref:System.Windows.Input.ICommand> インターフェイスを実装する例を次に示します。

 [!code-csharp[PortableClassLibraryMVVM#4](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/relaycommand.cs#4)]
 [!code-vb[PortableClassLibraryMVVM#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/relaycommand.vb#4)]

 The following example shows a simplified view model.

 [!code-csharp[PortableClassLibraryMVVM#5](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainpageviewmodel.cs#5)]
 [!code-vb[PortableClassLibraryMVVM#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerviewmodel.vb#5)]  
  
### <a name="view"></a>View  
 From a .NET Framework 4.5 app, Windows 8.x Store app, Silverlight-based app, or Windows Phone 7.5 app, you can reference the assembly that contains the model and view model projects.  You then create a view that interacts with the view model. The following example shows a simplified Windows Presentation Foundation (WPF) app that retrieves and updates data from the view model. You could create similar views in Silverlight, Windows Phone, or Windows 8.x Store apps.  
  
 [!code-xaml[PortableClassLibraryMVVM#6](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainwindow.xaml#6)]  
  
## <a name="see-also"></a>関連項目

- [ポータブル クラス ライブラリ](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)
