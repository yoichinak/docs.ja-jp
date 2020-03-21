---
title: <applicationPool> 要素 (Web 設定)
ms.date: 03/30/2017
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
ms.openlocfilehash: 6feaa801610fa0ffbbf47575f25aff29fa46a66c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152855"
---
# <a name="applicationpool-element-web-settings"></a>\<applicationPool> 要素 (Web 設定)
ASP.NET アプリケーションが IIS 7.0 以降のバージョンで統合モードで実行されている場合に、プロセス全体の動作を管理するためにASP.NETによって使用される構成設定を指定します。  
  
> [!IMPORTANT]
> この要素とサポートする機能は、ASP.NET アプリケーションが IIS 7.0 以降のバージョンでホストされている場合にのみ機能します。  
  
[**\<構成>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<ウェブ>**](system-web-element-web-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<アプリケーションプール>**  
  
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
|`maxConcurrentRequestsPerCPU`|CPU ごとに許可ASP.NET同時要求の数を指定します。|  
|`maxConcurrentThreadsPerCPU`|各 CPU のアプリケーション プールで実行できる同時スレッドの数を指定します。 これにより、要求を処理するために CPU ごとに使用できるマネージ スレッドの数を制限できるため、ASP.NET同時実行を制御する別の方法が提供されます。 既定では、この設定は 0 で、ASP.NETは、CPU ごとに作成できるスレッドの数を制限しないことを意味します。|  
|`requestQueueLimit`|1 つのプロセスでASP.NETにキューに入れることができる要求の最大数を指定します。 1 つのアプリケーション プールで複数のASP.NETアプリケーションを実行する場合、アプリケーション プール内の任意のアプリケーションに対して行われる要求の累積セットは、この設定の対象となります。|  
  
### <a name="child-elements"></a>子要素  
 [なし] :  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<ウェブ>](system-web-element-web-settings.md)|ASP.NETがホスト アプリケーションと対話する方法に関する情報が含まれています。|  
  
## <a name="remarks"></a>解説  

統合モードで IIS 7.0 以降のバージョンを実行する場合、この要素の組み合わせにより、アプリケーションが IIS アプリケーション プールでホストされている場合に、ASP.NETがスレッドを管理し、要求をキューに格納する方法を構成できます。 IIS 6 を実行する場合、またはクラシック モードまたは ISAPI モードで IIS 7.0 を実行した場合、これらの設定は無視されます。  
  
設定`applicationPool`は、.NET Framework の特定のバージョンで実行されるすべてのアプリケーション プールに適用されます。 設定は、aspnet.config ファイルに含まれています。 このファイルのバージョンは、.NET Framework のバージョン 2.0 および 4.0 です。 (.NET Framework のバージョン 3.0 および 3.5 は、aspnet.config ファイルをバージョン 2.0 と共有します。  
  
> [!IMPORTANT]
> Windows 7 で IIS 7.0 を実行する場合は、アプリケーション プールごとに個別の aspnet.config ファイルを構成できます。 これにより、各アプリケーション プールのスレッドのパフォーマンスを調整できます。  
  
この設定`maxConcurrentRequestsPerCPU`では、.NET Framework 4 の既定の設定である "5000" は、実際に CPU あたり 5000 以上の要求がある場合を除き、ASP.NETによって制御される要求調整を効果的にオフにします。 既定の設定は、代わりに、CPU ごとの同時実行を自動的に管理する CLR スレッド プールに依存します。 非同期要求処理を広範に使用するアプリケーション、またはネットワーク I/O でブロックされた長時間の要求が多数あるアプリケーションは、.NET Framework 4 の既定の制限の増加により、恩恵を受けます。 ゼロ`maxConcurrentRequestsPerCPU`に設定すると、ASP.NET要求を処理するためのマネージ スレッドの使用が無効になります。 アプリケーションが IIS アプリケーション プールで実行されている場合、要求は IIS I/O スレッド上にとどまり、したがって同時実行制御は IIS スレッド設定によって制限されます。  
  
この`requestQueueLimit`設定は、ASP.NETアプリケーションの`requestQueueLimit`Web.config ファイルで設定される[processModel](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100))要素の属性と同じように機能します。 ただし、aspnet.config ファイルの`requestQueueLimit`設定は、Web.config ファイルの`requestQueueLimit`設定をオーバーライドします。 つまり、両方の属性が設定されている場合 (既定では true)、aspnet.config ファイルの`requestQueueLimit`設定が優先されます。  
  
## <a name="example"></a>例  

次の例は、次の状況で aspnet.config ファイルでプロセス全体の動作 ASP.NETを構成する方法を示しています。  
  
- アプリケーションは IIS 7.0 アプリケーション プールでホストされます。  
  
- IIS 7.0 は統合モードで実行されています。  
  
- アプリケーションは、.NET Framework 3.5 SP1 またはそれ以降のバージョンを使用しています。  
  
この例の値はデフォルト値です。  
  
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
|空にできる||  
  
## <a name="see-also"></a>関連項目

- [\<要素> (Web 設定)](system-web-element-web-settings.md)
