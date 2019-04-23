---
title: <applicationPool> 要素 (Web 設定)
ms.date: 03/30/2017
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
ms.openlocfilehash: 16207c3f3c711d06b71cafb2b67c5d29f3f14e39
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59184731"
---
# <a name="applicationpool-element-web-settings"></a>\<applicationPool > 要素 (Web 設定)
ASP.NET アプリケーションが統合モードで実行されている場合に、プロセス全体の動作を管理する、ASP.NET で使用される構成設定を指定します[!INCLUDE[iisver](../../../../../includes/iisver-md.md)]以降のバージョン。  
  
> [!IMPORTANT]
>  ASP.NET アプリケーションがホストされている場合のみ機能をサポートこの要素と機能[!INCLUDE[iisver](../../../../../includes/iisver-md.md)]以降のバージョン。  
  
 \<configuration>  
\<system.web > 要素 (Web 設定)  
\<applicationPool > 要素 (Web 設定)  
  
## <a name="syntax"></a>構文  
  
```xml  
<applicationPool   
    maxConcurrentRequestsPerCPU="5000"   
    maxConcurrentThreadsPerCPU="0"   
    requestQueueLimit="5000" />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`maxConcurrentRequestsPerCPU`|ASP.NET では、CPU ごとの同時要求の数を指定します。|  
|`maxConcurrentThreadsPerCPU`|アプリケーション プールの各 CPU の実行できる同時スレッドの数を指定します。 これにより、CPU あたりの要求を処理するために使用できるマネージ スレッドの数を制限するため、ASP.NET の同時実行を制御する別の方法を提供します。 既定では、この設定は 0 で、ASP.NET で制限しないこと、CPU ごとに作成できるスレッドの数が、CLR スレッド プールでは、作成できるスレッドの数によっても制限は。|  
|`requestQueueLimit`|ASP.NET の 1 つのプロセスでキューに追加される要求の最大数を指定します。 2 つまたは複数の ASP.NET アプリケーションは、1 つのアプリケーション プールで実行すると、アプリケーション プール内の任意のアプリケーションに対する要求の累積的なセットは、この設定の対象です。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<system.web >](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)|ASP.NET がホスト アプリケーションと対話する方法についてを説明します。|  
  
## <a name="remarks"></a>Remarks  
 実行するときに[!INCLUDE[iisver](../../../../../includes/iisver-md.md)]統合モードで以降のバージョンがこの要素を組み合わせて、アプリケーションが IIS アプリケーション プールでホストされている場合に、ASP.NET がスレッドとキューの要求を管理する方法を設定できますか。 IIS 6 を実行するかを実行する[!INCLUDE[iisver](../../../../../includes/iisver-md.md)]クラシック モードまたは ISAPI モードでは、これらの設定は無視されます。  
  
 `applicationPool`設定、.NET Framework の特定のバージョンで実行されるすべてのアプリケーション プールに適用されます。 設定は、aspnet.config ファイルに格納されます。 このファイルのバージョン 2.0 と 4.0 の .NET Framework のバージョンがあります。 (バージョン 3.0 および .NET framework 3.5 に、バージョン 2.0 ではある aspnet.config ファイルが共有)。  
  
> [!IMPORTANT]
>  実行する場合[!INCLUDE[iisver](../../../../../includes/iisver-md.md)]で[!INCLUDE[win7](../../../../../includes/win7-md.md)]、すべてのアプリケーション プールの別の aspnet.config ファイルを構成することができます。 これにより、各アプリケーション プールのスレッドのパフォーマンスを調整できます。  
  
 `maxConcurrentRequestsPerCPU`設定、「5000」の既定の設定、[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]が実際には、CPU あたり 5000 以上の要求がない限り、要求の調整をオフに効果的が ASP.NET によって制御されます。 既定の設定は、CPU あたりの同時実行を自動的に管理する CLR のスレッド プールに代わりに依存します。 非同期要求の処理の広範な使用を構成する、またはネットワーク I/O でブロックされている多くの実行時間の長い要求のアプリケーションにメリットが増加の既定の制限から、[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]します。 設定`maxConcurrentRequestsPerCPU`ASP.NET 要求を処理するためのマネージ スレッドの使用を解除します。 0 にします。 アプリケーションを IIS アプリケーション プールで実行すると、IIS の I/O スレッドで常に要求とスレッドの IIS 設定によって同時実行を調整するためです。  
  
 `requestQueueLimit`設定と同じように機能、`requestQueueLimit`の属性、 [processModel](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100))要素で、ASP.NET アプリケーションの Web.config ファイルで設定されます。 ただし、 `requestQueueLimit` aspnet.config ファイルの設定のオーバーライド、 `requestQueueLimit` Web.config ファイルで設定します。 つまり、両方の属性が設定されている場合 (既定では、これが true)、 `requestQueueLimit` aspnet.config ファイルで設定が優先されます。  
  
## <a name="example"></a>例  
 次の例では、次の状況で aspnet.config ファイルに ASP.NET プロセス全体の動作を構成する方法を示します。  
  
-   アプリケーションがホストされている、[!INCLUDE[iisver](../../../../../includes/iisver-md.md)]アプリケーション プール。  
  
-   [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] 統合モードで実行されています。  
  
-   アプリケーションを使用して、[!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)]以降のバージョン。  
  
 値の例では、既定値です。  
  
```xml  
<configuration>  
  <system.web>  
    <applicationPool   
        maxConcurrentRequestsPerCPU="5000"  
        maxConcurrentThreadsPerCPU="0"   
        requestQueueLimit="5000" />  
  </system.web>  
</configuration>  
```  
  
## <a name="element-information"></a>要素情報  
  
|||  
|-|-|  
|名前空間||  
|スキーマ名||  
|検証ファイル||  
|空にすることができます。||  
  
## <a name="see-also"></a>関連項目

- [\<system.web> 要素 (Web 設定)](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)
