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
ms.openlocfilehash: 99b04060d4e7c14313655010dc4fbd5ce1c90487
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788675"
---
# <a name="how-to-persist-and-restore-application-scope-properties-across-application-sessions"></a>方法: アプリケーション セッション全体でアプリケーション スコープのプロパティを永続化および復元する
この例では、アプリケーションがシャット ダウンするタイミングとアプリケーション スコープのプロパティ、アプリケーションが [次へ] の起動を復元する方法は、アプリケーション スコープのプロパティを永続化する方法を示します。  
  
## <a name="example"></a>例  
 アプリケーションでは、アプリケーション スコープのプロパティを永続化し、分離ストレージからそれを復元します。 分離ストレージは、アプリケーション ファイルへのアクセス許可なしで安全に使用できる保護されたストレージ領域です。  *App.xaml*ファイルで定義、`App_Startup`メソッドのハンドラーとして、<xref:System.Windows.Application.Startup?displayProperty=nameWithType>イベント、および`App_Exit`メソッドのハンドラーとして、<xref:System.Windows.Application.Exit?displayProperty=nameWithType>イベントを強調表示されている行の最初の例で示すようにします。 2 番目の例の一部を示しています、 *App.xaml.cs*と*App.xaml.vb*ファイルのコードを強調表示する、`App_Startup`メソッドで、アプリケーション スコープのプロパティ、および、復元`App_Exit`メソッドで、アプリケーション スコープのプロパティを保存します。

 [!code-xaml[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml?highlight=1-7)]
  
 [!code-csharp[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs?highlight=17-55)]
 [!code-vb[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb#persistrestoreappscopepropertiescodebehind1)]
