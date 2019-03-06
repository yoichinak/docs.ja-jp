---
title: '方法: 取得し、アプリケーションのメイン ウィンドウの設定'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- windows objects [WPF], setting
- setting windows objects [WPF]
- windows objects [WPF], getting
- getting windows objects [WPF]
ms.assetid: ec902bc4-4a59-46f5-8ec1-963b46789356
ms.openlocfilehash: ea8333aa82f1159afb438215940ee1e7c2605e96
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373557"
---
# <a name="how-to-get-and-set-the-main-application-window"></a>方法: 取得し、アプリケーションのメイン ウィンドウの設定
この例では、取得し、アプリケーションのメイン ウィンドウを設定する方法を示します。  
  
## <a name="example"></a>例  
 最初の<xref:System.Windows.Window>内で、Windows Presentation Foundation (WPF) アプリケーションはによって自動的に設定がインスタンス化される<xref:System.Windows.Application>メイン アプリケーション ウィンドウとして。 最初の<xref:System.Windows.Window>インスタンス化は、通常、スタートアップとして指定されているウィンドウをある[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)](を参照してください<xref:System.Windows.Application.StartupUri%2A>)。  
  
 最初の<xref:System.Windows.Window>コードを使用してインスタンス可能性があります。 1 つの例では、次のように、アプリケーションの起動時にウィンドウを開いては。  
  
 [!code-csharp[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/App.xaml.cs#firstwindowusingcodecodebehind)]
 [!code-vb[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/application.xaml.vb#firstwindowusingcodecodebehind)]  
  
 場合によっては、1 つ目のインスタンス化<xref:System.Windows.Window>が実際には、アプリケーションのメイン ウィンドウなど、スプラッシュ スクリーン。 この場合は、次のようなマークアップを使用して、メイン アプリケーション ウィンドウを指定できます。  
  
 [!code-xaml[ApplicationMainWindowSnippets#SetApplicationMainWindowXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/ApplicationMainWindowSnippets/XAML/App.xaml#setapplicationmainwindowxaml)]  
  
 メイン ウィンドウが自動または手動で指定されているかどうか、メイン ウィンドウから取得できます<xref:System.Windows.Application.MainWindow%2A>次のように、次のコードを使用します。  
  
 [!code-csharp[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationMainWindowSnippets/CSharp/App.xaml.cs#getapplicationmainwindowcode)]
 [!code-vb[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationMainWindowSnippets/visualbasic/application.xaml.vb#getapplicationmainwindowcode)]
