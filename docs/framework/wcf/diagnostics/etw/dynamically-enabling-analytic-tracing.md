---
title: 分析トレースの動的な有効化
ms.date: 03/30/2017
ms.assetid: 58b63cfc-307a-427d-b69d-9917ff9f44ac
ms.openlocfilehash: bea64ac9a9312d17b7f47e72a46d876552e20a12
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798096"
---
# <a name="dynamically-enabling-analytic-tracing"></a>分析トレースの動的な有効化
Windows オペレーティング システムに付属のツールでは、ETW (Event Tracing for Windows) を使用して、トレースを動的に有効化または無効化できます。 すべて[!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)]の Windows Communication Foundation (WCF) サービスでは、アプリケーションの web.config ファイルを変更したりサービスを再起動しなくても、分析トレースを動的に有効または無効にすることができます。 このため、トレース イベントを生成するアプリケーションに影響が生じません。  
  
 WCF トレースオプションは同様の方法で構成できます。 たとえば、アプリケーションに影響を与えずに、重大度レベルを **Error** から **Information** に変更できます。 これは、次のツールで実行できます。  
  
- **Logman** : トレース データを構成、制御、および照会するためのコマンド ライン ツールです。 詳細については、「 [Logman Create trace](https://go.microsoft.com/fwlink/?LinkId=165426) 」と「 [logman Update trace](https://go.microsoft.com/fwlink/?LinkId=165427)」を参照してください。  
  
- **EventViewer** : トレース結果を表示するための、Windows のグラフィカル管理ツールです。 詳細については、「 [WCF サービスと Windows イベントトレーシング](../../samples/wcf-services-and-event-tracing-for-windows.md)」および「[イベントビューアー](https://go.microsoft.com/fwlink/?LinkId=165428)」を参照してください。  
  
- **Perfmon** : カウンターを使用して、トレース カウンターおよびパフォーマンス トレースの効果を監視する、Windows のグラフィカル管理ツールです。 詳細については、「[データコレクターセットを手動で作成する](https://go.microsoft.com/fwlink/?LinkId=165429)」を参照してください。  
  
### <a name="keywords"></a>キーワード  
 <xref:System.ServiceModel.Activation.Configuration.ServiceModelActivationSectionGroup.Diagnostics%2A> クラスを使用するときには、通常、.NET Framework トレース メッセージが重大度レベル (エラー、警告、情報など) でフィルターされます。 ETW は、重大度レベルの概念をサポートしますが、キーワードを使用して、新しい柔軟なフィルター機構も追加されています。 キーワードは任意のテキスト値で、これによって、トレース イベントでそのイベントの意味に関する追加のコンテキストが提供されます。  
  
 WCF 分析トレースでは、各トレースイベントに2種類のキーワードがあります。 まず、各イベントには 1 つ以上のシナリオ キーワードがあります。 これらのキーワードは、そのイベントがサポートするシナリオを示します。 次の表に示すように、特定の目的に対応する 3 つのシナリオ キーワードがあります。 キーワードを使用したフィルター処理は、WCF サービスに支障をきたすことなく動的に変更できます。 このため、現在のトレース シナリオおよび収集するトレース情報の量を動的に変更できます。 たとえば、 `HealthMonitoring` を `Troubleshooting` に変更し、トレース イベントの詳細度を上げることができます。  
  
|キーワード|説明|  
|-------------|-----------------|  
|`HealthMonitoring`|サービスのアクティビティを監視できる、軽量の、最小限のトレース。|  
|`EndToEndMonitoring`|メッセージ フロー トレースのサポートに使用するイベント。|  
|`Troubleshooting`|WCF の機能拡張ポイントに関するより詳細なイベント。|  
  
 2番目のキーワードのグループは、.NET Framework のどのコンポーネントがイベントを生成したかを定義します。  
  
|キーワード|説明|  
|-------------|-----------------|  
|`UserEvents`|.NET Framework ではなく、ユーザーコードによって生成されるイベント。|  
|`ServiceModel`|WCF ランタイムによって生成されるイベント。|  
|`ServiceHost`|サービス ホストが生成するイベント。|  
|`WCFMessageLogging`|WCF メッセージログイベント。|  
  
## <a name="see-also"></a>関連項目

- [WCF サービスと Event Tracing for Windows](../../samples/wcf-services-and-event-tracing-for-windows.md)
