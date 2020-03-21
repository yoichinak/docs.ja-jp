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
ms.openlocfilehash: 69f15cc9583b397017ac30a0c567914495867c18
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153322"
---
# <a name="sharedlisteners-element"></a>\<共有リスナー>要素
任意の source 要素または trace 要素が参照できるリスナーを含みます。  これらのリスナーは、既定ではトレースを受信せず、実行時にこれらのリスナーを取得することはできません。 共有リスナーとして識別されたリスナーは、ソースまたはトレースに名前で追加できます。  
  
[**\<構成>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<診断>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<共有リスナー>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<sharedListeners>
  <add>...</add>  
</sharedListeners>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 [なし] :  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<>を追加する](add-element-for-listeners-for-trace.md)|`sharedListeners` コレクションにリスナーを追加します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`Configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`system.diagnostics`|ASP.NET 構成セクションのルート要素を指定します。|  
  
## <a name="remarks"></a>解説  
 共有リスナーコレクションにリスナーを追加しても、アクティブなリスナーにはなっていません。 トレース ソースまたはトレース要素の`Listeners`コレクションに追加することによって、トレース ソースまたはトレースに追加する必要があります。 .NET Framework のリスナー クラスは、<xref:System.Diagnostics.TraceListener>クラスから派生します。  
  
 この要素は、コンピューター構成ファイル (Machine.config) とアプリケーション構成ファイルで使用できます。  
  
## <a name="example"></a>例  
 次の例は、要素を使用`<sharedListeners>`して、 クラスと`console`<xref:System.Diagnostics.Trace>クラス`Listeners`の両方のリスナー<xref:System.Diagnostics.TraceSource>をコレクションに追加する方法を示しています。 コンソール トレース リスナーは、<xref:System.Diagnostics.TraceSource>または<xref:System.Diagnostics.Trace>への呼び出しを通じてトレース情報をコンソールに書き込みます。  
  
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
