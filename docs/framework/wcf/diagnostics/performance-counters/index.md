---
title: WCF パフォーマンス カウンター
ms.date: 03/30/2017
helpviewer_keywords:
- performance counters [WCF]
ms.assetid: f559b2bd-ed83-4988-97a1-e88f06646609
ms.openlocfilehash: 31c5b386d707aa49cd36d536f1c8b419eb74a658
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59087860"
---
# <a name="wcf-performance-counters"></a>WCF パフォーマンス カウンター
Windows Communication Foundation (WCF) には、多数アプリケーションのパフォーマンスの測定に役立つパフォーマンス カウンターにはが含まれています。  
  
## <a name="enabling-performance-counters"></a>パフォーマンス カウンターの有効化  
 次のように WCF サービスの app.config 構成ファイルで WCF サービスのパフォーマンス カウンターを有効ことができます。  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <diagnostics performanceCounters="All" />  
    </system.serviceModel>  
</configuration>  
```  
  
 特定の種類のパフォーマンス カウンターを有効にするよう `performanceCounters` 属性を設定できます。 有効な値は、次のとおりです。  
  
-   すべての：すべてのカテゴリ カウンター (ServiceModelService、ServiceModelEndpoint、ServiceModelOperation) が有効になります。  
  
-   ServiceOnly:ServiceModelService カテゴリ カウンターのみが有効になります。 これが既定値です。  
  
-   オフします。ServiceModel * パフォーマンス カウンターが無効です。  
  
 すべての WCF アプリケーションのパフォーマンス カウンターを有効にする場合は、Machine.config ファイルで構成設定を配置できます。  参照してください、**パフォーマンス カウンターのメモリ サイズの増加**コンピューターに十分なメモリのパフォーマンス カウンターの構成の詳細については後述します。  
  
 カスタム操作の呼び出し元などの WCF 機能拡張ポイントを使用する場合は、独自のパフォーマンス カウンターも出力する必要があります。 これは、ため、WCF は既定のパスに標準のパフォーマンス カウンター データを出力できなく機能拡張ポイントを実装する場合です。 手動パフォーマンス カウンターのサポートを実装しない場合、予測したパフォーマンス カウンター データが得られない場合があります。  
  
 また次のように、コード内でパフォーマンス カウンターを有効にすることもできます。  
  
```  
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
 Windows に付属のパフォーマンス モニター (Perfmon.exe) を使用して、パフォーマンス カウンターによりキャプチャされたデータを表示できます。 移動して、このツールを起動できます**開始**、 をクリック**実行**と種類`perfmon.exe` ダイアログ ボックス。  
  
> [!NOTE]
>  エンドポイント ディスパッチャーによって最後のメッセージが処理される前に、パフォーマンス カウンター インスタンスが解放される場合があります。 その結果、パフォーマンス データに一部のメッセージがキャプチャされない可能性があります。  
  
## <a name="increasing-memory-size-for-performance-counters"></a>パフォーマンス カウンターのメモリ サイズの増加  
 WCF では、そのパフォーマンス カウンターのカテゴリを個別の共有メモリを使用します。  
  
 既定では、個々の共有メモリは、グローバル パフォーマンス カウンターのメモリ サイズの 4 分の 1 に設定されます。 グローバル パフォーマンス カウンターのメモリの既定値は 524,288 バイトです。 そのため、3 つの WCF パフォーマンス カウンターのカテゴリには、既定のサイズは約 128 KB があります。 コンピューターで WCF アプリケーションの実行時特性によっては、パフォーマンス カウンターのメモリを使い果たして可能性があります。 この場合、WCF は、アプリケーション イベント ログにエラーを書き込みます。 エラーの内容の状態のパフォーマンス カウンターが読み込まれていないことと、エントリには、例外が含まれています"System.invalidoperationexception::。カスタム カウンター ファイル ビューのメモリ不足です。" このエラー レベルでトレースが有効になっている場合は、さらにこの障害がトレースされます。 パフォーマンス カウンターのメモリがなくなった場合は、パフォーマンスの低下になる可能性がありますを有効になっているパフォーマンス カウンターと、WCF アプリケーションの実行を継続します。 コンピューターの管理者は、使用可能なすべてのパフォーマンス カウンターをいつでも読み込めるだけの十分なメモリを割り当てておく必要があります。  
  
 レジストリ内の WCF カテゴリのパフォーマンス カウンターのメモリの量を変更することができます。 これを行うには、次の 3 つの場所に `FileMappingSize` という名前の新しい DWORD 値を追加し、目的の値をバイト単位で設定します。 コンピューターを再起動すると、設定した値が有効になります。  
  
-   HKLM\System\CurrentControlSet\Services\ServiceModelEndpoint 4.0.0.0\Performance  
  
-   HKLM\System\CurrentControlSet\Services\ServiceModelOperation 4.0.0.0\Performance  
  
-   HKLM\System\CurrentControlSet\Services\ServiceModelService 4.0.0.0\Performance  
  
 膨大な数のオブジェクト (ServiceHost など) が破棄され、ガベージ コレクトされるまで待機している場合、`PrivateBytes` パフォーマンス カウンターには非常に高い数値が登録されます。 この問題を解決するには、アプリケーション固有の独自のカウンターを追加するか、`performanceCounters` 属性を使用してサービス レベルのカウンターだけを有効にします。  
  
## <a name="types-of-performance-counters"></a>パフォーマンス カウンターの種類  
 次の 3 つの異なるレベルのスコープはパフォーマンス カウンター。サービス、エンドポイントおよび操作します。  
  
 WMI を使用してパフォーマンス カウンターのインスタンス名を取得できます。 例えば以下のようにします。  
  
-   WMI を通じてサービス カウンター インスタンス名を取得できます[サービス](../../../../../docs/framework/wcf/diagnostics/wmi/service.md)インスタンスの"CounterInstanceName"プロパティです。  
  
-   WMI を通じてエンドポイント カウンター インスタンス名を取得できます[エンドポイント](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md)インスタンスの"CounterInstanceName"プロパティです。  
  
-   WMI を通じて操作カウンター インスタンス名を取得できます[エンドポイント](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md)インスタンスの"GetOperationCounterInstanceName"メソッドです。  
  
 WMI の詳細については、次を参照してください。[診断用の Windows Management Instrumentation のを使用して](../../../../../docs/framework/wcf/diagnostics/wmi/index.md)します。  
  
### <a name="service-performance-counters"></a>サービスのパフォーマンス カウンター  
 サービスのパフォーマンス カウンターはサービス動作全体を測定し、サービス全体のパフォーマンスを診断するために使用できます。 パフォーマンス モニターを使用して表示する場合、これらのカウンターは、`ServiceModelService 4.0.0.0` パフォーマンス オブジェクトの下にあります。 インスタンスには次のパターンの名前が付けられています。  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
 サービス スコープ内のカウンターは、エンドポイントのコレクションのカウンターが集計されています。  
  
 サービス インスタンス作成のパフォーマンス カウンターは、新しい InstanceContext が作成されるとインクリメントされます。 新しい InstanceContext は、非アクティブ化メッセージを (既存のサービスで) 受信した場合でも、あるセッションからインスタンスに接続し、セッションを終了後に別のセッションから再接続した場合でも作成されることに注意してください。  
  
### <a name="endpoint-performance-counters"></a>エンドポイントのパフォーマンス カウンター  
 エンドポイントのパフォーマンス カウンターにより、エンドポイントでのメッセージの受信状況を表すデータを参照できます。 パフォーマンス モニターを使用して表示する場合、これらのカウンターは、`ServiceModelEndpoint 4.0.0.0` パフォーマンス オブジェクトの下にあります。 インスタンスには次のパターンの名前が付けられています。  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 このデータは、個々の操作で収集されるデータに似ていますが、エンドポイントから集計されただけのデータです。  
  
 エンドポイント スコープ内のカウンターは、操作のコレクションのカウンターから集計されます。  
  
> [!NOTE]
>  コントラクト名とアドレスが同一の 2 つのエンドポイントは、同じカウンター インスタンスにマップされます。  
  
### <a name="operation-performance-counters"></a>操作のパフォーマンス カウンター  
 パフォーマンス モニターを使用して表示する場合、操作パフォーマンス カウンターは、`ServiceModelOperation 4.0.0.0` パフォーマンス オブジェクトの下にあります。 それぞれの操作に個別のインスタンスがあります。 つまり、指定したコントラクトに 10 の操作がある場合、10 の操作カウンター インスタンスがそのコントラクトに関連付けられます。 オブジェクトのインスタンスには次のパターンの名前が付いています。  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 このカウンターにより呼び出しがどのように使用されている、操作がどれほど効率的に実行されているかを調べることができます。  
  
 カウンターが複数のスコープで表示される場合、上位のスコープで収集されたデータは、下位のスコープからのデータが集計されています。 たとえば、エンドポイントの `Calls` は、エンドポイント内のすべての操作呼び出しの合計を表します。サービスの `Calls` は、サービス内のすべての操作呼び出しの合計を表します。  
  
> [!NOTE]
>  1 つのコントラクトに重複した操作名がある場合は、その両方の操作に対してカウンター インスタンスは 1 つだけ取得されます。  
  
## <a name="programming-the-wcf-performance-counters"></a>WCF パフォーマンス カウンターのプログラミング  
 複数のファイルは、WCF パフォーマンス カウンタをプログラムでアクセスできるように、SDK のインストール フォルダーにインストールされます。 そのファイルを次に示します。  
  
-   _ServiceModelEndpointPerfCounters.vrg  
  
-   _ServiceModelOperationPerfCounters.vrg  
  
-   _ServiceModelServicePerfCounters.vrg  
  
-   _SMSvcHostPerfCounters.vrg  
  
-   _TransactionBridgePerfCounters.vrg  
  
 カウンターをプログラムでアクセスする方法の詳細については、次を参照してください。[パフォーマンス カウンターのプログラミング アーキテクチャ](https://go.microsoft.com/fwlink/?LinkId=95179)します。  
  
## <a name="see-also"></a>関連項目

- [管理と診断](../../../../../docs/framework/wcf/diagnostics/index.md)
