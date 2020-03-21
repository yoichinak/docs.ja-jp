---
title: <system.web> 要素 (Web 設定)
ms.date: 03/30/2017
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- system.Web element
- <system.Web> element
- ASP.NET configuration system
- configuration files [ASP.NET]
ms.assetid: 24c4cf4f-ad32-42b2-b040-8e4549e2855e
ms.openlocfilehash: b37b05bdf90630251cbfcf86751243a3a8b77663
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152842"
---
# <a name="systemweb-element-web-settings"></a>\<要素> (Web 設定)
ASP.NET ホスト レイヤーがプロセス全体の動作を管理する方法に関する情報が含まれています。  
  
[**\<構成>**](../configuration-element.md)  
&nbsp;&nbsp;**\<ウェブ>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  

以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  

[なし] :  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<アプリケーションプール>](applicationpool-element-web-settings.md)|aspnet.config ファイル内の IIS アプリケーション プールの構成設定を指定します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<構成>](../configuration-element.md)|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素を指定します。|  
  
## <a name="remarks"></a>解説  

要素`system.web`とその子`applicationPool`要素は、.NET Framework 3.5 SP1 の時点で .NET Framework に追加されました。 統合モードで IIS 7.0 以降のバージョンを実行すると、この要素の組み合わせによって、ASP.NETがスレッドを管理する方法と、iIS アプリケーション プールでホストされている場合の要求ASP.NETキューに追加する方法を構成できます。 クラシック モードまたは ISAPI モードで IIS 7.0 以降のバージョンを実行する場合、これらの設定は無視されます。  
  
## <a name="example"></a>例  

次の例は ASP.NET、iIS アプリケーション プールでASP.NETがホストされている場合に、aspnet.config ファイルでプロセス全体の動作を構成する方法を示ASP.NET。 この例では、IIS が統合モードで実行されており、アプリケーションが .NET Framework 3.5 SP1 以降のバージョンを使用していることを前提としています。 この現象は、.NET Framework 3.5 SP1 より前のバージョンの .NET Framework では発生しません。 この例の値はデフォルト値です。  
  
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

- [\<アプリケーションプール>要素 (Web 設定)](applicationpool-element-web-settings.md)
