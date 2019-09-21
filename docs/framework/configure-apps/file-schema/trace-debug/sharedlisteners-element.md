---
title: <sharedListeners> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#sharedListeners
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners
helpviewer_keywords:
- <sharedListeners> element
- listeners
- shared listeners
- trace listeners, <sharedListeners> element
- sharedListeners element
ms.assetid: de200534-19dd-4156-86cf-c50521802c4c
ms.openlocfilehash: 41cabcbce13409b0842cbbd625028b51d32d59d0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926982"
---
# <a name="sharedlisteners-element"></a>\<sharedListeners > 要素
任意の source 要素または trace 要素が参照できるリスナーを含みます。  これらのリスナーは、既定ではトレースを受信せず、実行時にこれらのリスナーを取得することはできません。 共有リスナーとして識別されるリスナーは、名前を指定してソースまたはトレースに追加できます。  
  
 \<configuration>  
\<system.diagnostics>  
\<sharedListeners >  
  
## <a name="syntax"></a>構文  
  
```xml  
<sharedListeners>   
  <add>...</add>  
</sharedListeners>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<add>](add-element-for-listeners-for-trace.md)|`sharedListeners` コレクションにリスナーを追加します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`Configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`system.diagnostics`|ASP.NET 構成セクションのルート要素を指定します。|  
  
## <a name="remarks"></a>Remarks  
 リスナーを共有リスナーコレクションに追加しても、それがアクティブなリスナーになることはありません。 トレースソースまたはトレースに追加するには、そのトレース要素の`Listeners`コレクションに追加する必要があります。 .NET Framework 内のリスナークラスは、 <xref:System.Diagnostics.TraceListener>クラスから派生します。  
  
 この要素は、コンピューターの構成ファイル (machine.config) とアプリケーション構成ファイルで使用できます。  
  
## <a name="example"></a>例  
 次の例は`<sharedListeners>` 、要素を使用し<xref:System.Diagnostics.TraceSource>て、クラスと`console` <xref:System.Diagnostics.Trace>クラスの`Listeners`両方のコレクションにリスナーを追加する方法を示しています。 コンソールトレースリスナーは、 <xref:System.Diagnostics.TraceSource>または<xref:System.Diagnostics.Trace>の呼び出しを通じて、トレース情報をコンソールに書き込みます。  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sharedListeners>  
      <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"  
          initializeData="Warning" />  
      </add>  
    </sharedListeners>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"  >  
        <listeners>  
          <add name="console" />  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Verbose"/>  
    </switches>  
    <trace>  
      <listeners>  
        <add name="console" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Diagnostics.TraceListener>
- [トレースおよびデバッグ設定のスキーマ](index.md)
- [トレース リスナー](../../../debug-trace-profile/trace-listeners.md)
