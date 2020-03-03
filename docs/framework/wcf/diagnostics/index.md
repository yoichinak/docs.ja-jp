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
ms.openlocfilehash: dfe169cd6c8d9a643e90e98fc9f22bf116d4335f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795976"
---
# <a name="administration-and-diagnostics"></a>管理と診断
Windows Communication Foundation (WCF) には、アプリケーションのライフサイクルのさまざまな段階を監視するのに役立つ豊富な機能セットが用意されています。 たとえば、展開時に構成を使用してサービスとクライアントを設定できます。 WCF には、アプリケーションのパフォーマンスを測定するのに役立つ、多数のパフォーマンスカウンターが用意されています。 WCF では、WCF Windows Management Instrumentation (WMI) プロバイダーを介して実行時にサービスの検査データを公開することもできます。 アプリケーションにエラーが発生したり、適切に動作しなくなったりした場合は、イベント ログを使用して、何か重大なことが発生していないかを確認できます。 メッセージ ログとトレースを使用して、アプリケーションでどのようなイベントが発生しているのかをエンドツーエンドで確認することもできます。 これらの機能により、開発者と IT プロフェッショナルは、正常に動作していないときに WCF アプリケーションのトラブルシューティングを行うことができます。  
  
> [!NOTE]
> 特定の詳細情報を含まないエラーを受信している場合は`includeExceptionDetailInFaults` 、 [ \<servicedebug >](../../configure-apps/file-schema/wcf/servicedebug.md)構成要素の属性を有効にする必要があります。 これにより、WCF は例外の詳細をクライアントに送信するように指示します。これにより、より高度な診断を必要とせずに、多くの一般的な問題を検出できます。 詳細については、「[エラーの送受信](../sending-and-receiving-faults.md)」を参照してください。  
  
## <a name="diagnostics-features-provided-by-wcf"></a>WCF に用意された診断機能  
 WCF には、次の診断機能が用意されています。  
  
- エンド ツー エンドのトレースは、デバッガーを使用せずにアプリケーションのトラブルシューティングを行うためのインストルメンテーション データを提供します。 WCF は、プロセスマイルストーンのトレースとエラーメッセージを出力します。 これには、チャネル ファクトリのオープンやサービス ホストによるメッセージの送受信が含まれます。 実行中のアプリケーションに対してトレースを有効にすると、その進行状況を監視できます。 詳細については、「[トレース](./tracing/index.md)」を参照してください。 トレースを使用してアプリケーションをデバッグする方法については、「[トレースを使用したアプリケーションのトラブルシューティング](./tracing/using-tracing-to-troubleshoot-your-application.md)」を参照してください。  
  
- メッセージ ログを使用すると、送信前と送信後の両方のメッセージを確認できます。 詳細については、「[メッセージログ](message-logging.md)」トピックを参照してください。  
  
- イベント トレースは、すべての重大な問題に関連するイベントをイベント ログに書き込みます。 後でイベント ビューアーを使用して異常を調査できます。 詳細については、[イベントログ](./event-logging/index.md)のトピックを参照してください。  
  
- パフォーマンス モニターを介して公開されるパフォーマンス カウンターを使用すると、アプリケーションとシステムの状態を監視できます。 詳細については、「[パフォーマンスカウンター](./performance-counters/index.md) 」を参照してください。  
  
- <xref:System.ServiceModel.Configuration> 名前空間を使用すると、構成ファイルを読み込んでサービスまたはクライアント エンドポイントを設定できます。 多数のコンピューターに更新を展開する必要がある場合は、オブジェクト モデルを使用して、さまざまなアプリケーションに対する変更をスクリプトで処理できます。 または、[構成エディターツール (svcconfigeditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md)を使用して、GUI ウィザードを使用して構成設定を編集することもできます。 詳細については、「[アプリケーションの構成](configuring-your-application.md)」を参照してください。  
  
- WMI を使用すると、コンピューター上でリッスン中のサービスと使用しているバインディングを確認できます。 詳細については、「 [Using Windows Management Instrumentation For Diagnostics](./wmi/index.md) 」トピックを参照してください。  
  
 また、wcf には、WCF アプリケーションの作成、配置、および管理を容易にする GUI およびコマンドラインツールも用意されています。 詳細については、「 [Windows Communication Foundation ツール](../tools.md)」を参照してください。 たとえば、[構成エディターツール (svcconfigeditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md)を使用して、XML を直接編集するのではなく、ウィザードを使用して WCF 構成設定を作成および編集できます。 また、[サービストレースビューアーツール (svctraceviewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md)を使用して、トレースメッセージを表示、グループ化、およびフィルター処理して、WCF サービスの問題を診断、修復、および検証することもできます。  
  
## <a name="see-also"></a>関連項目

- [アプリケーションの構成](configuring-your-application.md)
- [サービスの配置](deploying-services.md)
- [例外リファレンス](./exceptions-reference/index.md)
- [イベント ログ](./event-logging/index.md)
- [メッセージ ログ](message-logging.md)
- [構成エディター ツール (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md)
- [サービス トレース ビューアー ツール (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md)
- [ServiceModel 登録ツール](servicemodel-registration-tool.md)
- [トレース](./tracing/index.md)
- [診断用の WMI (Windows Management Instrumentation) の使用](./wmi/index.md)
- [パフォーマンス カウンター](./performance-counters/index.md)
- [Windows Communication Foundation ツール](../tools.md)
