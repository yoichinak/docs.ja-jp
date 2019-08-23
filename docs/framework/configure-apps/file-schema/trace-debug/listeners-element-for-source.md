---
title: <source> の <listeners> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners
helpviewer_keywords:
- listeners element for <source>
- <listeners> element for <source>
ms.assetid: a2991f43-b4d3-4614-a8e7-da392de9697f
ms.openlocfilehash: 853bc94978218fd4d426e6070b3a36e20435cd6d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920493"
---
# <a name="listeners-element-for-source"></a>\<ソース > の\<リスナー > 要素
のコレクション<xref:System.Diagnostics.TraceSource.Listeners%2A>内のリスナーを追加または削除します。<xref:System.Diagnostics.TraceSource> リスナーは、ログ、ウィンドウ、テキストファイルなど、適切なターゲットにトレース出力を送信します。  
  
 \<configuration>  
\<system.diagnostics>  
\<ソース >  
\<ソース >  
\<リスナー > 要素  
  
## <a name="syntax"></a>構文  
  
```xml  
<listeners>   
  <add>...</add>  
  <remove ... />  
  <clear/>  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<add>](add-element-for-listeners-for-source.md)|`Listeners` コレクションにリスナーを追加します。|  
|[\<remove>](remove-element-for-listeners-for-source.md)|`Listeners`コレクションからリスナーを削除します。|  
|[\<clear>](clear-element-for-listeners-for-source.md)|トレース ソースの `Listeners` コレクションを消去します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`system.diagnostics`|メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。|  
|`sources`|トレース メッセージを開始するトレース ソースを保持します。|  
|`source`|トレース メッセージを開始するトレース ソースを指定します。|  
  
## <a name="remarks"></a>Remarks  
  
## <a name="configuration-file"></a>構成ファイル  
 この要素は、コンピューターの構成ファイル (machine.config) とアプリケーション構成ファイルで使用できます。  
  
## <a name="example"></a>例  
 次の例は、 `<listeners>`要素を使用して、コンソールトレースリスナーを`mySource`ソースに追加し、既定のトレースリスナーを削除する方法を示しています。  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"   
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener">  
            <filter type="System.Diagnostics.EventTypeFilter"   
              initializeData="Error"/>  
          </add>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Diagnostics.TraceListener>
- [トレースおよびデバッグ設定のスキーマ](index.md)
- [トレース リスナー](../../../debug-trace-profile/trace-listeners.md)
