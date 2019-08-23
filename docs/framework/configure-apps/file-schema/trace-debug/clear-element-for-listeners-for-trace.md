---
title: <clear> の <listeners> の <trace> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 9816ba0f8e4ddd4c38537eb4e014a4240ff20407
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927180"
---
# <a name="clear-element-for-listeners-for-trace"></a>\<トレース > の\<リスナー \<> の > 要素をクリアします
トレースの `Listeners` コレクションを削除します。  
  
 \<configuration>  
\<system.diagnostics>  
\<トレース >  
\<リスナー >  
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
|`listeners`|メッセージを収集、格納、およびルーティングするリスナーを格納します。 リスナーは、適切なターゲットにトレース出力を送信します。|  
  
## <a name="remarks"></a>Remarks  
 要素`<clear>`は、トレースの`Listeners`コレクションからすべてのリスナーを削除します。 要素を使用`<add>`し`<clear>`て、コレクション内に他のアクティブなリスナーが存在しないことを特定することができます。  
  
 コレクションは、 `Listeners` <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType>プロパティ ( <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> )でメソッドを呼び出すことで、プログラムによって消去できます。`System.Diagnostics.Trace.Listeners.Clear()`  
  
 この要素は、コンピューターの構成ファイル (machine.config) とアプリケーション構成ファイルで使用できます。  
  
> [!NOTE]
> 要素`<clear>`は、、 <xref:System.Diagnostics.DefaultTraceListener> 、 <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>、 `Listeners`および<xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType> <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>の各メソッドの動作を変更して、をコレクションから削除します。<xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> 通常、 `Assert`メソッド`Fail`またはメソッドを呼び出すと、メッセージボックスが表示されます。 ただし、 <xref:System.Diagnostics.DefaultTraceListener>が`Listeners`コレクションに含まれていない場合、メッセージボックスは表示されません。  
  
## <a name="example"></a>例  
 次の例では、要素を`<clear>`使用し`<add>`て、トレースの`Listeners`コレクションにリスナー `console`を追加する前に、要素を使用する方法を示します。  
  
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
- [トレースおよびデバッグ設定のスキーマ](index.md)
- [\<remove>](remove-element-for-listeners-for-trace.md)
- [トレース リスナー](../../../debug-trace-profile/trace-listeners.md)
