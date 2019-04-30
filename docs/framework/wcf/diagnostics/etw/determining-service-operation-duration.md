---
title: サービス操作の実行時間の確認
ms.date: 03/30/2017
ms.assetid: e8a93a2c-2c20-48b3-8986-57e90e9aa908
ms.openlocfilehash: fd7dec5784f50a0613b574822a31202a859b34c6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61999455"
---
# <a name="determining-service-operation-duration"></a>サービス操作の実行時間の確認
Windows Communication Foundation (WCF) アプリケーションの分析トレースが有効な場合、サービス操作の実行中は、イベント ログを調べることで簡単に決定されます。  ここでは、サービス操作の実行にかかる時間を確認する方法を示します。  
  
### <a name="determining-service-operation-execution-duration"></a>サービス操作の実行時間の確認  
  
1. クリックしてイベント ビューアーを開いて**開始**、**実行**、入力と`eventvwr.exe`します。  
  
2. 分析トレースを有効にしていない場合は展開**Applications and Services Logs**、 **Microsoft**、 **Windows**、**アプリケーション サーバー-アプリケーション**. 選択**ビュー**、 **分析およびデバッグ ログ**します。 右クリック**分析**選択**ログの有効化**します。 サービス操作が実行された後にトレースを表示できるように、イベント ビューアーを開いたままにしておきます。  
  
3. 次に、サービス プロジェクトとそのサービスと対話するクライアント プロジェクトを含む WCF アプリケーションを開きます。  次でこのようなアプリケーションを作成することができます、[チュートリアル入門](../../../../../docs/framework/wcf/getting-started-tutorial.md)します。  WCF サンプルをインストールした場合は、開く、 [Getting Started](../../../../../docs/framework/wcf/samples/getting-started-sample.md)を含む、完成したプロジェクトのチュートリアルで作成します。  
  
4. キーを押してサーバー アプリケーションを実行します。 **F5**します。 右クリックし、クライアント アプリケーションを実行、**クライアント**プロジェクトと選択**デバッグ**、**新しいインスタンスを開始**します。  
  
5. イベント ビューアーで、分析ログを更新し、イベント ID でイベントを並べ替えます。  イベント ID を持つイベントを探します[214 - OperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/214-operationcompleted.md)します。  これらのイベントは、完了した操作、およびその操作にかかった時間を示します。  次のイベントは、追加操作の時間を示しています。  
  
    ```Output  
    An OperationInvoker completed the call to the 'Add' method.  The method call duration was '3' ms.  
    ```
