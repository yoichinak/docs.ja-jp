---
title: '方法: アプリケーション セッション全体でアプリケーション スコープのプロパティを永続化および復元する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application-scope properties [WPF], persisting
- persisting application-scope properties [WPF]
- properties [WPF], persisting
- restoring application-scope properties [WPF]
- properties [WPF], restoring
- application-scope properties [WPF], restoring
ms.assetid: 55d5904a-f444-4eb5-abd3-6bc74dd14226
ms.openlocfilehash: d9c2dda2745e7528902b6b1c4f46d17264d1a8d8
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666724"
---
# <a name="how-to-persist-and-restore-application-scope-properties-across-application-sessions"></a>方法: アプリケーション セッション全体でアプリケーション スコープのプロパティを永続化および復元する
この例では、アプリケーションのシャットダウン時にアプリケーションスコープのプロパティを永続化する方法と、アプリケーションの次回起動時にアプリケーションスコープのプロパティを復元する方法を示します。  
  
## <a name="example"></a>例  
 アプリケーションは、アプリケーションスコープのプロパティをに永続化し、分離ストレージから復元します。 分離ストレージは、ファイルアクセス許可のないアプリケーションで安全に使用できる、保護されたストレージ領域です。  *App.xaml*ファイル`App_Startup`は、 <xref:System.Windows.Application.Startup?displayProperty=nameWithType>イベントのハンドラーとしてメソッドを定義し`App_Exit` 、最初の例の強調表示され<xref:System.Windows.Application.Exit?displayProperty=nameWithType>た行に示すように、そのイベントのハンドラーとしてメソッドを定義します。 2番目の例は、 *App.xaml.cs*ファイルと app.xaml ファイルの一部を示して*います。* このメソッド`App_Startup`は、アプリケーションスコープのプロパティを`App_Exit`復元するメソッドのコードを強調表示し、メソッドを使用して、アプリケーションスコープを保存します。属性.

 [!code-xaml[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml?highlight=1-7)]
  
 [!code-csharp[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs?highlight=17-55)]
 [!code-vb[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb?highlight=14-45)]
