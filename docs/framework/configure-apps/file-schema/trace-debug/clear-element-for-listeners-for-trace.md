---
title: <clear> の <listeners> の <trace> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 97b18f9d6baa618b0f535955b232e2119c758b11
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59124892"
---
# <a name="clear-element-for-listeners-for-trace"></a>\<クリア > 要素の\<リスナー > の\<トレース >
トレースの `Listeners` コレクションを削除します。  
  
 \<configuration>  
\<system.diagnostics>  
\<トレース >  
\<listeners>  
\<clear>  
  
## <a name="syntax"></a>構文  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`system.diagnostics`|メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。|  
|`trace`|トレース メッセージを収集、格納、およびルーティングするリスナーを保持します。|  
|`listeners`|収集、格納、およびメッセージをルーティングするリスナーが含まれています。 リスナーでは、適切なターゲットのトレースを出力します。|  
  
## <a name="remarks"></a>Remarks  
 `<clear>`要素からすべてのリスナーを削除して、`Listeners`トレースのコレクション。 使用することができます、`<clear>`要素を使用する前に、`<add>`要素をコレクション内の他のアクティブなリスナーが存在しないことを特定します。  
  
 オフにすることができます、`Listeners`呼び出すことによってプログラムでのコレクション、<xref:System.Diagnostics.TraceListenerCollection.Clear%2A>メソッドを<xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType>プロパティ (`System.Diagnostics.Trace.Listeners.Clear()`)。  
  
 この要素は、マシン構成ファイル (Machine.config) と、アプリケーション構成ファイルで使用できます。  
  
> [!NOTE]
>  `<clear>`要素は、削除、<xref:System.Diagnostics.DefaultTraceListener>から、`Listeners`の動作を変更するコレクション、 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>、 <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>、 <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>、および<xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType>メソッド。 呼び出す、`Assert`または`Fail`メソッドは、通常、メッセージ ボックスの表示になります。 場合、メッセージ ボックスが表示されません、<xref:System.Diagnostics.DefaultTraceListener>内にない、`Listeners`コレクション。  
  
## <a name="example"></a>例  
 次の例は、使用する方法を示します、`<clear>`要素を使用する前に、`<add>`リスナーを追加する要素`console`を`Listeners`トレースのコレクション。  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <clear/>  
        <add name="console"   
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"   
            initializeData="Error" />  
        </add>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Diagnostics.Trace.Listeners%2A>
- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.TraceSource>
- [トレースおよびデバッグ設定のスキーマ](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [\<remove>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)
- [トレース リスナー](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
