---
title: 管理と診断
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, diagnostics
- Windows Communication Foundation, administration
- diagnostics [WCF]
- WCF, diagnostics
- administration [WCF]
- WCF, administration
ms.assetid: 34c81c08-0e0f-4fbc-9ae8-91948640ee43
ms.openlocfilehash: 8ec59ef316bfa19046082a8ee0a4052c69d5c323
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54508757"
---
# <a name="administration-and-diagnostics"></a>管理と診断
Windows Communication Foundation (WCF) は、アプリケーションのライフ サイクルのさまざまな段階を監視するのに役立つ機能の豊富なセットを提供します。 たとえば、展開時に構成を使用してサービスとクライアントを設定できます。 WCF には、多数アプリケーションのパフォーマンスの測定に役立つパフォーマンス カウンターにはが含まれています。 WCF には、WCF Windows Management Instrumentation (WMI) プロバイダーを介して実行時のサービスの検査データも公開します。 アプリケーションにエラーが発生したり、適切に動作しなくなったりした場合は、イベント ログを使用して、何か重大なことが発生していないかを確認できます。 メッセージ ログとトレースを使用して、アプリケーションでどのようなイベントが発生しているのかをエンドツーエンドで確認することもできます。 これらの機能は、開発者や IT プロフェッショナルの両方が正しく動作しない場合、WCF アプリケーションのトラブルシューティングに役立ちます。  
  
> [!NOTE]
>  有効にした具体的な詳細情報のないエラーが発生した場合、`includeExceptionDetailInFaults`の属性、 [ \<serviceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md)構成要素。 これより高度な診断を必要とせず、多くの一般的な問題を検出することができます WCF クライアントに例外の詳細を送信するように指示します。 詳細については、[Sending and Receiving Faults](../../../../docs/framework/wcf/sending-and-receiving-faults.md)を参照してください。  
  
## <a name="diagnostics-features-provided-by-wcf"></a>WCF に用意された診断機能  
 WCF には、次の診断機能が用意されています。  
  
-   エンド ツー エンドのトレースは、デバッガーを使用せずにアプリケーションのトラブルシューティングを行うためのインストルメンテーション データを提供します。 WCF では、エラー メッセージだけでなく、処理マイルス トーンのトレースを出力します。 これには、チャネル ファクトリのオープンやサービス ホストによるメッセージの送受信が含まれます。 実行中のアプリケーションに対してトレースを有効にすると、その進行状況を監視できます。 詳細については、次を参照してください。、[トレース](../../../../docs/framework/wcf/diagnostics/tracing/index.md)トピック。 どのようにできるトレースを使用するアプリケーションをデバッグする詳細については、次を参照してください。、[を使用して、アプリケーションのトラブルシューティングのトレース](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)トピック。  
  
-   メッセージ ログを使用すると、送信前と送信後の両方のメッセージを確認できます。 詳細については、次を参照してください。、[メッセージ ログ](../../../../docs/framework/wcf/diagnostics/message-logging.md)トピック。  
  
-   イベント トレースは、すべての重大な問題に関連するイベントをイベント ログに書き込みます。 後でイベント ビューアーを使用して異常を調査できます。 詳細については、次を参照してください。、[イベントがログ記録](../../../../docs/framework/wcf/diagnostics/event-logging/index.md)トピック。  
  
-   パフォーマンス モニターを介して公開されるパフォーマンス カウンターを使用すると、アプリケーションとシステムの状態を監視できます。 詳細については、次を参照してください。、[パフォーマンス カウンター](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)トピック。  
  
-   <xref:System.ServiceModel.Configuration> 名前空間を使用すると、構成ファイルを読み込んでサービスまたはクライアント エンドポイントを設定できます。 多数のコンピューターに更新を展開する必要がある場合は、オブジェクト モデルを使用して、さまざまなアプリケーションに対する変更をスクリプトで処理できます。 また、使用することができます、[構成エディター ツール (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) GUI ウィザードを使用して構成設定を編集します。 詳細については、次を参照してください。、 [、アプリケーションを構成する](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md)トピック。  
  
-   WMI を使用すると、コンピューター上でリッスン中のサービスと使用しているバインディングを確認できます。 詳細については、次を参照してください。、[診断用の Windows Management Instrumentation のを使用して](../../../../docs/framework/wcf/diagnostics/wmi/index.md)トピック。  
  
 WCF には、作成、展開、および WCF アプリケーションの管理を容易にいくつかの GUI とコマンド ライン ツールも用意されています。 詳細については、[Windows Communication Foundation ツール](../../../../docs/framework/wcf/tools.md)を参照してください。 たとえば、使用することができます、[構成エディター ツール (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)を作成して XML を直接編集する代わりに、ウィザードを使用して WCF 構成設定を編集します。 使用することも、[サービス トレース ビューアー ツール (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)を表示、グループ、および診断できるように、トレース メッセージをフィルター処理、修復、および WCF サービスで問題を確認します。  
  
## <a name="see-also"></a>関連項目
- [アプリケーションの構成](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md)
- [サービスの配置](../../../../docs/framework/wcf/diagnostics/deploying-services.md)
- [例外リファレンス](../../../../docs/framework/wcf/diagnostics/exceptions-reference/index.md)
- [イベント ログ](../../../../docs/framework/wcf/diagnostics/event-logging/index.md)
- [メッセージ ログ](../../../../docs/framework/wcf/diagnostics/message-logging.md)
- [構成エディター ツール (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)
- [サービス トレース ビューアー ツール (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
- [ServiceModel 登録ツール](../../../../docs/framework/wcf/diagnostics/servicemodel-registration-tool.md)
- [トレース](../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [診断用の WMI (Windows Management Instrumentation) の使用](../../../../docs/framework/wcf/diagnostics/wmi/index.md)
- [パフォーマンス カウンター](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
- [Windows Communication Foundation ツール](../../../../docs/framework/wcf/tools.md)
