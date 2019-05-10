---
title: CLR ETW イベント
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: ef2b31c3-7426-43e7-9924-92339b96556d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a6b18f736743f1057641c20c7ef2bc544272f94f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64616659"
---
# <a name="clr-etw-events"></a>CLR ETW イベント
このセクションのトピックでは、Windows イベント トレーシング (ETW) イベントについて説明します。 各イベントは、キーワードとレベルに関連付けられています。詳細については、「[CLR ETW のキーワードとレベル](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)」トピックを参照してください。 CLR には、イベントのプロバイダーが 2 つあります。  
  
- ランタイム プロバイダー。有効になっているキーワードに応じてイベントを発生させます (キーワードとはイベントのカテゴリです)。 CLR ランタイム プロバイダーの GUID は e13c0d23-ccbc-4e12-931b-d9cc2eee27e4 です。  
  
- ランダウン プロバイダー。特殊な用途があります。 CLR ランダウン プロバイダーの GUID は a669021c-c450-4609-a035-5af59af4df18 です。  
  
 プロバイダーの詳細については、「[CLR ETW Providers](../../../docs/framework/performance/clr-etw-providers.md)」(CLR ETW プロバイダー) を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [ランタイム情報イベント](../../../docs/framework/performance/runtime-information-etw-events.md)  
 SKU、バージョン番号、アクティブ化の方法、起動時に使用されたコマンド ライン パラメーター、GUID (該当する場合) などのランタイムに関する情報をキャプチャします。  
  
 [Exception Thrown_V1 イベント](../../../docs/framework/performance/exception-thrown-v1-etw-event.md)  
 スローされる例外に関する情報をキャプチャします。  
  
 [競合イベント](../../../docs/framework/performance/contention-etw-events.md)  
 ランタイムが使用するモニター ロックまたはネイティブ ロックの競合に関する情報をキャプチャします。  
  
 [スレッド プール イベント](../../../docs/framework/performance/thread-pool-etw-events.md)  
 ワーカー スレッド プールと I/O スレッド プールに関する情報をキャプチャします。  
  
 [ローダー イベント](../../../docs/framework/performance/loader-etw-events.md)  
 アプリケーションのドメイン、アセンブリ、およびモジュールのロードとアンロードに関連する情報をキャプチャします。  
  
 [メソッド イベント](../../../docs/framework/performance/method-etw-events.md)  
 CLR メソッド シンボルの解決に関する情報をキャプチャします。  
  
 [ガベージ コレクション イベント](../../../docs/framework/performance/garbage-collection-etw-events.md)  
 診断とデバッグに役立つガベージ コレクションに関する情報をキャプチャします。  
  
 [JIT トレース イベント](../../../docs/framework/performance/jit-tracing-etw-events.md)  
 Just-In-Time (JIT) インライン展開と末尾呼び出しに関する情報をキャプチャします。  
  
 [相互運用イベント](../../../docs/framework/performance/interop-etw-events.md)  
 Microsoft intermediate language (MSIL) のスタブ生成とキャッシュに関する情報をキャプチャします。  
  
 [ARM のイベント](../../../docs/framework/performance/application-domain-resource-monitoring-arm-etw-events.md)  
 アプリケーション ドメインの状態に関する詳細な診断情報をキャプチャします。  
  
 [セキュリティ イベント](../../../docs/framework/performance/security-etw-events.md)  
 厳密な名前と Authenticode の検証に関する情報をキャプチャします。  
  
 [スタック イベント](../../../docs/framework/performance/stack-etw-event.md)  
 イベントが発生した後に、他のイベントでスタック トレースの生成に使用された情報をキャプチャします。  
  
## <a name="see-also"></a>関連項目

- [デバッグの向上およびパフォーマンス調整 ETW を](https://go.microsoft.com/fwlink/?LinkId=179696)
- [Windows のパフォーマンスに関するブログ](https://go.microsoft.com/fwlink/?LinkId=179509)
- [.NET Framework のログ記録の制御](../../../docs/framework/performance/controlling-logging.md)
- [CLR ETW プロバイダー](../../../docs/framework/performance/clr-etw-providers.md)
- [CLR ETW キーワードおよびレベル](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)
- [共通言語ランタイムの ETW イベント](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
