---
title: <clear>の<listeners>要素<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 905dad8274fede80f4809ff3c7a014049f9df450
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153543"
---
# <a name="clear-element-for-listeners-for-trace"></a>\<トレース>の\<>リスナーの>\<要素をクリアします。
トレースの `Listeners` コレクションを削除します。  

[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<診断>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<トレース>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<リスナー>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<クリア>**

## <a name="syntax"></a>構文  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 [なし] :  
  
### <a name="child-elements"></a>子要素  
 [なし] :  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`system.diagnostics`|メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。|  
|`trace`|トレース メッセージを収集、格納、およびルーティングするリスナーを保持します。|  
|`listeners`|メッセージを収集、格納、およびルーティングするリスナーが含まれています。 リスナーは、トレース出力を適切なターゲットに送ります。|  
  
## <a name="remarks"></a>解説  
 この`<clear>`要素は、トレースのコレクションからすべての`Listeners`リスナーを削除します。 要素を`<clear>`使用する前に要素を`<add>`使用して、コレクション内に他のアクティブなリスナーがないことを確認できます。  
  
 プロパティ ( `Listeners` )`System.Diagnostics.Trace.Listeners.Clear()`のメソッドを<xref:System.Diagnostics.TraceListenerCollection.Clear%2A>呼び出<xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType>すことで、プログラムでコレクションをクリアできます。  
  
 この要素は、コンピューター構成ファイル (Machine.config) とアプリケーション構成ファイルで使用できます。  
  
> [!NOTE]
> 要素`<clear>`は<xref:System.Diagnostics.DefaultTraceListener>`Listeners`、コレクションからを削除し、 、、<xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType><xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>および<xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType><xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType>メソッドの動作を変更します。 または`Fail``Assert`メソッドを呼び出すと、通常はメッセージ ボックスが表示されます。 ただし、 がコレクションに含まれていない場合<xref:System.Diagnostics.DefaultTraceListener>は、メッセージ ボックス`Listeners`は表示されません。  
  
## <a name="example"></a>例  
 次の例は、要素を使用`<clear>`してトレース用の`<add>`リスナー`console`をコレクションに追加する前`Listeners`に、要素を使用する方法を示しています。  
  
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
- [\<>を削除する](remove-element-for-listeners-for-trace.md)
- [トレース リスナー](../../../debug-trace-profile/trace-listeners.md)
