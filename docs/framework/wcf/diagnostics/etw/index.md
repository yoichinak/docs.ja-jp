---
title: ETW を使用した分析トレース
ms.date: 03/30/2017
helpviewer_keywords:
- diagnostics [WCF], analytic tracing
- administration [WCF], analytic tracing
- analytic tracing [WCF]
ms.assetid: 1d518e47-a38d-41e8-93d7-8c3b361f6a56
ms.openlocfilehash: cff13439995d8a90da15b7afa15723f21574e35e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61962046"
---
# <a name="analytic-tracing-with-etw"></a>ETW を使用した分析トレース
Windows Communication Foundation (WCF) の分析トレースは、WCF サービスの実行中に診断情報をキャプチャする手段を提供します。 WCF 分析トレース イベントは、運用環境で WCF サービスのトラブルシューティングが可能に WCF スタック内のキー_ポイントで出力されます。 WCF サービスの分析トレースが影響を最小限製品サーバーのパフォーマンスにホストする[!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)]WCF サービスのようにこれらのイベントは Event Tracing for Windows (ETW) セッションに非常に効率的に生成されます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [分析トレースの概要](../../../../../docs/framework/wcf/diagnostics/etw/analytic-tracing-overview.md)  
 WCF 分析トレースがでどのように動作するかについて説明します。[!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)]します。  
  
 [分析トレースの動的な有効化](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md)  
 ETW を使用してトレースを動的に有効化または無効化する方法について説明します。  
  
 [メッセージ フローのトレースの構成](../../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md)  
 メッセージ フローのトレースを構成する方法について説明します。  
  
 [分析トレース イベント リファレンス](../../../../../docs/framework/wcf/diagnostics/etw/analytic-trace-event-reference.md)  
 イベント ID とそれらのイベント レベル、イベント メッセージ、およびキーワードを表で示します。  
  
## <a name="see-also"></a>関連項目

- [WCF サービスと Event Tracing for Windows](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)
- [Windows のイベント トレースへの追跡イベント](../../../../../docs/framework/windows-workflow-foundation/samples/tracking-events-into-event-tracing-in-windows.md)
