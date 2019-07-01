---
title: ワークフロー ホスティングのオプション
ms.date: 03/30/2017
ms.assetid: 37bcd668-9c5c-4e7c-81da-a1f1b3a16514
ms.openlocfilehash: b0cd9748c28cd6206e1fedffc5772b2849462dba
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487359"
---
# <a name="workflow-hosting-options"></a>ワークフロー ホスティングのオプション
ほとんどの Windows Workflow Foundation (WF) のサンプルを使用して、ワークフロー コンソール アプリケーションでホストされているが、実際のワークフローにとって現実的なシナリオはありません。 実際のビジネス アプリケーション内のワークフローは永続的なプロセスの Windows サービスの作成で、developer、または IIS 7.0 や AppFabric などのサーバー アプリケーションによってホストされます。 これらの方法の違いを次に示します。  
  
## <a name="hosting-workflows-in-iis-with-windows-appfabric"></a>Windows AppFabric を使用した IIS でのワークフローのホスト  
 IIS と AppFabric は、ワークフローに推奨されるホストです。 AppFabric を使用したワークフローのホスト アプリケーションは Windows プロセス アクティブ化サービスで、これは IIS を介した HTTP への依存関係のみを解消します。  
  
## <a name="hosting-workflows-in-iis-alone"></a>IIS のみでのワークフローのホスト  
 管理と監視を実行中のアプリケーションの保守を容易にする AppFabric を使用した使用可能なツールがある、単独で IIS 7.0 の使用はお勧めできません。 ワークフローは、AppFabric への移行に関してインフラストラクチャ上の問題がある場合だけで IIS 7.0 でのみホストされている必要があります。  
  
> [!WARNING]
>  IIS 7.0 は、さまざまな理由から定期的にアプリケーション プールをリサイクルします。 アプリケーション プールがリサイクルされると、IIS は古いプールへのメッセージの受け取りを中止し、新しいアプリケーション プールをインスタンス化して新しい要求を受け取ります。 ワークフローには、応答の送信後の作業が引き続き発生する場合、IIS 7.0 は、実行されている作業の認識できなくなります、ホストのアプリケーション プールをリサイクルすることがあります。 これは、ワークフローが中断され、記録、追跡サービスの場合、 [1004 - WorkflowInstanceAborted](1004-workflowinstanceaborted.md)理由フィールドが空白のメッセージ。  
>   
>  永続化を使用する場合、ホストは、最後の永続性ポイントから、中止されたインスタンスを明示的に再開する必要があります。  
>   
>  AppFabric を使用する場合、永続化を使用すると、ワークフロー管理サービスは、最終的に、最後に成功した永続性ポイントからワークフローを再開します。 永続化を使用せず、ワークフローが要求/応答パターン以外の操作を実行している場合、ワークフローが中止されるとデータは失われます。  
  
## <a name="hosting-a-workflow-in-a-custom-windows-service"></a>カスタム Windows サービスでのワークフローのホスト  
 カスタム ワークフロー サービスを作成してワークフローをホストする場合、開発者は AppFabric に標準搭載されている多くの機能を複製する必要がありますが、カスタム機能をより柔軟に使用できるようになります。 このオプションは、AppFabric を選択できない場合にのみ検討してください。
