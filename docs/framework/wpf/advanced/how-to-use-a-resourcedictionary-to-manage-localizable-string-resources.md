---
title: '方法: ResourceDictionary を使用してローカライズ可能な文字列リソースを管理する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- resources [WPF], packaging string resources
- packaging string resources [WPF]
- ResourceDictionary [WPF]
- localization [WPF], packaging string resources
ms.assetid: 19e7d9a5-20df-4ad3-b157-fe6515902e5e
ms.openlocfilehash: e28086d8c97070b854ebdea35fe347c64c5cd7ac
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377938"
---
# <a name="how-to-use-a-resourcedictionary-to-manage-localizable-string-resources"></a>方法: ResourceDictionary を使用してローカライズ可能な文字列リソースを管理する
この例は、使用する方法を示します、 <xref:System.Windows.ResourceDictionary> Windows Presentation Foundation (WPF) アプリケーションのローカライズ可能な文字列リソースをパッケージ化します。  
  
### <a name="to-use-a-resourcedictionary-to-manage-localizable-string-resources"></a>ResourceDictionary を使用してローカライズ可能な文字列リソースを管理するには  
  
1.  作成、<xref:System.Windows.ResourceDictionary>にローカライズする文字列を格納しています。 次のコードは一例を示しています。  
  
     [!code-xaml[StringLocalizationSample#StringResourceDictionary](~/samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/StringResources.xaml#stringresourcedictionary)]  
  
     このコードでは、文字列リソースを定義します。 `localizedMessage`、型の<xref:System.String>、から、 <xref:System> mscorlib.dll に名前空間。  
  
2.  追加、<xref:System.Windows.ResourceDictionary>アプリケーションには、次のコードを使用します。  
  
     [!code-xaml[StringLocalizationSample#ReferencingStringResourceDictionary](~/samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/App.xaml#referencingstringresourcedictionary)]  
  
3.  マークアップの文字列リソースを使用して、使用して[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]次のようにします。  
  
     [!code-xaml[StringLocalizationSample#GetLocalizedResourceFromMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml#getlocalizedresourcefrommarkup)]  
  
4.  次のようなコードを使用して、コードビハインドから文字列リソースを使用します。  
  
     [!code-csharp[StringLocalizationSample#GetLocalizedResourceFromCode](~/samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml.cs#getlocalizedresourcefromcode)]
     [!code-vb[StringLocalizationSample#GetLocalizedResourceFromCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StringLocalizationSample/VisualBasic/MainWindow.xaml.vb#getlocalizedresourcefromcode)]  
  
5.  アプリケーションをローカライズします。 詳細については、次を参照してください。[アプリケーションをローカライズする](how-to-localize-an-application.md)します。
