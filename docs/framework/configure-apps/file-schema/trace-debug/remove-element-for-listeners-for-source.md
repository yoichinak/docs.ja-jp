---
title: <remove> の <listeners> の <source> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
ms.openlocfilehash: edd27dd262004aead7db4d81db8ecab0e831dac1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926993"
---
# <a name="remove-element-for-listeners-for-source"></a>\<ソース > の\<リスナー \<> の > 要素を削除します
トレース ソースの `Listeners` コレクションからリスナーを削除します。  
  
 \<configuration>  
\<system.diagnostics>  
\<ソース >  
\<ソース >  
\<リスナー >  
\<remove>  
  
## <a name="syntax"></a>構文  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`name`|必須の属性です。<br /><br /> `Listeners`コレクションから削除するリスナーの名前。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`system.diagnostics`|メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。|  
|`sources`|トレース メッセージを開始するトレース ソースを保持します。|  
|`source`|トレース メッセージを開始するトレース ソースを指定します。|  
|`listeners`|メッセージを収集、格納、およびルーティングするリスナーを指定します。|  
  
## <a name="remarks"></a>Remarks  
 要素`<remove>`は、指定されたリスナー `Listeners`をトレースソースのコレクションから削除します。  
  
 インスタンスの`Listeners` <xref:System.Diagnostics.TraceSource.Listeners%2A>プロパティ<xref:System.Diagnostics.TraceListenerCollection.Remove%2A>に対してメソッドを呼び出すことによって、プログラムによってトレースソースのコレクションから要素を削除できます。 <xref:System.Diagnostics.TraceSource>  
  
 この要素は、コンピューターの構成ファイル (machine.config) とアプリケーション構成ファイルで使用できます。  
  
## <a name="example"></a>例  
 次の例では、要素を`<remove>`使用し`<add>`て、リスナー `console`をトレースソース`TraceSourceApp`の`Listeners`コレクションに追加する前に、要素を使用する方法を示します。  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="TraceSourceApp" switchName="sourceSwitch"   
         switchType="System.Diagnostics.SourceSwitch" >  
         <listeners>  
           <remove name="Default"/>  
           <add name="console"   
             type="System.Diagnostics.ConsoleTraceListener" />  
         </listeners>  
      </source>  
    </sources>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Diagnostics.TraceSource.Listeners%2A>
- <xref:System.Diagnostics.TraceSource>
- [トレースおよびデバッグ設定のスキーマ](index.md)
- [\<clear>](clear-element-for-listeners-for-source.md)
- [トレース リスナー](../../../debug-trace-profile/trace-listeners.md)
