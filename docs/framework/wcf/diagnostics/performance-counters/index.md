---
title: WCF パフォーマンス カウンター
ms.date: 03/30/2017
helpviewer_keywords:
- performance counters [WCF]
ms.assetid: f559b2bd-ed83-4988-97a1-e88f06646609
ms.openlocfilehash: 73bb02379308fbfe507137e61ac8d84e6b9760b4
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395888"
---
# <a name="wcf-performance-counters"></a>WCF パフォーマンス カウンター
Windows Communication Foundation (WCF) には、アプリケーションのパフォーマンスを測定するのに役立つ多数のパフォーマンスカウンターが含まれています。  
  
## <a name="enabling-performance-counters"></a>パフォーマンス カウンターの有効化  
 Wcf サービスのパフォーマンスカウンターは、wcf サービスの app.config 構成ファイルを使用して次のように有効にすることができます。  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <diagnostics performanceCounters="All" />  
    </system.serviceModel>  
</configuration>  
```  
  
 特定の種類のパフォーマンス カウンターを有効にするよう `performanceCounters` 属性を設定できます。 有効な値は、次のとおりです。  
  
- All : すべてのカテゴリ カウンター (ServiceModelService、ServiceModelEndpoint、ServiceModelOperation) を有効にします。  
  
- ServiceOnly : ServiceModelService カテゴリ カウンターのみを有効にします。 これは既定値です。  
  
- Off : ServiceModel* パフォーマンス カウンターを無効にします。  
  
 すべての WCF アプリケーションに対してパフォーマンスカウンターを有効にする場合は、machine.config ファイルに構成設定を配置できます。  コンピューターのパフォーマンスカウンター用に十分なメモリを構成する方法の詳細については、後述の「**パフォーマンスカウンターのメモリサイズの増加**」セクションを参照してください。  
  
 カスタム操作の呼び出し元などの WCF 機能拡張ポイントを使用する場合は、独自のパフォーマンスカウンターも生成する必要があります。 これは、機能拡張ポイントを実装すると、WCF が標準のパフォーマンスカウンターデータを既定のパスに出力しなくなる可能性があるためです。 手動パフォーマンス カウンターのサポートを実装しない場合、予測したパフォーマンス カウンター データが得られない場合があります。  
  
 また次のように、コード内でパフォーマンス カウンターを有効にすることもできます。  
  
```csharp
using System.Configuration;  
using System.ServiceModel.Configuration;  
using System.ServiceModel.Diagnostics;  
Configuration config = ConfigurationManager.OpenExeConfiguration(  
    ConfigurationUserLevel.None);  
ServiceModelSectionGroup sg = ServiceModelSectionGroup.GetSectionGroup(config);  
sg.Diagnostic.PerformanceCounters = PerformanceCounterScope.All;  
config.Save();  
```  
  
## <a name="viewing-performance-data"></a>パフォーマンス データの表示  
 Windows に付属のパフォーマンス モニター (Perfmon.exe) を使用して、パフォーマンス カウンターによりキャプチャされたデータを表示できます。 このツールを起動するには、 **[スタート]** に移動し、 **[実行]** をクリックして、ダイアログボックスに「`perfmon.exe`」と入力します。  
  
> [!NOTE]
> エンドポイント ディスパッチャーによって最後のメッセージが処理される前に、パフォーマンス カウンター インスタンスが解放される場合があります。 その結果、パフォーマンス データに一部のメッセージがキャプチャされない可能性があります。  
  
## <a name="increasing-memory-size-for-performance-counters"></a>パフォーマンス カウンターのメモリ サイズの増加  
 WCF では、パフォーマンスカウンターカテゴリに個別の共有メモリを使用します。  
  
 既定では、個々の共有メモリは、グローバル パフォーマンス カウンターのメモリ サイズの 4 分の 1 に設定されます。 グローバル パフォーマンス カウンターのメモリの既定値は 524,288 バイトです。 このため、3つの WCF パフォーマンスカウンタカテゴリの既定のサイズは、それぞれ約 128 KB です。 コンピューター上の WCF アプリケーションのランタイム特性によっては、パフォーマンスカウンターのメモリが不足することがあります。 これが発生すると、WCF はアプリケーションイベントログにエラーを書き込みます。 エラーの内容にはパフォーマンス カウンターが読み込まれなかったことが示され、エントリには、"System.InvalidOperationException: カスタム カウンター ファイル ビューのメモリが足りません" という例外が含まれます。 このエラー レベルでトレースが有効になっている場合は、さらにこの障害がトレースされます。 パフォーマンスカウンターのメモリが不足している場合は、パフォーマンスカウンターが有効になっている WCF アプリケーションの実行を継続すると、パフォーマンスが低下する可能性があります。 コンピューターの管理者は、使用可能なすべてのパフォーマンス カウンターをいつでも読み込めるだけの十分なメモリを割り当てておく必要があります。  
  
 レジストリの WCF カテゴリのパフォーマンスカウンターのメモリ量を変更できます。 これを行うには、次の 3 つの場所に `FileMappingSize` という名前の新しい DWORD 値を追加し、目的の値をバイト単位で設定します。 コンピューターを再起動すると、設定した値が有効になります。  
  
- HKLM\System\CurrentControlSet\Services\ServiceModelEndpoint 4.0.0.0\Performance  
  
- HKLM\System\CurrentControlSet\Services\ServiceModelOperation 4.0.0.0\Performance  
  
- HKLM\System\CurrentControlSet\Services\ServiceModelService 4.0.0.0\Performance  
  
 膨大な数のオブジェクト (ServiceHost など) が破棄され、ガベージ コレクトされるまで待機している場合、`PrivateBytes` パフォーマンス カウンターには非常に高い数値が登録されます。 この問題を解決するには、アプリケーション固有の独自のカウンターを追加するか、`performanceCounters` 属性を使用してサービス レベルのカウンターだけを有効にします。  
  
## <a name="types-of-performance-counters"></a>パフォーマンス カウンターの種類  
 パフォーマンス カウンターには、サービス、エンドポイント、操作の 3 つのレベルがあります。  
  
 WMI を使用してパフォーマンス カウンターのインスタンス名を取得できます。 たとえば、オブジェクトに適用された  
  
- サービスカウンターのインスタンス名は、WMI[サービス](../wmi/service.md)インスタンスの "counterinstancename" プロパティを使用して取得できます。  
  
- エンドポイントカウンターのインスタンス名は、WMI[エンドポイント](../wmi/endpoint.md)インスタンスの "counterinstancename" プロパティを使用して取得できます。  
  
- 操作カウンターのインスタンス名は、WMI[エンドポイント](../wmi/endpoint.md)インスタンスの "GetOperationCounterInstanceName" メソッドを使用して取得できます。  
  
 WMI の詳細については、「[診断のための Windows Management Instrumentation の使用](../wmi/index.md)」を参照してください。  
  
### <a name="service-performance-counters"></a>サービスのパフォーマンス カウンター  
 サービスのパフォーマンス カウンターはサービス動作全体を測定し、サービス全体のパフォーマンスを診断するために使用できます。 パフォーマンス モニターを使用して表示する場合、これらのカウンターは、`ServiceModelService 4.0.0.0` パフォーマンス オブジェクトの下にあります。 インスタンスには次のパターンの名前が付けられています。  
  
`ServiceName@ServiceBaseAddress`
  
 サービス スコープ内のカウンターは、エンドポイントのコレクションのカウンターが集計されています。  
  
 サービス インスタンス作成のパフォーマンス カウンターは、新しい InstanceContext が作成されるとインクリメントされます。 新しい InstanceContext は、非アクティブ化メッセージを (既存のサービスで) 受信した場合でも、あるセッションからインスタンスに接続し、セッションを終了後に別のセッションから再接続した場合でも作成されることに注意してください。  
  
### <a name="endpoint-performance-counters"></a>エンドポイントのパフォーマンス カウンター  
 エンドポイントのパフォーマンス カウンターにより、エンドポイントでのメッセージの受信状況を表すデータを参照できます。 パフォーマンス モニターを使用して表示する場合、これらのカウンターは、`ServiceModelEndpoint 4.0.0.0` パフォーマンス オブジェクトの下にあります。 インスタンスには次のパターンの名前が付けられています。  
  
`(ServiceName).(ContractName)@(endpoint listener address)`
  
 このデータは、個々の操作で収集されるデータに似ていますが、エンドポイントから集計されただけのデータです。  
  
 エンドポイント スコープ内のカウンターは、操作のコレクションのカウンターから集計されます。  
  
> [!NOTE]
> コントラクト名とアドレスが同一の 2 つのエンドポイントは、同じカウンター インスタンスにマップされます。  
  
### <a name="operation-performance-counters"></a>操作のパフォーマンス カウンター  
 パフォーマンス モニターを使用して表示する場合、操作パフォーマンス カウンターは、`ServiceModelOperation 4.0.0.0` パフォーマンス オブジェクトの下にあります。 それぞれの操作に個別のインスタンスがあります。 つまり、指定したコントラクトに 10 の操作がある場合、10 の操作カウンター インスタンスがそのコントラクトに関連付けられます。 オブジェクトのインスタンスには次のパターンの名前が付いています。  
  
`(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)`
  
 このカウンターにより呼び出しがどのように使用されている、操作がどれほど効率的に実行されているかを調べることができます。  
  
 カウンターが複数のスコープで表示される場合、上位のスコープで収集されたデータは、下位のスコープからのデータが集計されています。 たとえば、エンドポイントの `Calls` は、エンドポイント内のすべての操作呼び出しの合計を表します。サービスの `Calls` は、サービス内のすべての操作呼び出しの合計を表します。  
  
> [!NOTE]
> 1 つのコントラクトに重複した操作名がある場合は、その両方の操作に対してカウンター インスタンスは 1 つだけ取得されます。  
  
## <a name="programming-the-wcf-performance-counters"></a>WCF パフォーマンス カウンターのプログラミング  

SDK のインストールフォルダーには、プログラムによって WCF パフォーマンスカウンターにアクセスできるように、いくつかのファイルがインストールされます。 これらのファイルは次のように一覧表示されます。
  
- *\_ServiceModelEndpointPerfCounters*
- *\_ServiceModelOperationPerfCounters*
- *\_ServiceModelServicePerfCounters*  
- *\_SMSvcHostPerfCounters*
- *\_TransactionBridgePerfCounters*
  
プログラムによってカウンターにアクセスする方法の詳細については、「[パフォーマンスカウンターのプログラミングアーキテクチャ](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/5f9bkxzf(v=vs.90))」を参照してください。
  
## <a name="see-also"></a>関連項目

- [管理と診断](../index.md)
