---
title: '方法: メインアプリケーションウィンドウを取得および設定する'
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
ms.openlocfilehash: 5894761c4b6258cbf90d369a722ffc5abca51885
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582556"
---
# <a name="how-to-get-and-set-the-main-application-window"></a>方法: メインアプリケーションウィンドウを取得および設定する
この例では、メインアプリケーションウィンドウを取得して設定する方法を示します。  
  
## <a name="example"></a>例  
 Windows Presentation Foundation (WPF) アプリケーション内でインスタンス化される最初の <xref:System.Windows.Window> は、<xref:System.Windows.Application> によってメインアプリケーションウィンドウとして自動的に設定されます。 インスタンス化される最初の <xref:System.Windows.Window> は、通常、スタートアップ URI (uniform resource identifier) として指定されるウィンドウです (<xref:System.Windows.Application.StartupUri%2A> を参照)。  
  
 最初の <xref:System.Windows.Window> は、コードを使用してインスタンス化することもできます。 1つの例として、次のように、アプリケーションの起動時にウィンドウを開くことがあります。  
  
 [!code-csharp[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/App.xaml.cs#firstwindowusingcodecodebehind)]
 [!code-vb[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/application.xaml.vb#firstwindowusingcodecodebehind)]  
  
 場合によっては、最初にインスタンス化された <xref:System.Windows.Window> が、実際にはスプラッシュスクリーンなどのメインアプリケーションウィンドウではありません。 この場合、次のように、マークアップを使用してメインアプリケーションウィンドウを指定できます。  
  
 [!code-xaml[ApplicationMainWindowSnippets#SetApplicationMainWindowXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/ApplicationMainWindowSnippets/XAML/App.xaml#setapplicationmainwindowxaml)]  
  
 メインウィンドウを自動的に指定するか手動で指定するかにかかわらず、次のようなコードを使用して <xref:System.Windows.Application.MainWindow%2A> からメインウィンドウを取得できます。  
  
 [!code-csharp[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationMainWindowSnippets/CSharp/App.xaml.cs#getapplicationmainwindowcode)]
 [!code-vb[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationMainWindowSnippets/visualbasic/application.xaml.vb#getapplicationmainwindowcode)]
