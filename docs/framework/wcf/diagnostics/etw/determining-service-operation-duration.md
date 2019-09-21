---
title: サービス操作の実行時間の確認
ms.date: 03/30/2017
ms.assetid: e8a93a2c-2c20-48b3-8986-57e90e9aa908
ms.openlocfilehash: 9bc38f40b22eca8278905440ee69af9f38b81a0d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798111"
---
# <a name="determining-service-operation-duration"></a>サービス操作の実行時間の確認
Windows Communication Foundation (WCF) アプリケーションで分析トレースが有効になっている場合、サービス操作の実行時間は、イベントログを調べることで簡単に確認できます。  ここでは、サービス操作の実行にかかる時間を確認する方法を示します。  
  
### <a name="determining-service-operation-execution-duration"></a>サービス操作の実行時間の確認  
  
1. **[開始]** 、 **[実行]** の順に`eventvwr.exe`クリックしてイベントビューアーを開き、「」と入力します。  
  
2. 分析トレースを有効にしていない場合は、 **[アプリケーションとサービスログ]** 、 **[Microsoft]** 、 **[Windows]** 、 **[アプリケーションサーバー-アプリケーション]** の順に展開します。 **[表示]** 、 **[分析およびデバッグログの表示]** を選択します。 **[分析]** を右クリックし、 **[ログを有効にする]** を選択します。 サービス操作が実行された後にトレースを表示できるように、イベント ビューアーを開いたままにしておきます。  
  
3. 次に、サービスプロジェクトと、そのサービスと対話するクライアントプロジェクトを含む WCF アプリケーションを開きます。  このようなアプリケーションを作成するには、[はじめにチュートリアル](../../getting-started-tutorial.md)に従ってください。  WCF サンプルがインストールされている場合は、チュートリアルで作成した完成したプロジェクトを含む[はじめに](../../samples/getting-started-sample.md)を開くことができます。  
  
4. **F5**キーを押して、サーバーアプリケーションを実行します。 **クライアントプロジェクトを**右クリックし、 **[デバッグ]** 、 **[新しいインスタンスを開始]** の順に選択して、クライアントアプリケーションを実行します。  
  
5. イベント ビューアーで、分析ログを更新し、イベント ID でイベントを並べ替えます。  イベント ID [214-OperationCompleted](214-operationcompleted.md)のイベントを探します。  これらのイベントは、完了した操作、およびその操作にかかった時間を示します。  次のイベントは、追加操作の時間を示しています。  
  
    ```Output  
    An OperationInvoker completed the call to the 'Add' method.  The method call duration was '3' ms.  
    ```
