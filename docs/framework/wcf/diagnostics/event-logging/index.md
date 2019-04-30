---
title: WCF のイベント ログ
ms.date: 03/30/2017
helpviewer_keywords:
- event logging [WCF]
ms.assetid: aac0530d-f44c-45a1-bada-e30e0677b41f
ms.openlocfilehash: 2dd4f82e8a100074850b21d298e91dc5dc15c59d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61999259"
---
# <a name="event-logging-in-wcf"></a>WCF のイベント ログ
Windows Communication Foundation (WCF) は、Windows イベント ログで内部イベントをトレースします。  
  
## <a name="viewing-event-logs"></a>イベント ログの表示  
 イベント ログは、既定で自動的に有効になります。無効にする方法はありません。 イベント ビューアーを使用して、WCF によって記録されたイベントを表示できます。 このツールを起動する をクリックして**開始**、 をクリックして**コントロール パネルの **、 をダブルクリックします**管理ツール**、し、ダブルクリック**イベント ビューアー**.  
  
### <a name="application-event-log"></a>アプリケーション イベント ログ  
 **アプリケーション イベント ログ**WCF によって生成されたイベントのほとんどが含まれています。 このエントリの多くは、アプリケーションに関して特定の機能を起動できなかったことを示しています。 その例は次のとおりです。  
  
- メッセージ ログ記録とトレース:WCF では、トレースとメッセージ ログが失敗したときに、イベント ログにイベントを書き込みます。 ただし、トレース エラーが発生するたびにイベントがトリガーされるわけではありません。 イベント ログがトレース エラーで完全に指定されていることを防ぐためには、WCF は、このようなイベントを 10 分のブラック アウト期間を実装します。 これは、WCF では、イベント ログにトレース エラーを書き込む場合、しません。 ここでも少なくとも 10 分間を意味します。  
  
- 共有リスナー:WCF TCP ポート共有サービスは、開始に失敗したときにイベントを記録します。  
  
- [!INCLUDE[infocard](../../../../../includes/infocard-md.md)]:サービスの開始に失敗したときにイベントを記録します。  
  
- 起動エラーやクラッシュなど、重大なエラー イベント。  
  
- メッセージ ログが有効にします。メッセージのログ記録をオンにすると、イベント ログに記録します。 これには機密情報やアプリケーション固有の情報がメッセージのヘッダーや本文に記録されている可能性があることを管理者に知らせる目的があります。  
  
- `enableLoggingKnownPII` ファイルの `machineSettings` 要素で、`machine.config` 属性が設定されている場合、イベントはログに記録されます。 この属性は、コンピューター上で実行しているアプリケーションが、既知の個人を特定できる情報 (PII) をログに記録できるかどうかを指定します。  
  
- 特定のアプリケーションで PII ログを有効にするために、`logKnownPii` ファイルまたは `app.config` ファイルの `web.config` 属性が `true` に設定され、`enableLoggingKnownPII` ファイルの `machineSettings` 要素で、`machine.config` 属性が `false` に設定されている場合、イベントはログに記録されます。 また、`logKnownPii` と `enableLoggingKnownPII` の両方が `true` に設定されている場合、イベントはログに記録されます。 これらの構成設定の詳細については、の [セキュリティ] セクションを参照してください、[メッセージ ログの構成](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)トピック。  
  
### <a name="security-event-log"></a>セキュリティ イベント ログ  
 **セキュリティ イベント ログ**WCF によってログに記録されるセキュリティ監査イベントが含まれています。  
  
### <a name="system-event-log"></a>システム イベント ログ  
 WCF は記録されません。 何も、**システム イベント ログ**します。  
  
### <a name="event-log-entries"></a>イベント ログ エントリ  
 **ソース**イベントがログ エントリを生成するアセンブリの名前。  
  
 イベント ログ エントリの型によって、イベントの重大度がわかります。 各イベントは単一の型でなければなりません。アプリケーションがイベントをレポートする際には、そのイベントの型が示されます。 イベント ビューアーは、この型を使用して、ログのリスト ビューに表示するアイコンを決定します。 イベント ログ エントリで使用されるイベントの型については、「<xref:System.Diagnostics.EventLogEntryType>」を参照してください。  
  
 「詳細」をクリックすると、イベント ビューアでイベントを表示するときにイベント ビューアーが、インターネット経由で情報を送信可能性があります。 詳細については、イベント ビューアーのヘルプを参照してください。  
  
## <a name="see-also"></a>関連項目

- [管理と診断](../../../../../docs/framework/wcf/diagnostics/index.md)
- [イベント一覧](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
